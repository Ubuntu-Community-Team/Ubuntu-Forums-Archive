---
title: "Help with Windows 7 install please."
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by johntland on 2011-12-10
I am at a loss. I have tried to manually download the ISO (several flavors actually) and sticking them in the same folder as the wubi.exe, unplug my network. So, here is what my log file says. Maybe someone with more experience can help me. FWI: I did make a bootable USB ISO last night, but wasn't happy with the speed of it. I have a 120 GB SSD I want Ubuntu installed it. Here are the specs of my machine:
CPU Information: Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz ¦¦ Cores: 4 ¦¦ Threads: 8 ¦¦ Clock Speed: 2195 MHz 
 
Physical Memory Used: 1879 MB / 8169 MB (23%) [Samsung, 2 sticks] Page File Memory Used: 1977 MB / 16337 MB 
 
Display Device: NVIDIA GeForce GTX 560M ¦¦ Detected monitors: 1 ¦¦ Y!Epic is on monitor: 0 ¦¦ Primary: 1600x900 (Num: 0) [60 Hz] ¦¦ 
 
Two hard drives. Windows installed on an Intel 120GB SSD/Storage 500GB Sata
 
Here is the log file:
```

12-09 20:33 INFO   root: === wubi 11.10 rev245 ===
12-09 20:33 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 20:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-09 20:33 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\data
12-09 20:33 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\bin\7z.exe
12-09 20:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 20:33 DEBUG  CommonBackend: Fetching basic info...
12-09 20:33 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-09 20:33 DEBUG  CommonBackend: platform=win32
12-09 20:33 DEBUG  CommonBackend: osname=nt
12-09 20:33 DEBUG  CommonBackend: language=en_US
12-09 20:33 DEBUG  CommonBackend: encoding=cp1252
12-09 20:33 DEBUG  WindowsBackend: arch=amd64
12-09 20:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\data\isolist.ini
12-09 20:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 20:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 20:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 20:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 20:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 20:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 20:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 20:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 20:33 DEBUG  WindowsBackend: Fetching host info...
12-09 20:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 20:33 DEBUG  WindowsBackend: windows version=vista
12-09 20:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 20:33 DEBUG  WindowsBackend: windows_sp=None
12-09 20:33 DEBUG  WindowsBackend: windows_build=7601
12-09 20:33 DEBUG  WindowsBackend: gmt=-6
12-09 20:33 DEBUG  WindowsBackend: country=US
12-09 20:33 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 20:33 DEBUG  WindowsBackend: windows_username=John
12-09 20:33 DEBUG  WindowsBackend: user_full_name=John
12-09 20:33 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 20:33 DEBUG  WindowsBackend: windows_language_code=1033
12-09 20:33 DEBUG  WindowsBackend: windows_language=English
12-09 20:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 20:33 DEBUG  WindowsBackend: bootloader=vista
12-09 20:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 70863.671875 mb free ntfs)
12-09 20:33 DEBUG  WindowsBackend: drive=Drive(C: hd 70863.671875 mb free ntfs)
12-09 20:33 DEBUG  WindowsBackend: drive=Drive(D: hd 197402.253906 mb free ntfs)
12-09 20:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-09 20:33 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 20:33 DEBUG  WindowsBackend: uninstaller_path=None
12-09 20:33 DEBUG  WindowsBackend: previous_target_dir=None
12-09 20:33 DEBUG  WindowsBackend: previous_distro_name=None
12-09 20:33 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 20:33 DEBUG  WindowsBackend: keyboard_layout=us
12-09 20:33 DEBUG  WindowsBackend: keyboard_variant=
12-09 20:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 20:33 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 20:33 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 20:33 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 20:33 DEBUG  CommonBackend: Searching for local CDs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 INFO   root: Running the installer...
12-09 20:33 DEBUG  WindowsFrontend: __init__...
12-09 20:33 DEBUG  WindowsFrontend: on_init...
12-09 20:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\translations, languages=['en_US', 'en']
12-09 20:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\translations, languages=['en_US', 'en']
12-09 20:33 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 20:33 INFO   root: Received settings
12-09 20:33 DEBUG  CommonBackend: Searching for local CD
12-09 20:33 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7485.tmp is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7485.tmp\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:33 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:33 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:33 DEBUG  CommonBackend: Searching for local ISO
12-09 20:33 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-09 20:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-09 20:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7485.tmp\translations, languages=['en_US', 'en']
12-09 20:33 DEBUG  TaskList: # Running tasklist...
12-09 20:33 DEBUG  TaskList: ## Running select_target_dir...
12-09 20:33 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 20:33 DEBUG  TaskList: ## Finished select_target_dir
12-09 20:33 DEBUG  TaskList: ## Running create_dir_structure...
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 20:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 20:33 DEBUG  TaskList: ## Finished create_dir_structure
12-09 20:33 DEBUG  TaskList: ## Running create_uninstaller...
12-09 20:33 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 20:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 20:33 DEBUG  TaskList: ## Finished create_uninstaller
12-09 20:33 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 20:33 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 20:33 DEBUG  TaskList: ## Running get_diskimage...
12-09 20:33 DEBUG  TaskList: New task download
12-09 20:33 DEBUG  TaskList: ### Running download...
12-09 20:33 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 20:33 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 20:42 DEBUG  TaskList: ### Finished download
12-09 20:42 DEBUG  downloader: download finished (read 507143012 bytes)
12-09 20:42 DEBUG  TaskList: ## Finished get_diskimage
12-09 20:42 DEBUG  TaskList: ## Running extract_diskimage...
12-09 20:42 DEBUG  TaskList: ## Finished extract_diskimage
12-09 20:42 DEBUG  TaskList: ## Running choose_disk_sizes...
12-09 20:42 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-09 20:42 DEBUG  TaskList: ## Finished choose_disk_sizes
12-09 20:42 DEBUG  TaskList: ## Running expand_diskimage...
12-09 20:45 DEBUG  TaskList: ## Finished expand_diskimage
12-09 20:45 DEBUG  TaskList: ## Running create_swap_diskimage...
12-09 20:45 DEBUG  TaskList: ## Finished create_swap_diskimage
12-09 20:45 DEBUG  TaskList: ## Running modify_bootloader...
12-09 20:45 DEBUG  TaskList: New task modify_bcd
12-09 20:45 DEBUG  TaskList: ### Running modify_bcd...
12-09 20:45 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 70863.671875 mb free ntfs)
12-09 20:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8cb2d9b6-7c05-11de-842e-b4611d44fefa}
12-09 20:45 DEBUG  TaskList: ### Finished modify_bcd
12-09 20:45 DEBUG  TaskList: New task modify_bcd
12-09 20:45 DEBUG  TaskList: ### Running modify_bcd...
12-09 20:45 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 197402.253906 mb free ntfs)
12-09 20:45 DEBUG  WindowsBackend: BCD has already been modified
12-09 20:45 DEBUG  TaskList: ### Finished modify_bcd
12-09 20:45 DEBUG  TaskList: New task modify_bcd
12-09 20:45 DEBUG  TaskList: ### Running modify_bcd...
12-09 20:45 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
12-09 20:45 DEBUG  WindowsBackend: BCD has already been modified
12-09 20:45 DEBUG  TaskList: ### Finished modify_bcd
12-09 20:45 DEBUG  TaskList: ## Finished modify_bootloader
12-09 20:45 DEBUG  TaskList: ## Running diskimage_bootloader...
12-09 20:45 DEBUG  WindowsBackend: Copying C:\Users\John\AppData\Local\Temp\pyl7485.tmp\winboot -> C:\ubuntu\winboot
12-09 20:45 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 20:45 DEBUG  TaskList: # Cancelling tasklist
12-09 20:45 DEBUG  TaskList: # Finished tasklist
12-09 20:45 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 20:52 INFO   root: === wubi 11.10 rev245 ===
12-09 20:52 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 20:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-09 20:52 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\data
12-09 20:52 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\bin\7z.exe
12-09 20:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 20:52 DEBUG  CommonBackend: Fetching basic info...
12-09 20:52 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-09 20:52 DEBUG  CommonBackend: platform=win32
12-09 20:52 DEBUG  CommonBackend: osname=nt
12-09 20:52 DEBUG  CommonBackend: language=en_US
12-09 20:52 DEBUG  CommonBackend: encoding=cp1252
12-09 20:52 DEBUG  WindowsBackend: arch=amd64
12-09 20:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\data\isolist.ini
12-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 20:52 DEBUG  WindowsBackend: Fetching host info...
12-09 20:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 20:52 DEBUG  WindowsBackend: windows version=vista
12-09 20:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 20:52 DEBUG  WindowsBackend: windows_sp=None
12-09 20:52 DEBUG  WindowsBackend: windows_build=7601
12-09 20:52 DEBUG  WindowsBackend: gmt=-6
12-09 20:52 DEBUG  WindowsBackend: country=US
12-09 20:52 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 20:52 DEBUG  WindowsBackend: windows_username=John
12-09 20:52 DEBUG  WindowsBackend: user_full_name=John
12-09 20:52 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 20:52 DEBUG  WindowsBackend: windows_language_code=1033
12-09 20:52 DEBUG  WindowsBackend: windows_language=English
12-09 20:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 20:52 DEBUG  WindowsBackend: bootloader=vista
12-09 20:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 67290.6679688 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(C: hd 67290.6679688 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(D: hd 197395.871094 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 20:52 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 20:52 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 20:52 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 20:52 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 20:52 DEBUG  WindowsBackend: keyboard_layout=us
12-09 20:52 DEBUG  WindowsBackend: keyboard_variant=
12-09 20:52 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 20:52 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 20:52 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 20:52 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 20:52 DEBUG  CommonBackend: Searching for local CDs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 INFO   root: Already installed, running the uninstaller...
12-09 20:52 INFO   root: Running the uninstaller...
12-09 20:52 INFO   CommonBackend: This is the uninstaller running
12-09 20:52 DEBUG  WindowsFrontend: __init__...
12-09 20:52 DEBUG  WindowsFrontend: on_init...
12-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\translations, languages=['en_US', 'en']
12-09 20:52 INFO   root: Received settings
12-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\translations, languages=['en_US', 'en']
12-09 20:52 DEBUG  TaskList: # Running tasklist...
12-09 20:52 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 20:52 DEBUG  WindowsBackend: Removing bcd entry {8cb2d9b6-7c05-11de-842e-b4611d44fefa}
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-09 20:52 DEBUG  WindowsBackend: undo_bootini C:
12-09 20:52 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 67290.6679688 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: undo_bootini D:
12-09 20:52 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 197395.871094 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: undo_bootini Q:
12-09 20:52 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 20:52 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 20:52 DEBUG  TaskList: ## Running Remove target dir...
12-09 20:52 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 20:52 DEBUG  TaskList: ## Finished Remove target dir
12-09 20:52 DEBUG  TaskList: ## Running Remove registry key...
12-09 20:52 DEBUG  TaskList: ## Finished Remove registry key
12-09 20:52 DEBUG  TaskList: # Finished tasklist
12-09 20:52 INFO   root: Almost finished uninstalling
12-09 20:52 INFO   root: Finished uninstallation
12-09 20:52 DEBUG  CommonBackend: Fetching basic info...
12-09 20:52 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-09 20:52 DEBUG  CommonBackend: platform=win32
12-09 20:52 DEBUG  CommonBackend: osname=nt
12-09 20:52 DEBUG  WindowsBackend: arch=amd64
12-09 20:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\data\isolist.ini
12-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 20:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 20:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 20:52 DEBUG  WindowsBackend: Fetching host info...
12-09 20:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 20:52 DEBUG  WindowsBackend: windows version=vista
12-09 20:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 20:52 DEBUG  WindowsBackend: windows_sp=None
12-09 20:52 DEBUG  WindowsBackend: windows_build=7601
12-09 20:52 DEBUG  WindowsBackend: gmt=-6
12-09 20:52 DEBUG  WindowsBackend: country=US
12-09 20:52 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 20:52 DEBUG  WindowsBackend: windows_username=John
12-09 20:52 DEBUG  WindowsBackend: user_full_name=John
12-09 20:52 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 20:52 DEBUG  WindowsBackend: windows_language_code=1033
12-09 20:52 DEBUG  WindowsBackend: windows_language=English
12-09 20:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 20:52 DEBUG  WindowsBackend: bootloader=vista
12-09 20:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 70496.0507813 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(C: hd 70496.0507813 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(D: hd 197396.0 mb free ntfs)
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-09 20:52 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 20:52 DEBUG  WindowsBackend: uninstaller_path=None
12-09 20:52 DEBUG  WindowsBackend: previous_target_dir=None
12-09 20:52 DEBUG  WindowsBackend: previous_distro_name=None
12-09 20:52 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 20:52 DEBUG  WindowsBackend: keyboard_layout=us
12-09 20:52 DEBUG  WindowsBackend: keyboard_variant=
12-09 20:52 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 20:52 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 20:52 DEBUG  CommonBackend: Searching for local CDs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 INFO   root: Running the installer...
12-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\translations, languages=['en_US', 'en']
12-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\translations, languages=['en_US', 'en']
12-09 20:52 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 20:52 INFO   root: Received settings
12-09 20:52 DEBUG  CommonBackend: Searching for local CD
12-09 20:52 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE6E7.tmp is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 20:52 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 20:52 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 20:52 DEBUG  CommonBackend: Searching for local ISO
12-09 20:52 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-09 20:52 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-09 20:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\translations, languages=['en_US', 'en']
12-09 20:52 DEBUG  TaskList: # Running tasklist...
12-09 20:52 DEBUG  TaskList: ## Running select_target_dir...
12-09 20:52 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 20:52 DEBUG  TaskList: ## Finished select_target_dir
12-09 20:52 DEBUG  TaskList: ## Running create_dir_structure...
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 20:52 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 20:52 DEBUG  TaskList: ## Finished create_dir_structure
12-09 20:52 DEBUG  TaskList: ## Running create_uninstaller...
12-09 20:52 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 20:52 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 20:52 DEBUG  TaskList: ## Finished create_uninstaller
12-09 20:52 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 20:52 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 20:52 DEBUG  TaskList: ## Running get_diskimage...
12-09 20:52 DEBUG  TaskList: New task download
12-09 20:52 DEBUG  TaskList: ### Running download...
12-09 20:52 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 20:52 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 21:05 DEBUG  TaskList: ### Finished download
12-09 21:05 DEBUG  downloader: download finished (read 507143012 bytes)
12-09 21:05 DEBUG  TaskList: ## Finished get_diskimage
12-09 21:05 DEBUG  TaskList: ## Running extract_diskimage...
12-09 21:06 DEBUG  TaskList: ## Finished extract_diskimage
12-09 21:06 DEBUG  TaskList: ## Running choose_disk_sizes...
12-09 21:06 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-09 21:06 DEBUG  TaskList: ## Finished choose_disk_sizes
12-09 21:06 DEBUG  TaskList: ## Running expand_diskimage...
12-09 21:08 DEBUG  TaskList: ## Finished expand_diskimage
12-09 21:08 DEBUG  TaskList: ## Running create_swap_diskimage...
12-09 21:08 DEBUG  TaskList: ## Finished create_swap_diskimage
12-09 21:08 DEBUG  TaskList: ## Running modify_bootloader...
12-09 21:08 DEBUG  TaskList: New task modify_bcd
12-09 21:08 DEBUG  TaskList: ### Running modify_bcd...
12-09 21:08 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 70496.0507813 mb free ntfs)
12-09 21:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8cb2d9b7-7c05-11de-842e-b4611d44fefa}
12-09 21:08 DEBUG  TaskList: ### Finished modify_bcd
12-09 21:08 DEBUG  TaskList: New task modify_bcd
12-09 21:08 DEBUG  TaskList: ### Running modify_bcd...
12-09 21:08 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 197396.0 mb free ntfs)
12-09 21:08 DEBUG  WindowsBackend: BCD has already been modified
12-09 21:08 DEBUG  TaskList: ### Finished modify_bcd
12-09 21:08 DEBUG  TaskList: New task modify_bcd
12-09 21:08 DEBUG  TaskList: ### Running modify_bcd...
12-09 21:08 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
12-09 21:08 DEBUG  WindowsBackend: BCD has already been modified
12-09 21:08 DEBUG  TaskList: ### Finished modify_bcd
12-09 21:08 DEBUG  TaskList: ## Finished modify_bootloader
12-09 21:08 DEBUG  TaskList: ## Running diskimage_bootloader...
12-09 21:08 DEBUG  WindowsBackend: Copying C:\Users\John\AppData\Local\Temp\pylE6E7.tmp\winboot -> C:\ubuntu\winboot
12-09 21:08 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 21:08 DEBUG  TaskList: # Cancelling tasklist
12-09 21:08 DEBUG  TaskList: # Finished tasklist
12-09 21:08 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 22:32 INFO   root: === wubi 11.10 rev245 ===
12-09 22:32 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 22:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-09 22:32 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\data
12-09 22:32 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\bin\7z.exe
12-09 22:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 22:32 DEBUG  CommonBackend: Fetching basic info...
12-09 22:32 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-09 22:32 DEBUG  CommonBackend: platform=win32
12-09 22:32 DEBUG  CommonBackend: osname=nt
12-09 22:32 DEBUG  CommonBackend: language=en_US
12-09 22:32 DEBUG  CommonBackend: encoding=cp1252
12-09 22:32 DEBUG  WindowsBackend: arch=amd64
12-09 22:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\data\isolist.ini
12-09 22:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 22:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 22:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 22:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 22:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 22:32 DEBUG  WindowsBackend: Fetching host info...
12-09 22:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 22:32 DEBUG  WindowsBackend: windows version=vista
12-09 22:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 22:32 DEBUG  WindowsBackend: windows_sp=None
12-09 22:32 DEBUG  WindowsBackend: windows_build=7601
12-09 22:32 DEBUG  WindowsBackend: gmt=-6
12-09 22:32 DEBUG  WindowsBackend: country=US
12-09 22:32 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 22:32 DEBUG  WindowsBackend: windows_username=John
12-09 22:32 DEBUG  WindowsBackend: user_full_name=John
12-09 22:32 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 22:32 DEBUG  WindowsBackend: windows_language_code=1033
12-09 22:32 DEBUG  WindowsBackend: windows_language=English
12-09 22:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 22:32 DEBUG  WindowsBackend: bootloader=vista
12-09 22:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 67349.3476563 mb free ntfs)
12-09 22:32 DEBUG  WindowsBackend: drive=Drive(C: hd 67349.3476563 mb free ntfs)
12-09 22:32 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.015625 mb free ntfs)
12-09 22:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 22:32 DEBUG  WindowsBackend: drive=Drive(G: removable 2840.79101563 mb free fat32)
12-09 22:32 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 22:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 22:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 22:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 22:32 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 22:32 DEBUG  WindowsBackend: keyboard_layout=us
12-09 22:32 DEBUG  WindowsBackend: keyboard_variant=
12-09 22:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 22:32 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 22:32 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 22:32 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 22:32 DEBUG  CommonBackend: Searching for local CDs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4D35.tmp is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 22:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 22:32 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:32 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-09 22:32 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
12-09 22:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
12-09 22:32 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-09 22:32 INFO   root: Running the uninstaller...
12-09 22:32 INFO   CommonBackend: This is the uninstaller running
12-09 22:32 DEBUG  WindowsFrontend: __init__...
12-09 22:32 DEBUG  WindowsFrontend: on_init...
12-09 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\translations, languages=['en_US', 'en']
12-09 22:32 INFO   root: Received settings
12-09 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\translations, languages=['en_US', 'en']
12-09 22:32 DEBUG  TaskList: # Running tasklist...
12-09 22:32 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 22:32 DEBUG  WindowsBackend: Removing bcd entry {8cb2d9b7-7c05-11de-842e-b4611d44fefa}
12-09 22:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-09 22:32 DEBUG  WindowsBackend: undo_bootini C:
12-09 22:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 67349.3476563 mb free ntfs)
12-09 22:32 DEBUG  WindowsBackend: undo_bootini D:
12-09 22:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.015625 mb free ntfs)
12-09 22:32 DEBUG  WindowsBackend: undo_bootini G:
12-09 22:32 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 2840.79101563 mb free fat32)
12-09 22:32 DEBUG  WindowsBackend: undo_bootini Q:
12-09 22:32 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 22:32 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 22:32 DEBUG  TaskList: ## Running Remove target dir...
12-09 22:32 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 22:32 DEBUG  TaskList: ## Finished Remove target dir
12-09 22:32 DEBUG  TaskList: ## Running Remove registry key...
12-09 22:32 DEBUG  TaskList: ## Finished Remove registry key
12-09 22:32 DEBUG  TaskList: # Finished tasklist
12-09 22:32 INFO   root: Almost finished uninstalling
12-09 22:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4D35.tmp\translations, languages=['en_US', 'en']
12-09 22:32 INFO   root: Finished uninstallation
12-09 22:32 DEBUG  root: application.quit
12-09 22:32 DEBUG  WindowsFrontend: frontend.quit
12-09 22:32 DEBUG  WindowsFrontend: frontend.on_quit
12-09 22:32 DEBUG  root: application.on_quit
12-09 22:32 INFO   root: sys.exit
12-09 22:37 INFO   root: === wubi 11.10 rev245 ===
12-09 22:37 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 22:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\NQZN73SB\\wubi.exe"']
12-09 22:37 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\data
12-09 22:37 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\bin\7z.exe
12-09 22:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 22:37 DEBUG  CommonBackend: Fetching basic info...
12-09 22:37 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\NQZN73SB\wubi.exe
12-09 22:37 DEBUG  CommonBackend: platform=win32
12-09 22:37 DEBUG  CommonBackend: osname=nt
12-09 22:37 DEBUG  CommonBackend: language=en_US
12-09 22:37 DEBUG  CommonBackend: encoding=cp1252
12-09 22:37 DEBUG  WindowsBackend: arch=amd64
12-09 22:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\data\isolist.ini
12-09 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 22:37 DEBUG  WindowsBackend: Fetching host info...
12-09 22:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 22:37 DEBUG  WindowsBackend: windows version=vista
12-09 22:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 22:37 DEBUG  WindowsBackend: windows_sp=None
12-09 22:37 DEBUG  WindowsBackend: windows_build=7601
12-09 22:37 DEBUG  WindowsBackend: gmt=-6
12-09 22:37 DEBUG  WindowsBackend: country=US
12-09 22:37 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 22:37 DEBUG  WindowsBackend: windows_username=John
12-09 22:37 DEBUG  WindowsBackend: user_full_name=John
12-09 22:37 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 22:37 DEBUG  WindowsBackend: windows_language_code=1033
12-09 22:37 DEBUG  WindowsBackend: windows_language=English
12-09 22:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 22:37 DEBUG  WindowsBackend: bootloader=vista
12-09 22:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69765.2109375 mb free ntfs)
12-09 22:37 DEBUG  WindowsBackend: drive=Drive(C: hd 69765.2109375 mb free ntfs)
12-09 22:37 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 22:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-09 22:37 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 22:37 DEBUG  WindowsBackend: uninstaller_path=None
12-09 22:37 DEBUG  WindowsBackend: previous_target_dir=None
12-09 22:37 DEBUG  WindowsBackend: previous_distro_name=None
12-09 22:37 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 22:37 DEBUG  WindowsBackend: keyboard_layout=us
12-09 22:37 DEBUG  WindowsBackend: keyboard_variant=
12-09 22:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 22:37 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 22:37 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 22:37 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 22:37 DEBUG  CommonBackend: Searching for local CDs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Xubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Xubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Mythbuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylAD6D.tmp is a valid Mythbuntu CD
12-09 22:37 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 22:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 INFO   root: Running the installer...
12-09 22:38 DEBUG  WindowsFrontend: __init__...
12-09 22:38 DEBUG  WindowsFrontend: on_init...
12-09 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\translations, languages=['en_US', 'en']
12-09 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylAD6D.tmp\translations, languages=['en_US', 'en']
12-09 22:38 INFO   root: === wubi 11.10 rev245 ===
12-09 22:38 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 22:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\X3T4BAUW\\wubi.exe"']
12-09 22:38 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\data
12-09 22:38 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\bin\7z.exe
12-09 22:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 22:38 DEBUG  CommonBackend: Fetching basic info...
12-09 22:38 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\X3T4BAUW\wubi.exe
12-09 22:38 DEBUG  CommonBackend: platform=win32
12-09 22:38 DEBUG  CommonBackend: osname=nt
12-09 22:38 DEBUG  CommonBackend: language=en_US
12-09 22:38 DEBUG  CommonBackend: encoding=cp1252
12-09 22:38 DEBUG  WindowsBackend: arch=amd64
12-09 22:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\data\isolist.ini
12-09 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 22:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 22:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 22:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 22:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 22:38 DEBUG  WindowsBackend: Fetching host info...
12-09 22:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 22:38 DEBUG  WindowsBackend: windows version=vista
12-09 22:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 22:38 DEBUG  WindowsBackend: windows_sp=None
12-09 22:38 DEBUG  WindowsBackend: windows_build=7601
12-09 22:38 DEBUG  WindowsBackend: gmt=-6
12-09 22:38 DEBUG  WindowsBackend: country=US
12-09 22:38 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 22:38 DEBUG  WindowsBackend: windows_username=John
12-09 22:38 DEBUG  WindowsBackend: user_full_name=John
12-09 22:38 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 22:38 DEBUG  WindowsBackend: windows_language_code=1033
12-09 22:38 DEBUG  WindowsBackend: windows_language=English
12-09 22:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 22:38 DEBUG  WindowsBackend: bootloader=vista
12-09 22:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 70441.9804688 mb free ntfs)
12-09 22:38 DEBUG  WindowsBackend: drive=Drive(C: hd 70441.9804688 mb free ntfs)
12-09 22:38 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 22:38 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 22:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 22:38 DEBUG  WindowsBackend: uninstaller_path=None
12-09 22:38 DEBUG  WindowsBackend: previous_target_dir=None
12-09 22:38 DEBUG  WindowsBackend: previous_distro_name=None
12-09 22:38 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 22:38 DEBUG  WindowsBackend: keyboard_layout=us
12-09 22:38 DEBUG  WindowsBackend: keyboard_variant=
12-09 22:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 22:38 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 22:38 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 22:38 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 22:38 DEBUG  CommonBackend: Searching for local CDs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 22:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 22:38 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:38 INFO   root: Running the installer...
12-09 22:38 DEBUG  WindowsFrontend: __init__...
12-09 22:38 DEBUG  WindowsFrontend: on_init...
12-09 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\translations, languages=['en_US', 'en']
12-09 22:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\translations, languages=['en_US', 'en']
12-09 22:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 22:39 INFO   root: Received settings
12-09 22:39 DEBUG  CommonBackend: Searching for local CD
12-09 22:39 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl93E5.tmp is a valid Ubuntu CD
12-09 22:39 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\casper\filesystem.squashfs
12-09 22:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:39 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:39 DEBUG  CommonBackend: Searching for local ISO
12-09 22:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\translations, languages=['en_US', 'en']
12-09 22:39 DEBUG  TaskList: # Running tasklist...
12-09 22:39 DEBUG  TaskList: ## Running select_target_dir...
12-09 22:39 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 22:39 DEBUG  TaskList: ## Finished select_target_dir
12-09 22:39 DEBUG  TaskList: ## Running create_dir_structure...
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 22:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 22:39 DEBUG  TaskList: ## Finished create_dir_structure
12-09 22:39 DEBUG  TaskList: ## Running create_uninstaller...
12-09 22:39 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\X3T4BAUW\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 22:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 22:39 DEBUG  TaskList: ## Finished create_uninstaller
12-09 22:39 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 22:39 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 22:39 DEBUG  TaskList: ## Running get_diskimage...
12-09 22:39 DEBUG  TaskList: New task download
12-09 22:39 DEBUG  TaskList: ### Running download...
12-09 22:39 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 22:39 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 22:52 DEBUG  TaskList: ### Finished download
12-09 22:52 DEBUG  downloader: download finished (read 507143012 bytes)
12-09 22:52 DEBUG  TaskList: ## Finished get_diskimage
12-09 22:52 DEBUG  TaskList: ## Running extract_diskimage...
12-09 22:53 DEBUG  TaskList: ## Finished extract_diskimage
12-09 22:53 DEBUG  TaskList: ## Running choose_disk_sizes...
12-09 22:53 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-09 22:53 DEBUG  TaskList: ## Finished choose_disk_sizes
12-09 22:53 DEBUG  TaskList: ## Running expand_diskimage...
12-09 22:55 DEBUG  TaskList: ## Finished expand_diskimage
12-09 22:55 DEBUG  TaskList: ## Running create_swap_diskimage...
12-09 22:55 DEBUG  TaskList: ## Finished create_swap_diskimage
12-09 22:55 DEBUG  TaskList: ## Running modify_bootloader...
12-09 22:55 DEBUG  TaskList: New task modify_bcd
12-09 22:55 DEBUG  TaskList: ### Running modify_bcd...
12-09 22:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 70441.9804688 mb free ntfs)
12-09 22:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8cb2d9b8-7c05-11de-842e-b4611d44fefa}
12-09 22:55 DEBUG  TaskList: ### Finished modify_bcd
12-09 22:55 DEBUG  TaskList: New task modify_bcd
12-09 22:55 DEBUG  TaskList: ### Running modify_bcd...
12-09 22:55 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 196707.144531 mb free ntfs)
12-09 22:55 DEBUG  WindowsBackend: BCD has already been modified
12-09 22:55 DEBUG  TaskList: ### Finished modify_bcd
12-09 22:55 DEBUG  TaskList: New task modify_bcd
12-09 22:55 DEBUG  TaskList: ### Running modify_bcd...
12-09 22:55 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
12-09 22:55 DEBUG  WindowsBackend: BCD has already been modified
12-09 22:55 DEBUG  TaskList: ### Finished modify_bcd
12-09 22:55 DEBUG  TaskList: ## Finished modify_bootloader
12-09 22:55 DEBUG  TaskList: ## Running diskimage_bootloader...
12-09 22:55 DEBUG  WindowsBackend: Copying C:\Users\John\AppData\Local\Temp\pyl93E5.tmp\winboot -> C:\ubuntu\winboot
12-09 22:55 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 22:55 DEBUG  TaskList: # Cancelling tasklist
12-09 22:55 DEBUG  TaskList: # Finished tasklist
12-09 22:55 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-09 22:56 INFO   WindowsFrontend: Operation cancelled
12-09 22:56 DEBUG  WindowsFrontend: frontend.quit
12-09 22:56 DEBUG  WindowsFrontend: frontend.on_quit
12-09 22:56 DEBUG  root: application.on_quit
12-09 22:56 INFO   root: sys.exit
12-09 22:59 INFO   root: === wubi 11.10 rev245 ===
12-09 22:59 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 22:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 22:59 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\data
12-09 22:59 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\bin\7z.exe
12-09 22:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 22:59 DEBUG  CommonBackend: Fetching basic info...
12-09 22:59 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 22:59 DEBUG  CommonBackend: platform=win32
12-09 22:59 DEBUG  CommonBackend: osname=nt
12-09 22:59 DEBUG  CommonBackend: language=en_US
12-09 22:59 DEBUG  CommonBackend: encoding=cp1252
12-09 22:59 DEBUG  WindowsBackend: arch=amd64
12-09 22:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\data\isolist.ini
12-09 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 22:59 DEBUG  WindowsBackend: Fetching host info...
12-09 22:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 22:59 DEBUG  WindowsBackend: windows version=vista
12-09 22:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 22:59 DEBUG  WindowsBackend: windows_sp=None
12-09 22:59 DEBUG  WindowsBackend: windows_build=7601
12-09 22:59 DEBUG  WindowsBackend: gmt=-6
12-09 22:59 DEBUG  WindowsBackend: country=US
12-09 22:59 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 22:59 DEBUG  WindowsBackend: windows_username=John
12-09 22:59 DEBUG  WindowsBackend: user_full_name=John
12-09 22:59 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 22:59 DEBUG  WindowsBackend: windows_language_code=1033
12-09 22:59 DEBUG  WindowsBackend: windows_language=English
12-09 22:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 22:59 DEBUG  WindowsBackend: bootloader=vista
12-09 22:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 66626.3632813 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(C: hd 66626.3632813 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.015625 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 22:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 22:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 22:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 22:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 22:59 DEBUG  WindowsBackend: keyboard_layout=us
12-09 22:59 DEBUG  WindowsBackend: keyboard_variant=
12-09 22:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 22:59 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 22:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 22:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 22:59 DEBUG  CommonBackend: Searching for local CDs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 22:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 INFO   root: Already installed, running the uninstaller...
12-09 22:59 INFO   root: Running the uninstaller...
12-09 22:59 INFO   CommonBackend: This is the uninstaller running
12-09 22:59 DEBUG  WindowsFrontend: __init__...
12-09 22:59 DEBUG  WindowsFrontend: on_init...
12-09 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\translations, languages=['en_US', 'en']
12-09 22:59 INFO   root: Received settings
12-09 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\translations, languages=['en_US', 'en']
12-09 22:59 DEBUG  TaskList: # Running tasklist...
12-09 22:59 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 22:59 DEBUG  WindowsBackend: Removing bcd entry {8cb2d9b8-7c05-11de-842e-b4611d44fefa}
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
12-09 22:59 DEBUG  WindowsBackend: undo_bootini C:
12-09 22:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 66626.3632813 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: undo_bootini D:
12-09 22:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.015625 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: undo_bootini Q:
12-09 22:59 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 22:59 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 22:59 DEBUG  TaskList: ## Running Remove target dir...
12-09 22:59 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 22:59 DEBUG  TaskList: ## Finished Remove target dir
12-09 22:59 DEBUG  TaskList: ## Running Remove registry key...
12-09 22:59 DEBUG  TaskList: ## Finished Remove registry key
12-09 22:59 DEBUG  TaskList: # Finished tasklist
12-09 22:59 INFO   root: Almost finished uninstalling
12-09 22:59 INFO   root: Finished uninstallation
12-09 22:59 DEBUG  CommonBackend: Fetching basic info...
12-09 22:59 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 22:59 DEBUG  CommonBackend: platform=win32
12-09 22:59 DEBUG  CommonBackend: osname=nt
12-09 22:59 DEBUG  WindowsBackend: arch=amd64
12-09 22:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\data\isolist.ini
12-09 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 22:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 22:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 22:59 DEBUG  WindowsBackend: Fetching host info...
12-09 22:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 22:59 DEBUG  WindowsBackend: windows version=vista
12-09 22:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 22:59 DEBUG  WindowsBackend: windows_sp=None
12-09 22:59 DEBUG  WindowsBackend: windows_build=7601
12-09 22:59 DEBUG  WindowsBackend: gmt=-6
12-09 22:59 DEBUG  WindowsBackend: country=US
12-09 22:59 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 22:59 DEBUG  WindowsBackend: windows_username=John
12-09 22:59 DEBUG  WindowsBackend: user_full_name=John
12-09 22:59 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 22:59 DEBUG  WindowsBackend: windows_language_code=1033
12-09 22:59 DEBUG  WindowsBackend: windows_language=English
12-09 22:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 22:59 DEBUG  WindowsBackend: bootloader=vista
12-09 22:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69833.3398438 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(C: hd 69833.3398438 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 22:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 22:59 DEBUG  WindowsBackend: uninstaller_path=None
12-09 22:59 DEBUG  WindowsBackend: previous_target_dir=None
12-09 22:59 DEBUG  WindowsBackend: previous_distro_name=None
12-09 22:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 22:59 DEBUG  WindowsBackend: keyboard_layout=us
12-09 22:59 DEBUG  WindowsBackend: keyboard_variant=
12-09 22:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 22:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 22:59 DEBUG  CommonBackend: Searching for local CDs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 INFO   root: Running the installer...
12-09 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\translations, languages=['en_US', 'en']
12-09 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\translations, languages=['en_US', 'en']
12-09 22:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 22:59 INFO   root: Received settings
12-09 22:59 DEBUG  CommonBackend: Searching for local CD
12-09 22:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 22:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 22:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 22:59 DEBUG  CommonBackend: Searching for local ISO
12-09 22:59 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 22:59 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 22:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 22:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 22:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 22:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl4C7A.tmp\translations, languages=['en_US', 'en']
12-09 22:59 DEBUG  TaskList: # Running tasklist...
12-09 22:59 DEBUG  TaskList: ## Running select_target_dir...
12-09 22:59 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 22:59 DEBUG  TaskList: ## Finished select_target_dir
12-09 22:59 DEBUG  TaskList: ## Running create_dir_structure...
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 22:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 22:59 DEBUG  TaskList: ## Finished create_dir_structure
12-09 22:59 DEBUG  TaskList: ## Running create_uninstaller...
12-09 22:59 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 22:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 22:59 DEBUG  TaskList: ## Finished create_uninstaller
12-09 22:59 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 22:59 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 22:59 DEBUG  TaskList: ## Running get_diskimage...
12-09 22:59 DEBUG  TaskList: New task download
12-09 22:59 DEBUG  TaskList: ### Running download...
12-09 22:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 22:59 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 23:02 INFO   WindowsFrontend: Operation cancelled
12-09 23:02 DEBUG  WindowsFrontend: frontend.quit
12-09 23:02 DEBUG  WindowsFrontend: frontend.on_quit
12-09 23:02 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-09 23:02 DEBUG  TaskList: # Cancelling tasklist
12-09 23:02 DEBUG  downloader: download finished (read 185237504 bytes)
12-09 23:02 DEBUG  TaskList: ### Finished download
12-09 23:02 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-09 23:02 DEBUG  root: application.on_quit
12-09 23:02 DEBUG  root: Forceful exit
12-09 23:02 INFO   root: sys.exit
12-09 23:02 INFO   root: === wubi 11.10 rev245 ===
12-09 23:02 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 23:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 23:02 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\data
12-09 23:02 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\bin\7z.exe
12-09 23:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 23:02 DEBUG  CommonBackend: Fetching basic info...
12-09 23:02 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:02 DEBUG  CommonBackend: platform=win32
12-09 23:02 DEBUG  CommonBackend: osname=nt
12-09 23:02 DEBUG  CommonBackend: language=en_US
12-09 23:02 DEBUG  CommonBackend: encoding=cp1252
12-09 23:02 DEBUG  WindowsBackend: arch=amd64
12-09 23:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\data\isolist.ini
12-09 23:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:02 DEBUG  WindowsBackend: Fetching host info...
12-09 23:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:02 DEBUG  WindowsBackend: windows version=vista
12-09 23:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:02 DEBUG  WindowsBackend: windows_sp=None
12-09 23:02 DEBUG  WindowsBackend: windows_build=7601
12-09 23:02 DEBUG  WindowsBackend: gmt=-6
12-09 23:02 DEBUG  WindowsBackend: country=US
12-09 23:02 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:02 DEBUG  WindowsBackend: windows_username=John
12-09 23:02 DEBUG  WindowsBackend: user_full_name=John
12-09 23:02 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:02 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:02 DEBUG  WindowsBackend: windows_language=English
12-09 23:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:02 DEBUG  WindowsBackend: bootloader=vista
12-09 23:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69654.1484375 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(C: hd 69654.1484375 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:02 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 23:02 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 23:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 23:02 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:02 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:02 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 23:02 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 23:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:02 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:02 DEBUG  CommonBackend: Searching for local CDs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:02 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 INFO   root: Already installed, running the uninstaller...
12-09 23:02 INFO   root: Running the uninstaller...
12-09 23:02 INFO   CommonBackend: This is the uninstaller running
12-09 23:02 DEBUG  WindowsFrontend: __init__...
12-09 23:02 DEBUG  WindowsFrontend: on_init...
12-09 23:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\translations, languages=['en_US', 'en']
12-09 23:02 INFO   root: Received settings
12-09 23:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\translations, languages=['en_US', 'en']
12-09 23:02 DEBUG  TaskList: # Running tasklist...
12-09 23:02 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 23:02 DEBUG  WindowsBackend: Could not find bcd id
12-09 23:02 DEBUG  WindowsBackend: undo_bootini C:
12-09 23:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69654.1484375 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: undo_bootini D:
12-09 23:02 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: undo_bootini Q:
12-09 23:02 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 23:02 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 23:02 DEBUG  TaskList: ## Running Remove target dir...
12-09 23:02 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 23:02 DEBUG  TaskList: ## Finished Remove target dir
12-09 23:02 DEBUG  TaskList: ## Running Remove registry key...
12-09 23:02 DEBUG  TaskList: ## Finished Remove registry key
12-09 23:02 DEBUG  TaskList: # Finished tasklist
12-09 23:02 INFO   root: Almost finished uninstalling
12-09 23:02 INFO   root: Finished uninstallation
12-09 23:02 DEBUG  CommonBackend: Fetching basic info...
12-09 23:02 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:02 DEBUG  CommonBackend: platform=win32
12-09 23:02 DEBUG  CommonBackend: osname=nt
12-09 23:02 DEBUG  WindowsBackend: arch=amd64
12-09 23:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\data\isolist.ini
12-09 23:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:02 DEBUG  WindowsBackend: Fetching host info...
12-09 23:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:02 DEBUG  WindowsBackend: windows version=vista
12-09 23:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:02 DEBUG  WindowsBackend: windows_sp=None
12-09 23:02 DEBUG  WindowsBackend: windows_build=7601
12-09 23:02 DEBUG  WindowsBackend: gmt=-6
12-09 23:02 DEBUG  WindowsBackend: country=US
12-09 23:02 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:02 DEBUG  WindowsBackend: windows_username=John
12-09 23:02 DEBUG  WindowsBackend: user_full_name=John
12-09 23:02 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:02 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:02 DEBUG  WindowsBackend: windows_language=English
12-09 23:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:02 DEBUG  WindowsBackend: bootloader=vista
12-09 23:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69833.1640625 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(C: hd 69833.1640625 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:02 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:02 DEBUG  WindowsBackend: uninstaller_path=None
12-09 23:02 DEBUG  WindowsBackend: previous_target_dir=None
12-09 23:02 DEBUG  WindowsBackend: previous_distro_name=None
12-09 23:02 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:02 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:02 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:02 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:02 DEBUG  CommonBackend: Searching for local CDs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:02 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:02 INFO   root: Running the installer...
12-09 23:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\translations, languages=['en_US', 'en']
12-09 23:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\translations, languages=['en_US', 'en']
12-09 23:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 23:03 INFO   root: Received settings
12-09 23:03 DEBUG  CommonBackend: Searching for local CD
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD2C9.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  CommonBackend: Searching for local ISO
12-09 23:03 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:03 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD2C9.tmp\translations, languages=['en_US', 'en']
12-09 23:03 DEBUG  TaskList: # Running tasklist...
12-09 23:03 DEBUG  TaskList: ## Running select_target_dir...
12-09 23:03 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 23:03 DEBUG  TaskList: ## Finished select_target_dir
12-09 23:03 DEBUG  TaskList: ## Running create_dir_structure...
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 23:03 DEBUG  TaskList: ## Finished create_dir_structure
12-09 23:03 DEBUG  TaskList: ## Running create_uninstaller...
12-09 23:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 23:03 DEBUG  TaskList: ## Finished create_uninstaller
12-09 23:03 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 23:03 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 23:03 DEBUG  TaskList: ## Running get_diskimage...
12-09 23:03 DEBUG  TaskList: New task download
12-09 23:03 DEBUG  TaskList: ### Running download...
12-09 23:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 23:03 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-09 23:03 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-09 23:03 DEBUG  TaskList: ### Finished download
12-09 23:03 DEBUG  TaskList: ## Finished get_diskimage
12-09 23:03 DEBUG  TaskList: ## Running extract_diskimage...
12-09 23:03 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:03 DEBUG  TaskList: # Cancelling tasklist
12-09 23:03 DEBUG  TaskList: # Finished tasklist
12-09 23:03 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:03 INFO   root: === wubi 11.10 rev245 ===
12-09 23:03 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 23:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 23:03 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\data
12-09 23:03 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\bin\7z.exe
12-09 23:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 23:03 DEBUG  CommonBackend: Fetching basic info...
12-09 23:03 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:03 DEBUG  CommonBackend: platform=win32
12-09 23:03 DEBUG  CommonBackend: osname=nt
12-09 23:03 DEBUG  CommonBackend: language=en_US
12-09 23:03 DEBUG  CommonBackend: encoding=cp1252
12-09 23:03 DEBUG  WindowsBackend: arch=amd64
12-09 23:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\data\isolist.ini
12-09 23:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:03 DEBUG  WindowsBackend: Fetching host info...
12-09 23:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:03 DEBUG  WindowsBackend: windows version=vista
12-09 23:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:03 DEBUG  WindowsBackend: windows_sp=None
12-09 23:03 DEBUG  WindowsBackend: windows_build=7601
12-09 23:03 DEBUG  WindowsBackend: gmt=-6
12-09 23:03 DEBUG  WindowsBackend: country=US
12-09 23:03 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:03 DEBUG  WindowsBackend: windows_username=John
12-09 23:03 DEBUG  WindowsBackend: user_full_name=John
12-09 23:03 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:03 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:03 DEBUG  WindowsBackend: windows_language=English
12-09 23:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:03 DEBUG  WindowsBackend: bootloader=vista
12-09 23:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69830.21875 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(C: hd 69830.21875 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 23:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 23:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 23:03 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:03 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:03 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 23:03 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 23:03 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:03 DEBUG  CommonBackend: Searching for local CDs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 INFO   root: Already installed, running the uninstaller...
12-09 23:03 INFO   root: Running the uninstaller...
12-09 23:03 INFO   CommonBackend: This is the uninstaller running
12-09 23:03 DEBUG  WindowsFrontend: __init__...
12-09 23:03 DEBUG  WindowsFrontend: on_init...
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\translations, languages=['en_US', 'en']
12-09 23:03 INFO   root: Received settings
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\translations, languages=['en_US', 'en']
12-09 23:03 DEBUG  TaskList: # Running tasklist...
12-09 23:03 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 23:03 DEBUG  WindowsBackend: Could not find bcd id
12-09 23:03 DEBUG  WindowsBackend: undo_bootini C:
12-09 23:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69830.21875 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: undo_bootini D:
12-09 23:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: undo_bootini Q:
12-09 23:03 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 23:03 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 23:03 DEBUG  TaskList: ## Running Remove target dir...
12-09 23:03 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 23:03 DEBUG  TaskList: ## Finished Remove target dir
12-09 23:03 DEBUG  TaskList: ## Running Remove registry key...
12-09 23:03 DEBUG  TaskList: ## Finished Remove registry key
12-09 23:03 DEBUG  TaskList: # Finished tasklist
12-09 23:03 INFO   root: Almost finished uninstalling
12-09 23:03 INFO   root: Finished uninstallation
12-09 23:03 DEBUG  CommonBackend: Fetching basic info...
12-09 23:03 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:03 DEBUG  CommonBackend: platform=win32
12-09 23:03 DEBUG  CommonBackend: osname=nt
12-09 23:03 DEBUG  WindowsBackend: arch=amd64
12-09 23:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\data\isolist.ini
12-09 23:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:03 DEBUG  WindowsBackend: Fetching host info...
12-09 23:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:03 DEBUG  WindowsBackend: windows version=vista
12-09 23:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:03 DEBUG  WindowsBackend: windows_sp=None
12-09 23:03 DEBUG  WindowsBackend: windows_build=7601
12-09 23:03 DEBUG  WindowsBackend: gmt=-6
12-09 23:03 DEBUG  WindowsBackend: country=US
12-09 23:03 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:03 DEBUG  WindowsBackend: windows_username=John
12-09 23:03 DEBUG  WindowsBackend: user_full_name=John
12-09 23:03 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:03 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:03 DEBUG  WindowsBackend: windows_language=English
12-09 23:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:03 DEBUG  WindowsBackend: bootloader=vista
12-09 23:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69832.5898438 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(C: hd 69832.5898438 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:03 DEBUG  WindowsBackend: uninstaller_path=None
12-09 23:03 DEBUG  WindowsBackend: previous_target_dir=None
12-09 23:03 DEBUG  WindowsBackend: previous_distro_name=None
12-09 23:03 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:03 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:03 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:03 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:03 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:03 DEBUG  CommonBackend: Searching for local CDs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 INFO   root: Running the installer...
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\translations, languages=['en_US', 'en']
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\translations, languages=['en_US', 'en']
12-09 23:03 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 23:03 INFO   root: Received settings
12-09 23:03 DEBUG  CommonBackend: Searching for local CD
12-09 23:03 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:03 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:03 DEBUG  CommonBackend: Searching for local ISO
12-09 23:03 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:03 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:03 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:03 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl6DC0.tmp\translations, languages=['en_US', 'en']
12-09 23:03 DEBUG  TaskList: # Running tasklist...
12-09 23:03 DEBUG  TaskList: ## Running select_target_dir...
12-09 23:03 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 23:03 DEBUG  TaskList: ## Finished select_target_dir
12-09 23:03 DEBUG  TaskList: ## Running create_dir_structure...
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 23:03 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 23:03 DEBUG  TaskList: ## Finished create_dir_structure
12-09 23:03 DEBUG  TaskList: ## Running create_uninstaller...
12-09 23:03 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 23:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 23:03 DEBUG  TaskList: ## Finished create_uninstaller
12-09 23:03 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 23:03 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 23:03 DEBUG  TaskList: ## Running get_diskimage...
12-09 23:03 DEBUG  TaskList: New task download
12-09 23:03 DEBUG  TaskList: ### Running download...
12-09 23:03 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 23:03 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-09 23:03 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-09 23:03 DEBUG  TaskList: ### Finished download
12-09 23:03 DEBUG  TaskList: ## Finished get_diskimage
12-09 23:03 DEBUG  TaskList: ## Running extract_diskimage...
12-09 23:03 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:03 DEBUG  TaskList: # Cancelling tasklist
12-09 23:03 DEBUG  TaskList: # Finished tasklist
12-09 23:03 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:04 INFO   root: === wubi 11.10 rev245 ===
12-09 23:04 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 23:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 23:04 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\data
12-09 23:04 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\bin\7z.exe
12-09 23:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 23:04 DEBUG  CommonBackend: Fetching basic info...
12-09 23:04 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:04 DEBUG  CommonBackend: platform=win32
12-09 23:04 DEBUG  CommonBackend: osname=nt
12-09 23:04 DEBUG  CommonBackend: language=en_US
12-09 23:04 DEBUG  CommonBackend: encoding=cp1252
12-09 23:04 DEBUG  WindowsBackend: arch=amd64
12-09 23:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\data\isolist.ini
12-09 23:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:04 DEBUG  WindowsBackend: Fetching host info...
12-09 23:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:04 DEBUG  WindowsBackend: windows version=vista
12-09 23:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:04 DEBUG  WindowsBackend: windows_sp=None
12-09 23:04 DEBUG  WindowsBackend: windows_build=7601
12-09 23:04 DEBUG  WindowsBackend: gmt=-6
12-09 23:04 DEBUG  WindowsBackend: country=US
12-09 23:04 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:04 DEBUG  WindowsBackend: windows_username=John
12-09 23:04 DEBUG  WindowsBackend: user_full_name=John
12-09 23:04 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:04 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:04 DEBUG  WindowsBackend: windows_language=English
12-09 23:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:04 DEBUG  WindowsBackend: bootloader=vista
12-09 23:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69845.6171875 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(C: hd 69845.6171875 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:04 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 23:04 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 23:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 23:04 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:04 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:04 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 23:04 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 23:04 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:04 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:04 DEBUG  CommonBackend: Searching for local CDs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 INFO   root: Already installed, running the uninstaller...
12-09 23:04 INFO   root: Running the uninstaller...
12-09 23:04 INFO   CommonBackend: This is the uninstaller running
12-09 23:04 DEBUG  WindowsFrontend: __init__...
12-09 23:04 DEBUG  WindowsFrontend: on_init...
12-09 23:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\translations, languages=['en_US', 'en']
12-09 23:04 INFO   root: Received settings
12-09 23:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\translations, languages=['en_US', 'en']
12-09 23:04 DEBUG  TaskList: # Running tasklist...
12-09 23:04 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 23:04 DEBUG  WindowsBackend: Could not find bcd id
12-09 23:04 DEBUG  WindowsBackend: undo_bootini C:
12-09 23:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69845.6171875 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: undo_bootini D:
12-09 23:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: undo_bootini Q:
12-09 23:04 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 23:04 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 23:04 DEBUG  TaskList: ## Running Remove target dir...
12-09 23:04 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 23:04 DEBUG  TaskList: ## Finished Remove target dir
12-09 23:04 DEBUG  TaskList: ## Running Remove registry key...
12-09 23:04 DEBUG  TaskList: ## Finished Remove registry key
12-09 23:04 DEBUG  TaskList: # Finished tasklist
12-09 23:04 INFO   root: Almost finished uninstalling
12-09 23:04 INFO   root: Finished uninstallation
12-09 23:04 DEBUG  CommonBackend: Fetching basic info...
12-09 23:04 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:04 DEBUG  CommonBackend: platform=win32
12-09 23:04 DEBUG  CommonBackend: osname=nt
12-09 23:04 DEBUG  WindowsBackend: arch=amd64
12-09 23:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\data\isolist.ini
12-09 23:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:04 DEBUG  WindowsBackend: Fetching host info...
12-09 23:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:04 DEBUG  WindowsBackend: windows version=vista
12-09 23:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:04 DEBUG  WindowsBackend: windows_sp=None
12-09 23:04 DEBUG  WindowsBackend: windows_build=7601
12-09 23:04 DEBUG  WindowsBackend: gmt=-6
12-09 23:04 DEBUG  WindowsBackend: country=US
12-09 23:04 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:04 DEBUG  WindowsBackend: windows_username=John
12-09 23:04 DEBUG  WindowsBackend: user_full_name=John
12-09 23:04 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:04 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:04 DEBUG  WindowsBackend: windows_language=English
12-09 23:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:04 DEBUG  WindowsBackend: bootloader=vista
12-09 23:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69847.9726563 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(C: hd 69847.9726563 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:04 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:04 DEBUG  WindowsBackend: uninstaller_path=None
12-09 23:04 DEBUG  WindowsBackend: previous_target_dir=None
12-09 23:04 DEBUG  WindowsBackend: previous_distro_name=None
12-09 23:04 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:04 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:04 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:04 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:04 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:04 DEBUG  CommonBackend: Searching for local CDs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 INFO   root: Running the installer...
12-09 23:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\translations, languages=['en_US', 'en']
12-09 23:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\translations, languages=['en_US', 'en']
12-09 23:04 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 23:04 INFO   root: Received settings
12-09 23:04 DEBUG  CommonBackend: Searching for local CD
12-09 23:04 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl69BA.tmp is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:04 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:04 DEBUG  CommonBackend: Searching for local ISO
12-09 23:04 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:04 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:04 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl69BA.tmp\translations, languages=['en_US', 'en']
12-09 23:04 DEBUG  TaskList: # Running tasklist...
12-09 23:04 DEBUG  TaskList: ## Running select_target_dir...
12-09 23:04 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 23:04 DEBUG  TaskList: ## Finished select_target_dir
12-09 23:04 DEBUG  TaskList: ## Running create_dir_structure...
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 23:04 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 23:04 DEBUG  TaskList: ## Finished create_dir_structure
12-09 23:04 DEBUG  TaskList: ## Running create_uninstaller...
12-09 23:04 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 23:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 23:04 DEBUG  TaskList: ## Finished create_uninstaller
12-09 23:04 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 23:04 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 23:04 DEBUG  TaskList: ## Running get_diskimage...
12-09 23:04 DEBUG  TaskList: New task download
12-09 23:04 DEBUG  TaskList: ### Running download...
12-09 23:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 23:04 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-09 23:04 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-09 23:04 DEBUG  TaskList: ### Finished download
12-09 23:04 DEBUG  TaskList: ## Finished get_diskimage
12-09 23:04 DEBUG  TaskList: ## Running extract_diskimage...
12-09 23:04 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:04 DEBUG  TaskList: # Cancelling tasklist
12-09 23:04 DEBUG  TaskList: # Finished tasklist
12-09 23:04 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-09 23:09 INFO   root: === wubi 11.10 rev245 ===
12-09 23:09 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 23:09 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 23:09 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\data
12-09 23:09 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\bin\7z.exe
12-09 23:09 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 23:09 DEBUG  CommonBackend: Fetching basic info...
12-09 23:09 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:09 DEBUG  CommonBackend: platform=win32
12-09 23:09 DEBUG  CommonBackend: osname=nt
12-09 23:09 DEBUG  CommonBackend: language=en_US
12-09 23:09 DEBUG  CommonBackend: encoding=cp1252
12-09 23:09 DEBUG  WindowsBackend: arch=amd64
12-09 23:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\data\isolist.ini
12-09 23:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:09 DEBUG  WindowsBackend: Fetching host info...
12-09 23:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:09 DEBUG  WindowsBackend: windows version=vista
12-09 23:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:09 DEBUG  WindowsBackend: windows_sp=None
12-09 23:09 DEBUG  WindowsBackend: windows_build=7601
12-09 23:09 DEBUG  WindowsBackend: gmt=-6
12-09 23:09 DEBUG  WindowsBackend: country=US
12-09 23:09 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:09 DEBUG  WindowsBackend: windows_username=John
12-09 23:09 DEBUG  WindowsBackend: user_full_name=John
12-09 23:09 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:09 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:09 DEBUG  WindowsBackend: windows_language=English
12-09 23:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:09 DEBUG  WindowsBackend: bootloader=vista
12-09 23:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69828.015625 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(C: hd 69828.015625 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:09 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 23:09 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 23:09 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 23:09 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:09 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:09 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:09 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 23:09 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 23:09 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:09 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:09 DEBUG  CommonBackend: Searching for local CDs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 INFO   root: Already installed, running the uninstaller...
12-09 23:09 INFO   root: Running the uninstaller...
12-09 23:09 INFO   CommonBackend: This is the uninstaller running
12-09 23:09 DEBUG  WindowsFrontend: __init__...
12-09 23:09 DEBUG  WindowsFrontend: on_init...
12-09 23:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\translations, languages=['en_US', 'en']
12-09 23:09 INFO   root: Received settings
12-09 23:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\translations, languages=['en_US', 'en']
12-09 23:09 DEBUG  TaskList: # Running tasklist...
12-09 23:09 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 23:09 DEBUG  WindowsBackend: Could not find bcd id
12-09 23:09 DEBUG  WindowsBackend: undo_bootini C:
12-09 23:09 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69828.015625 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: undo_bootini D:
12-09 23:09 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: undo_bootini Q:
12-09 23:09 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 23:09 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 23:09 DEBUG  TaskList: ## Running Remove target dir...
12-09 23:09 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 23:09 DEBUG  TaskList: ## Finished Remove target dir
12-09 23:09 DEBUG  TaskList: ## Running Remove registry key...
12-09 23:09 DEBUG  TaskList: ## Finished Remove registry key
12-09 23:09 DEBUG  TaskList: # Finished tasklist
12-09 23:09 INFO   root: Almost finished uninstalling
12-09 23:09 INFO   root: Finished uninstallation
12-09 23:09 DEBUG  CommonBackend: Fetching basic info...
12-09 23:09 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:09 DEBUG  CommonBackend: platform=win32
12-09 23:09 DEBUG  CommonBackend: osname=nt
12-09 23:09 DEBUG  WindowsBackend: arch=amd64
12-09 23:09 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\data\isolist.ini
12-09 23:09 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:09 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:09 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:09 DEBUG  WindowsBackend: Fetching host info...
12-09 23:09 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:09 DEBUG  WindowsBackend: windows version=vista
12-09 23:09 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:09 DEBUG  WindowsBackend: windows_sp=None
12-09 23:09 DEBUG  WindowsBackend: windows_build=7601
12-09 23:09 DEBUG  WindowsBackend: gmt=-6
12-09 23:09 DEBUG  WindowsBackend: country=US
12-09 23:09 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:09 DEBUG  WindowsBackend: windows_username=John
12-09 23:09 DEBUG  WindowsBackend: user_full_name=John
12-09 23:09 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:09 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:09 DEBUG  WindowsBackend: windows_language=English
12-09 23:09 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:09 DEBUG  WindowsBackend: bootloader=vista
12-09 23:09 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69830.3828125 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(C: hd 69830.3828125 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:09 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:09 DEBUG  WindowsBackend: uninstaller_path=None
12-09 23:09 DEBUG  WindowsBackend: previous_target_dir=None
12-09 23:09 DEBUG  WindowsBackend: previous_distro_name=None
12-09 23:09 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:09 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:09 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:09 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:09 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:09 DEBUG  CommonBackend: Searching for local CDs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 INFO   root: Running the installer...
12-09 23:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\translations, languages=['en_US', 'en']
12-09 23:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\translations, languages=['en_US', 'en']
12-09 23:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 23:09 INFO   root: Received settings
12-09 23:09 DEBUG  CommonBackend: Searching for local CD
12-09 23:09 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCA50.tmp is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCA50.tmp\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:09 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:09 DEBUG  CommonBackend: Searching for local ISO
12-09 23:09 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:09 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:09 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:09 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:09 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCA50.tmp\translations, languages=['en_US', 'en']
12-09 23:09 DEBUG  TaskList: # Running tasklist...
12-09 23:09 DEBUG  TaskList: ## Running select_target_dir...
12-09 23:09 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 23:09 DEBUG  TaskList: ## Finished select_target_dir
12-09 23:09 DEBUG  TaskList: ## Running create_dir_structure...
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 23:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 23:09 DEBUG  TaskList: ## Finished create_dir_structure
12-09 23:09 DEBUG  TaskList: ## Running create_uninstaller...
12-09 23:09 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 23:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 23:09 DEBUG  TaskList: ## Finished create_uninstaller
12-09 23:09 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 23:09 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 23:09 DEBUG  TaskList: ## Running get_diskimage...
12-09 23:09 DEBUG  TaskList: New task download
12-09 23:09 DEBUG  TaskList: ### Running download...
12-09 23:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 23:10 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 23:10 INFO   WindowsFrontend: Operation cancelled
12-09 23:10 DEBUG  WindowsFrontend: frontend.quit
12-09 23:10 DEBUG  WindowsFrontend: frontend.on_quit
12-09 23:10 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-09 23:10 DEBUG  TaskList: # Cancelling tasklist
12-09 23:10 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-09 23:10 DEBUG  root: application.on_quit
12-09 23:10 DEBUG  root: Forceful exit
12-09 23:10 INFO   root: sys.exit
12-09 23:11 INFO   root: === wubi 11.10 rev245 ===
12-09 23:11 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-09 23:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-09 23:11 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\data
12-09 23:11 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\bin\7z.exe
12-09 23:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-09 23:11 DEBUG  CommonBackend: Fetching basic info...
12-09 23:11 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:11 DEBUG  CommonBackend: platform=win32
12-09 23:11 DEBUG  CommonBackend: osname=nt
12-09 23:11 DEBUG  CommonBackend: language=en_US
12-09 23:11 DEBUG  CommonBackend: encoding=cp1252
12-09 23:11 DEBUG  WindowsBackend: arch=amd64
12-09 23:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\data\isolist.ini
12-09 23:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:11 DEBUG  WindowsBackend: Fetching host info...
12-09 23:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:11 DEBUG  WindowsBackend: windows version=vista
12-09 23:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:11 DEBUG  WindowsBackend: windows_sp=None
12-09 23:11 DEBUG  WindowsBackend: windows_build=7601
12-09 23:11 DEBUG  WindowsBackend: gmt=-6
12-09 23:11 DEBUG  WindowsBackend: country=US
12-09 23:11 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:11 DEBUG  WindowsBackend: windows_username=John
12-09 23:11 DEBUG  WindowsBackend: user_full_name=John
12-09 23:11 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:11 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:11 DEBUG  WindowsBackend: windows_language=English
12-09 23:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:11 DEBUG  WindowsBackend: bootloader=vista
12-09 23:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69124.78125 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(C: hd 69124.78125 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-09 23:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-09 23:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-09 23:11 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:11 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:11 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-09 23:11 DEBUG  CommonBackend: locale=en_US.UTF-8
12-09 23:11 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:11 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:11 DEBUG  CommonBackend: Searching for local CDs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 INFO   root: Already installed, running the uninstaller...
12-09 23:11 INFO   root: Running the uninstaller...
12-09 23:11 INFO   CommonBackend: This is the uninstaller running
12-09 23:11 DEBUG  WindowsFrontend: __init__...
12-09 23:11 DEBUG  WindowsFrontend: on_init...
12-09 23:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\translations, languages=['en_US', 'en']
12-09 23:11 INFO   root: Received settings
12-09 23:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\translations, languages=['en_US', 'en']
12-09 23:11 DEBUG  TaskList: # Running tasklist...
12-09 23:11 DEBUG  TaskList: ## Running Remove bootloader entry...
12-09 23:11 DEBUG  WindowsBackend: Could not find bcd id
12-09 23:11 DEBUG  WindowsBackend: undo_bootini C:
12-09 23:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69124.78125 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: undo_bootini D:
12-09 23:11 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: undo_bootini Q:
12-09 23:11 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-09 23:11 DEBUG  TaskList: ## Finished Remove bootloader entry
12-09 23:11 DEBUG  TaskList: ## Running Remove target dir...
12-09 23:11 DEBUG  CommonBackend: Deleting C:\ubuntu
12-09 23:11 DEBUG  TaskList: ## Finished Remove target dir
12-09 23:11 DEBUG  TaskList: ## Running Remove registry key...
12-09 23:11 DEBUG  TaskList: ## Finished Remove registry key
12-09 23:11 DEBUG  TaskList: # Finished tasklist
12-09 23:11 INFO   root: Almost finished uninstalling
12-09 23:11 INFO   root: Finished uninstallation
12-09 23:11 DEBUG  CommonBackend: Fetching basic info...
12-09 23:11 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-09 23:11 DEBUG  CommonBackend: platform=win32
12-09 23:11 DEBUG  CommonBackend: osname=nt
12-09 23:11 DEBUG  WindowsBackend: arch=amd64
12-09 23:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\data\isolist.ini
12-09 23:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-09 23:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-09 23:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-09 23:11 DEBUG  WindowsBackend: Fetching host info...
12-09 23:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-09 23:11 DEBUG  WindowsBackend: windows version=vista
12-09 23:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-09 23:11 DEBUG  WindowsBackend: windows_sp=None
12-09 23:11 DEBUG  WindowsBackend: windows_build=7601
12-09 23:11 DEBUG  WindowsBackend: gmt=-6
12-09 23:11 DEBUG  WindowsBackend: country=US
12-09 23:11 DEBUG  WindowsBackend: timezone=America/Chicago
12-09 23:11 DEBUG  WindowsBackend: windows_username=John
12-09 23:11 DEBUG  WindowsBackend: user_full_name=John
12-09 23:11 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-09 23:11 DEBUG  WindowsBackend: windows_language_code=1033
12-09 23:11 DEBUG  WindowsBackend: windows_language=English
12-09 23:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-09 23:11 DEBUG  WindowsBackend: bootloader=vista
12-09 23:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69140.2734375 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(C: hd 69140.2734375 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-09 23:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-09 23:11 DEBUG  WindowsBackend: uninstaller_path=None
12-09 23:11 DEBUG  WindowsBackend: previous_target_dir=None
12-09 23:11 DEBUG  WindowsBackend: previous_distro_name=None
12-09 23:11 DEBUG  WindowsBackend: keyboard_id=67699721
12-09 23:11 DEBUG  WindowsBackend: keyboard_layout=us
12-09 23:11 DEBUG  WindowsBackend: keyboard_variant=
12-09 23:11 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-09 23:11 DEBUG  CommonBackend: Searching ISOs on USB devices
12-09 23:11 DEBUG  CommonBackend: Searching for local CDs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 INFO   root: Running the installer...
12-09 23:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\translations, languages=['en_US', 'en']
12-09 23:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\translations, languages=['en_US', 'en']
12-09 23:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-09 23:11 INFO   root: Received settings
12-09 23:11 DEBUG  CommonBackend: Searching for local CD
12-09 23:11 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-09 23:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-09 23:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-09 23:11 DEBUG  CommonBackend: Searching for local ISO
12-09 23:11 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:11 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-amd64.iso
12-09 23:11 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-09 23:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-09 23:11 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-09 23:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8DCD.tmp\translations, languages=['en_US', 'en']
12-09 23:11 DEBUG  TaskList: # Running tasklist...
12-09 23:11 DEBUG  TaskList: ## Running select_target_dir...
12-09 23:11 INFO   WindowsBackend: Installing into C:\ubuntu
12-09 23:11 DEBUG  TaskList: ## Finished select_target_dir
12-09 23:11 DEBUG  TaskList: ## Running create_dir_structure...
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-09 23:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-09 23:11 DEBUG  TaskList: ## Finished create_dir_structure
12-09 23:11 DEBUG  TaskList: ## Running create_uninstaller...
12-09 23:11 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-09 23:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-09 23:11 DEBUG  TaskList: ## Finished create_uninstaller
12-09 23:11 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-09 23:11 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-09 23:11 DEBUG  TaskList: ## Running get_diskimage...
12-09 23:11 DEBUG  TaskList: New task download
12-09 23:11 DEBUG  TaskList: ### Running download...
12-09 23:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-09 23:11 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-09 23:12 INFO   WindowsFrontend: Operation cancelled
12-09 23:12 DEBUG  WindowsFrontend: frontend.quit
12-09 23:12 DEBUG  WindowsFrontend: frontend.on_quit
12-09 23:12 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-09 23:12 DEBUG  TaskList: # Cancelling tasklist
12-09 23:12 DEBUG  downloader: download finished (read 15360000 bytes)
12-09 23:12 DEBUG  TaskList: ### Finished download
12-09 23:12 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-09 23:12 DEBUG  root: application.on_quit
12-09 23:12 DEBUG  root: Forceful exit
12-09 23:12 INFO   root: sys.exit
12-10 03:46 INFO   root: === wubi 11.10 rev245 ===
12-10 03:46 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:46 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\data
12-10 03:46 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\bin\7z.exe
12-10 03:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:46 DEBUG  CommonBackend: Fetching basic info...
12-10 03:46 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:46 DEBUG  CommonBackend: platform=win32
12-10 03:46 DEBUG  CommonBackend: osname=nt
12-10 03:46 DEBUG  CommonBackend: language=en_US
12-10 03:46 DEBUG  CommonBackend: encoding=cp1252
12-10 03:46 DEBUG  WindowsBackend: arch=amd64
12-10 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\data\isolist.ini
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:46 DEBUG  WindowsBackend: Fetching host info...
12-10 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:46 DEBUG  WindowsBackend: windows version=vista
12-10 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:46 DEBUG  WindowsBackend: windows_sp=None
12-10 03:46 DEBUG  WindowsBackend: windows_build=7601
12-10 03:46 DEBUG  WindowsBackend: gmt=-6
12-10 03:46 DEBUG  WindowsBackend: country=US
12-10 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:46 DEBUG  WindowsBackend: windows_username=John
12-10 03:46 DEBUG  WindowsBackend: user_full_name=John
12-10 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:46 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:46 DEBUG  WindowsBackend: windows_language=English
12-10 03:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:46 DEBUG  WindowsBackend: bootloader=vista
12-10 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68614.265625 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 68614.265625 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:46 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:46 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:46 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:46 DEBUG  CommonBackend: Searching for local CDs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 INFO   root: Already installed, running the uninstaller...
12-10 03:46 INFO   root: Running the uninstaller...
12-10 03:46 INFO   CommonBackend: This is the uninstaller running
12-10 03:46 DEBUG  WindowsFrontend: __init__...
12-10 03:46 DEBUG  WindowsFrontend: on_init...
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\translations, languages=['en_US', 'en']
12-10 03:46 INFO   root: Received settings
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  TaskList: # Running tasklist...
12-10 03:46 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:46 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:46 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68614.265625 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:46 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:46 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:46 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:46 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:46 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:46 DEBUG  TaskList: # Finished tasklist
12-10 03:46 INFO   root: Almost finished uninstalling
12-10 03:46 INFO   root: Finished uninstallation
12-10 03:46 DEBUG  CommonBackend: Fetching basic info...
12-10 03:46 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:46 DEBUG  CommonBackend: platform=win32
12-10 03:46 DEBUG  CommonBackend: osname=nt
12-10 03:46 DEBUG  WindowsBackend: arch=amd64
12-10 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\data\isolist.ini
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:46 DEBUG  WindowsBackend: Fetching host info...
12-10 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:46 DEBUG  WindowsBackend: windows version=vista
12-10 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:46 DEBUG  WindowsBackend: windows_sp=None
12-10 03:46 DEBUG  WindowsBackend: windows_build=7601
12-10 03:46 DEBUG  WindowsBackend: gmt=-6
12-10 03:46 DEBUG  WindowsBackend: country=US
12-10 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:46 DEBUG  WindowsBackend: windows_username=John
12-10 03:46 DEBUG  WindowsBackend: user_full_name=John
12-10 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:46 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:46 DEBUG  WindowsBackend: windows_language=English
12-10 03:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:46 DEBUG  WindowsBackend: bootloader=vista
12-10 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68631.2734375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 68631.2734375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:46 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:46 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:46 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:46 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:46 DEBUG  CommonBackend: Searching for local CDs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 INFO   root: Running the installer...
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\translations, languages=['en_US', 'en']
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:46 INFO   root: Received settings
12-10 03:46 DEBUG  CommonBackend: Searching for local CD
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylF29D.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylF29D.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  CommonBackend: Searching for local ISO
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylF29D.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  TaskList: # Running tasklist...
12-10 03:46 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:46 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:46 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:46 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:46 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:46 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:46 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:46 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:46 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:46 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:46 DEBUG  TaskList: New task download
12-10 03:46 DEBUG  TaskList: ### Running download...
12-10 03:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:46 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 03:46 INFO   WindowsFrontend: Operation cancelled
12-10 03:46 DEBUG  WindowsFrontend: frontend.quit
12-10 03:46 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:46 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 03:46 DEBUG  TaskList: # Cancelling tasklist
12-10 03:46 DEBUG  downloader: download finished (read 10657792 bytes)
12-10 03:46 DEBUG  TaskList: ### Finished download
12-10 03:46 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 03:46 DEBUG  root: application.on_quit
12-10 03:46 DEBUG  root: Forceful exit
12-10 03:46 INFO   root: sys.exit
12-10 03:46 INFO   root: === wubi 11.10 rev245 ===
12-10 03:46 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:46 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\data
12-10 03:46 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\bin\7z.exe
12-10 03:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:46 DEBUG  CommonBackend: Fetching basic info...
12-10 03:46 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:46 DEBUG  CommonBackend: platform=win32
12-10 03:46 DEBUG  CommonBackend: osname=nt
12-10 03:46 DEBUG  CommonBackend: language=en_US
12-10 03:46 DEBUG  CommonBackend: encoding=cp1252
12-10 03:46 DEBUG  WindowsBackend: arch=amd64
12-10 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\data\isolist.ini
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:46 DEBUG  WindowsBackend: Fetching host info...
12-10 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:46 DEBUG  WindowsBackend: windows version=vista
12-10 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:46 DEBUG  WindowsBackend: windows_sp=None
12-10 03:46 DEBUG  WindowsBackend: windows_build=7601
12-10 03:46 DEBUG  WindowsBackend: gmt=-6
12-10 03:46 DEBUG  WindowsBackend: country=US
12-10 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:46 DEBUG  WindowsBackend: windows_username=John
12-10 03:46 DEBUG  WindowsBackend: user_full_name=John
12-10 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:46 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:46 DEBUG  WindowsBackend: windows_language=English
12-10 03:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:46 DEBUG  WindowsBackend: bootloader=vista
12-10 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68618.7109375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 68618.7109375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:46 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:46 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:46 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:46 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:46 DEBUG  CommonBackend: Searching for local CDs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 INFO   root: Already installed, running the uninstaller...
12-10 03:46 INFO   root: Running the uninstaller...
12-10 03:46 INFO   CommonBackend: This is the uninstaller running
12-10 03:46 DEBUG  WindowsFrontend: __init__...
12-10 03:46 DEBUG  WindowsFrontend: on_init...
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\translations, languages=['en_US', 'en']
12-10 03:46 INFO   root: Received settings
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  TaskList: # Running tasklist...
12-10 03:46 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:46 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:46 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68618.7109375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:46 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:46 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:46 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:46 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:46 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:46 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:46 DEBUG  TaskList: # Finished tasklist
12-10 03:46 INFO   root: Almost finished uninstalling
12-10 03:46 INFO   root: Finished uninstallation
12-10 03:46 DEBUG  CommonBackend: Fetching basic info...
12-10 03:46 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:46 DEBUG  CommonBackend: platform=win32
12-10 03:46 DEBUG  CommonBackend: osname=nt
12-10 03:46 DEBUG  WindowsBackend: arch=amd64
12-10 03:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\data\isolist.ini
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:46 DEBUG  WindowsBackend: Fetching host info...
12-10 03:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:46 DEBUG  WindowsBackend: windows version=vista
12-10 03:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:46 DEBUG  WindowsBackend: windows_sp=None
12-10 03:46 DEBUG  WindowsBackend: windows_build=7601
12-10 03:46 DEBUG  WindowsBackend: gmt=-6
12-10 03:46 DEBUG  WindowsBackend: country=US
12-10 03:46 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:46 DEBUG  WindowsBackend: windows_username=John
12-10 03:46 DEBUG  WindowsBackend: user_full_name=John
12-10 03:46 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:46 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:46 DEBUG  WindowsBackend: windows_language=English
12-10 03:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:46 DEBUG  WindowsBackend: bootloader=vista
12-10 03:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68631.234375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(C: hd 68631.234375 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:46 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:46 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:46 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:46 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:46 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:46 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:46 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:46 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:46 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:46 DEBUG  CommonBackend: Searching for local CDs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 INFO   root: Running the installer...
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\translations, languages=['en_US', 'en']
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:46 INFO   root: Received settings
12-10 03:46 DEBUG  CommonBackend: Searching for local CD
12-10 03:46 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl7FED.tmp is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:46 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:46 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:46 DEBUG  CommonBackend: Searching for local ISO
12-10 03:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl7FED.tmp\translations, languages=['en_US', 'en']
12-10 03:46 DEBUG  TaskList: # Running tasklist...
12-10 03:46 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:46 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:46 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:46 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:46 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:46 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:46 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:46 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:46 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:46 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:46 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:46 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:46 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:46 DEBUG  TaskList: New task download
12-10 03:46 DEBUG  TaskList: ### Running download...
12-10 03:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:46 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-10 03:46 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-10 03:46 DEBUG  TaskList: ### Finished download
12-10 03:46 DEBUG  TaskList: ## Finished get_diskimage
12-10 03:46 DEBUG  TaskList: ## Running extract_diskimage...
12-10 03:46 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:46 DEBUG  TaskList: # Cancelling tasklist
12-10 03:46 DEBUG  TaskList: # Finished tasklist
12-10 03:46 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:47 INFO   root: === wubi 11.10 rev245 ===
12-10 03:47 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:47 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\data
12-10 03:47 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylA51.tmp\bin\7z.exe
12-10 03:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:47 DEBUG  CommonBackend: Fetching basic info...
12-10 03:47 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:47 DEBUG  CommonBackend: platform=win32
12-10 03:47 DEBUG  CommonBackend: osname=nt
12-10 03:47 DEBUG  CommonBackend: language=en_US
12-10 03:47 DEBUG  CommonBackend: encoding=cp1252
12-10 03:47 DEBUG  WindowsBackend: arch=amd64
12-10 03:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylA51.tmp\data\isolist.ini
12-10 03:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:47 DEBUG  WindowsBackend: Fetching host info...
12-10 03:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:47 DEBUG  WindowsBackend: windows version=vista
12-10 03:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:47 DEBUG  WindowsBackend: windows_sp=None
12-10 03:47 DEBUG  WindowsBackend: windows_build=7601
12-10 03:47 DEBUG  WindowsBackend: gmt=-6
12-10 03:47 DEBUG  WindowsBackend: country=US
12-10 03:47 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:47 DEBUG  WindowsBackend: windows_username=John
12-10 03:47 DEBUG  WindowsBackend: user_full_name=John
12-10 03:47 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:47 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:47 DEBUG  WindowsBackend: windows_language=English
12-10 03:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:47 DEBUG  WindowsBackend: bootloader=vista
12-10 03:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68634.8867188 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(C: hd 68634.8867188 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:47 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:47 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:47 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:47 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:47 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:47 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:47 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:47 DEBUG  CommonBackend: Searching for local CDs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:47 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 INFO   root: Already installed, running the uninstaller...
12-10 03:47 INFO   root: Running the uninstaller...
12-10 03:47 INFO   CommonBackend: This is the uninstaller running
12-10 03:47 DEBUG  WindowsFrontend: __init__...
12-10 03:47 DEBUG  WindowsFrontend: on_init...
12-10 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\translations, languages=['en_US', 'en']
12-10 03:47 INFO   root: Received settings
12-10 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\translations, languages=['en_US', 'en']
12-10 03:47 DEBUG  TaskList: # Running tasklist...
12-10 03:47 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:47 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:47 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68634.8867188 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:47 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:47 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:47 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:47 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:47 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:47 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:47 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:47 DEBUG  TaskList: # Finished tasklist
12-10 03:47 INFO   root: Almost finished uninstalling
12-10 03:47 INFO   root: Finished uninstallation
12-10 03:47 DEBUG  CommonBackend: Fetching basic info...
12-10 03:47 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:47 DEBUG  CommonBackend: platform=win32
12-10 03:47 DEBUG  CommonBackend: osname=nt
12-10 03:47 DEBUG  WindowsBackend: arch=amd64
12-10 03:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylA51.tmp\data\isolist.ini
12-10 03:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:47 DEBUG  WindowsBackend: Fetching host info...
12-10 03:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:47 DEBUG  WindowsBackend: windows version=vista
12-10 03:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:47 DEBUG  WindowsBackend: windows_sp=None
12-10 03:47 DEBUG  WindowsBackend: windows_build=7601
12-10 03:47 DEBUG  WindowsBackend: gmt=-6
12-10 03:47 DEBUG  WindowsBackend: country=US
12-10 03:47 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:47 DEBUG  WindowsBackend: windows_username=John
12-10 03:47 DEBUG  WindowsBackend: user_full_name=John
12-10 03:47 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:47 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:47 DEBUG  WindowsBackend: windows_language=English
12-10 03:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:47 DEBUG  WindowsBackend: bootloader=vista
12-10 03:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68637.2539063 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(C: hd 68637.2539063 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:47 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:47 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:47 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:47 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:47 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:47 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:47 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:47 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:47 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:47 DEBUG  CommonBackend: Searching for local CDs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 INFO   root: Running the installer...
12-10 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\translations, languages=['en_US', 'en']
12-10 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\translations, languages=['en_US', 'en']
12-10 03:47 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:47 INFO   root: Received settings
12-10 03:47 DEBUG  CommonBackend: Searching for local CD
12-10 03:47 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA51.tmp is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA51.tmp\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:47 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:47 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:47 DEBUG  CommonBackend: Searching for local ISO
12-10 03:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA51.tmp\translations, languages=['en_US', 'en']
12-10 03:47 DEBUG  TaskList: # Running tasklist...
12-10 03:47 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:47 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:47 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:47 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:47 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:47 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:47 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:47 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:47 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:47 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:47 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:47 DEBUG  TaskList: New task download
12-10 03:47 DEBUG  TaskList: ### Running download...
12-10 03:47 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:47 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 03:48 INFO   WindowsFrontend: Operation cancelled
12-10 03:48 DEBUG  WindowsFrontend: frontend.quit
12-10 03:48 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:48 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 03:48 DEBUG  TaskList: # Cancelling tasklist
12-10 03:48 DEBUG  downloader: download finished (read 49569792 bytes)
12-10 03:48 DEBUG  TaskList: ### Finished download
12-10 03:48 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 03:48 DEBUG  root: application.on_quit
12-10 03:48 DEBUG  root: Forceful exit
12-10 03:48 INFO   root: sys.exit
12-10 03:50 INFO   root: === wubi 11.10 rev245 ===
12-10 03:50 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:50 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\data
12-10 03:50 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\bin\7z.exe
12-10 03:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:50 DEBUG  CommonBackend: Fetching basic info...
12-10 03:50 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:50 DEBUG  CommonBackend: platform=win32
12-10 03:50 DEBUG  CommonBackend: osname=nt
12-10 03:50 DEBUG  CommonBackend: language=en_US
12-10 03:50 DEBUG  CommonBackend: encoding=cp1252
12-10 03:50 DEBUG  WindowsBackend: arch=amd64
12-10 03:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\data\isolist.ini
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:50 DEBUG  WindowsBackend: Fetching host info...
12-10 03:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:50 DEBUG  WindowsBackend: windows version=vista
12-10 03:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:50 DEBUG  WindowsBackend: windows_sp=None
12-10 03:50 DEBUG  WindowsBackend: windows_build=7601
12-10 03:50 DEBUG  WindowsBackend: gmt=-6
12-10 03:50 DEBUG  WindowsBackend: country=US
12-10 03:50 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:50 DEBUG  WindowsBackend: windows_username=John
12-10 03:50 DEBUG  WindowsBackend: user_full_name=John
12-10 03:50 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:50 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:50 DEBUG  WindowsBackend: windows_language=English
12-10 03:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:50 DEBUG  WindowsBackend: bootloader=vista
12-10 03:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68594.0234375 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(C: hd 68594.0234375 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:50 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:50 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:50 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:50 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:50 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:50 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:50 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:50 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:50 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:50 DEBUG  CommonBackend: Searching for local CDs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 INFO   root: Already installed, running the uninstaller...
12-10 03:50 INFO   root: Running the uninstaller...
12-10 03:50 INFO   CommonBackend: This is the uninstaller running
12-10 03:50 DEBUG  WindowsFrontend: __init__...
12-10 03:50 DEBUG  WindowsFrontend: on_init...
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\translations, languages=['en_US', 'en']
12-10 03:50 INFO   root: Received settings
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\translations, languages=['en_US', 'en']
12-10 03:50 DEBUG  TaskList: # Running tasklist...
12-10 03:50 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:50 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:50 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:50 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68594.0234375 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:50 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:50 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:50 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:50 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:50 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:50 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:50 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:50 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:50 DEBUG  TaskList: # Finished tasklist
12-10 03:50 INFO   root: Almost finished uninstalling
12-10 03:50 INFO   root: Finished uninstallation
12-10 03:50 DEBUG  CommonBackend: Fetching basic info...
12-10 03:50 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:50 DEBUG  CommonBackend: platform=win32
12-10 03:50 DEBUG  CommonBackend: osname=nt
12-10 03:50 DEBUG  WindowsBackend: arch=amd64
12-10 03:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\data\isolist.ini
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:50 DEBUG  WindowsBackend: Fetching host info...
12-10 03:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:50 DEBUG  WindowsBackend: windows version=vista
12-10 03:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:50 DEBUG  WindowsBackend: windows_sp=None
12-10 03:50 DEBUG  WindowsBackend: windows_build=7601
12-10 03:50 DEBUG  WindowsBackend: gmt=-6
12-10 03:50 DEBUG  WindowsBackend: country=US
12-10 03:50 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:50 DEBUG  WindowsBackend: windows_username=John
12-10 03:50 DEBUG  WindowsBackend: user_full_name=John
12-10 03:50 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:50 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:50 DEBUG  WindowsBackend: windows_language=English
12-10 03:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:50 DEBUG  WindowsBackend: bootloader=vista
12-10 03:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68643.65625 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(C: hd 68643.65625 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:50 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:50 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:50 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:50 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:50 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:50 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:50 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:50 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:50 DEBUG  CommonBackend: Searching for local CDs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylEA5.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylEA5.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 INFO   root: Running the installer...
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\translations, languages=['en_US', 'en']
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylEA5.tmp\translations, languages=['en_US', 'en']
12-10 03:50 INFO   WindowsFrontend: Operation cancelled
12-10 03:50 DEBUG  WindowsFrontend: frontend.quit
12-10 03:50 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:50 DEBUG  root: application.on_quit
12-10 03:50 INFO   root: sys.exit
12-10 03:50 INFO   root: === wubi 11.10 rev245 ===
12-10 03:50 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:50 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\data
12-10 03:50 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\bin\7z.exe
12-10 03:50 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:50 DEBUG  CommonBackend: Fetching basic info...
12-10 03:50 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:50 DEBUG  CommonBackend: platform=win32
12-10 03:50 DEBUG  CommonBackend: osname=nt
12-10 03:50 DEBUG  CommonBackend: language=en_US
12-10 03:50 DEBUG  CommonBackend: encoding=cp1252
12-10 03:50 DEBUG  WindowsBackend: arch=amd64
12-10 03:50 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\data\isolist.ini
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:50 DEBUG  WindowsBackend: Fetching host info...
12-10 03:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:50 DEBUG  WindowsBackend: windows version=vista
12-10 03:50 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:50 DEBUG  WindowsBackend: windows_sp=None
12-10 03:50 DEBUG  WindowsBackend: windows_build=7601
12-10 03:50 DEBUG  WindowsBackend: gmt=-6
12-10 03:50 DEBUG  WindowsBackend: country=US
12-10 03:50 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:50 DEBUG  WindowsBackend: windows_username=John
12-10 03:50 DEBUG  WindowsBackend: user_full_name=John
12-10 03:50 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:50 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:50 DEBUG  WindowsBackend: windows_language=English
12-10 03:50 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:50 DEBUG  WindowsBackend: bootloader=vista
12-10 03:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68643.6015625 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(C: hd 68643.6015625 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:50 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:50 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:50 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:50 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:50 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:50 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:50 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:50 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:50 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:50 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:50 DEBUG  CommonBackend: Searching for local CDs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:50 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 INFO   root: Running the installer...
12-10 03:50 DEBUG  WindowsFrontend: __init__...
12-10 03:50 DEBUG  WindowsFrontend: on_init...
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\translations, languages=['en_US', 'en']
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\translations, languages=['en_US', 'en']
12-10 03:50 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:50 INFO   root: Received settings
12-10 03:50 DEBUG  CommonBackend: Searching for local CD
12-10 03:50 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl3528.tmp is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl3528.tmp\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:50 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:50 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:50 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:50 DEBUG  CommonBackend: Searching for local ISO
12-10 03:50 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl3528.tmp\translations, languages=['en_US', 'en']
12-10 03:50 DEBUG  TaskList: # Running tasklist...
12-10 03:50 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:50 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:50 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:50 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:50 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:50 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:50 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:50 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:50 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:50 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:50 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:50 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:50 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:50 DEBUG  TaskList: New task download
12-10 03:50 DEBUG  TaskList: ### Running download...
12-10 03:50 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:50 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 03:51 INFO   WindowsFrontend: Operation cancelled
12-10 03:51 DEBUG  WindowsFrontend: frontend.quit
12-10 03:51 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:51 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 03:51 DEBUG  TaskList: # Cancelling tasklist
12-10 03:51 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 03:51 DEBUG  root: application.on_quit
12-10 03:51 DEBUG  root: Forceful exit
12-10 03:51 INFO   root: sys.exit
12-10 03:51 INFO   root: === wubi 11.10 rev245 ===
12-10 03:51 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-10 03:51 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\data
12-10 03:51 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\bin\7z.exe
12-10 03:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:51 DEBUG  CommonBackend: Fetching basic info...
12-10 03:51 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:51 DEBUG  CommonBackend: platform=win32
12-10 03:51 DEBUG  CommonBackend: osname=nt
12-10 03:51 DEBUG  CommonBackend: language=en_US
12-10 03:51 DEBUG  CommonBackend: encoding=cp1252
12-10 03:51 DEBUG  WindowsBackend: arch=amd64
12-10 03:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\data\isolist.ini
12-10 03:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:51 DEBUG  WindowsBackend: Fetching host info...
12-10 03:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:51 DEBUG  WindowsBackend: windows version=vista
12-10 03:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:51 DEBUG  WindowsBackend: windows_sp=None
12-10 03:51 DEBUG  WindowsBackend: windows_build=7601
12-10 03:51 DEBUG  WindowsBackend: gmt=-6
12-10 03:51 DEBUG  WindowsBackend: country=US
12-10 03:51 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:51 DEBUG  WindowsBackend: windows_username=John
12-10 03:51 DEBUG  WindowsBackend: user_full_name=John
12-10 03:51 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:51 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:51 DEBUG  WindowsBackend: windows_language=English
12-10 03:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:51 DEBUG  WindowsBackend: bootloader=vista
12-10 03:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68638.1796875 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(C: hd 68638.1796875 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:51 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:51 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:51 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:51 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:51 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:51 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:51 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:51 DEBUG  CommonBackend: Searching for local CDs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 INFO   root: Already installed, running the uninstaller...
12-10 03:51 INFO   root: Running the uninstaller...
12-10 03:51 INFO   CommonBackend: This is the uninstaller running
12-10 03:51 DEBUG  WindowsFrontend: __init__...
12-10 03:51 DEBUG  WindowsFrontend: on_init...
12-10 03:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\translations, languages=['en_US', 'en']
12-10 03:51 INFO   root: Received settings
12-10 03:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\translations, languages=['en_US', 'en']
12-10 03:51 DEBUG  TaskList: # Running tasklist...
12-10 03:51 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:51 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:51 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:51 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68638.1796875 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:51 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:51 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:51 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:51 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:51 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:51 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:51 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:51 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:51 DEBUG  TaskList: # Finished tasklist
12-10 03:51 INFO   root: Almost finished uninstalling
12-10 03:51 INFO   root: Finished uninstallation
12-10 03:51 DEBUG  CommonBackend: Fetching basic info...
12-10 03:51 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:51 DEBUG  CommonBackend: platform=win32
12-10 03:51 DEBUG  CommonBackend: osname=nt
12-10 03:51 DEBUG  WindowsBackend: arch=amd64
12-10 03:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\data\isolist.ini
12-10 03:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:51 DEBUG  WindowsBackend: Fetching host info...
12-10 03:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:51 DEBUG  WindowsBackend: windows version=vista
12-10 03:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:51 DEBUG  WindowsBackend: windows_sp=None
12-10 03:51 DEBUG  WindowsBackend: windows_build=7601
12-10 03:51 DEBUG  WindowsBackend: gmt=-6
12-10 03:51 DEBUG  WindowsBackend: country=US
12-10 03:51 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:51 DEBUG  WindowsBackend: windows_username=John
12-10 03:51 DEBUG  WindowsBackend: user_full_name=John
12-10 03:51 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:51 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:51 DEBUG  WindowsBackend: windows_language=English
12-10 03:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:51 DEBUG  WindowsBackend: bootloader=vista
12-10 03:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68643.03125 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(C: hd 68643.03125 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:51 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:51 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:51 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:51 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:51 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:51 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:51 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:51 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:51 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:51 DEBUG  CommonBackend: Searching for local CDs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 INFO   root: Running the installer...
12-10 03:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\translations, languages=['en_US', 'en']
12-10 03:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\translations, languages=['en_US', 'en']
12-10 03:51 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:51 INFO   root: Received settings
12-10 03:51 DEBUG  CommonBackend: Searching for local CD
12-10 03:51 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylD54D.tmp is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylD54D.tmp\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:51 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:51 DEBUG  CommonBackend: Searching for local ISO
12-10 03:51 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:51 DEBUG  WindowsBackend:   extracting .disk\info from D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:51 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:51 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:51 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:51 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-10 03:51 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-10 03:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylD54D.tmp\translations, languages=['en_US', 'en']
12-10 03:51 DEBUG  TaskList: # Running tasklist...
12-10 03:51 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:51 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:51 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:51 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:51 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:51 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:51 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:51 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:51 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:51 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:51 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:51 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:51 DEBUG  TaskList: New task download
12-10 03:51 DEBUG  TaskList: ### Running download...
12-10 03:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:51 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 03:54 INFO   WindowsFrontend: Operation cancelled
12-10 03:54 DEBUG  WindowsFrontend: frontend.quit
12-10 03:54 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:54 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 03:54 DEBUG  TaskList: # Cancelling tasklist
12-10 03:54 DEBUG  downloader: download finished (read 158261248 bytes)
12-10 03:54 DEBUG  TaskList: ### Finished download
12-10 03:54 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 03:54 DEBUG  root: application.on_quit
12-10 03:54 DEBUG  root: Forceful exit
12-10 03:54 INFO   root: sys.exit
12-10 03:54 INFO   root: === wubi 11.10 rev245 ===
12-10 03:54 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 03:54 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\data
12-10 03:54 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\bin\7z.exe
12-10 03:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:54 DEBUG  CommonBackend: Fetching basic info...
12-10 03:54 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:54 DEBUG  CommonBackend: platform=win32
12-10 03:54 DEBUG  CommonBackend: osname=nt
12-10 03:54 DEBUG  CommonBackend: language=en_US
12-10 03:54 DEBUG  CommonBackend: encoding=cp1252
12-10 03:54 DEBUG  WindowsBackend: arch=amd64
12-10 03:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\data\isolist.ini
12-10 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:54 DEBUG  WindowsBackend: Fetching host info...
12-10 03:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:54 DEBUG  WindowsBackend: windows version=vista
12-10 03:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:54 DEBUG  WindowsBackend: windows_sp=None
12-10 03:54 DEBUG  WindowsBackend: windows_build=7601
12-10 03:54 DEBUG  WindowsBackend: gmt=-6
12-10 03:54 DEBUG  WindowsBackend: country=US
12-10 03:54 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:54 DEBUG  WindowsBackend: windows_username=John
12-10 03:54 DEBUG  WindowsBackend: user_full_name=John
12-10 03:54 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:54 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:54 DEBUG  WindowsBackend: windows_language=English
12-10 03:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:54 DEBUG  WindowsBackend: bootloader=vista
12-10 03:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68494.765625 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(C: hd 68494.765625 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:54 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:54 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:54 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:54 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:54 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:54 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:54 DEBUG  CommonBackend: Searching for local CDs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:54 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 INFO   root: Already installed, running the uninstaller...
12-10 03:54 INFO   root: Running the uninstaller...
12-10 03:54 INFO   CommonBackend: This is the uninstaller running
12-10 03:54 DEBUG  WindowsFrontend: __init__...
12-10 03:54 DEBUG  WindowsFrontend: on_init...
12-10 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\translations, languages=['en_US', 'en']
12-10 03:54 INFO   root: Received settings
12-10 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\translations, languages=['en_US', 'en']
12-10 03:54 DEBUG  TaskList: # Running tasklist...
12-10 03:54 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:54 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:54 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 68494.765625 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:54 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:54 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:54 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:54 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:54 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:54 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:54 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:54 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:54 DEBUG  TaskList: # Finished tasklist
12-10 03:54 INFO   root: Almost finished uninstalling
12-10 03:54 INFO   root: Finished uninstallation
12-10 03:54 DEBUG  CommonBackend: Fetching basic info...
12-10 03:54 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 03:54 DEBUG  CommonBackend: platform=win32
12-10 03:54 DEBUG  CommonBackend: osname=nt
12-10 03:54 DEBUG  WindowsBackend: arch=amd64
12-10 03:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\data\isolist.ini
12-10 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:54 DEBUG  WindowsBackend: Fetching host info...
12-10 03:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:54 DEBUG  WindowsBackend: windows version=vista
12-10 03:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:54 DEBUG  WindowsBackend: windows_sp=None
12-10 03:54 DEBUG  WindowsBackend: windows_build=7601
12-10 03:54 DEBUG  WindowsBackend: gmt=-6
12-10 03:54 DEBUG  WindowsBackend: country=US
12-10 03:54 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:54 DEBUG  WindowsBackend: windows_username=John
12-10 03:54 DEBUG  WindowsBackend: user_full_name=John
12-10 03:54 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:54 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:54 DEBUG  WindowsBackend: windows_language=English
12-10 03:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:54 DEBUG  WindowsBackend: bootloader=vista
12-10 03:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 68648.0546875 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(C: hd 68648.0546875 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(D: hd 196707.144531 mb free ntfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:54 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:54 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:54 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:54 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:54 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:54 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:54 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:54 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:54 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:54 DEBUG  CommonBackend: Searching for local CDs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCB8D.tmp is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:54 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:54 INFO   root: Running the installer...
12-10 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\translations, languages=['en_US', 'en']
12-10 03:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCB8D.tmp\translations, languages=['en_US', 'en']
12-10 03:54 INFO   WindowsFrontend: Operation cancelled
12-10 03:54 DEBUG  WindowsFrontend: frontend.quit
12-10 03:54 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:54 DEBUG  root: application.on_quit
12-10 03:54 INFO   root: sys.exit
12-10 03:56 INFO   root: === wubi 11.10 rev245 ===
12-10 03:56 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-10 03:56 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\data
12-10 03:56 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\bin\7z.exe
12-10 03:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:56 DEBUG  CommonBackend: Fetching basic info...
12-10 03:56 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:56 DEBUG  CommonBackend: platform=win32
12-10 03:56 DEBUG  CommonBackend: osname=nt
12-10 03:56 DEBUG  CommonBackend: language=en_US
12-10 03:56 DEBUG  CommonBackend: encoding=cp1252
12-10 03:56 DEBUG  WindowsBackend: arch=amd64
12-10 03:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\data\isolist.ini
12-10 03:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:56 DEBUG  WindowsBackend: Fetching host info...
12-10 03:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:56 DEBUG  WindowsBackend: windows version=vista
12-10 03:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:56 DEBUG  WindowsBackend: windows_sp=None
12-10 03:56 DEBUG  WindowsBackend: windows_build=7601
12-10 03:56 DEBUG  WindowsBackend: gmt=-6
12-10 03:56 DEBUG  WindowsBackend: country=US
12-10 03:56 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:56 DEBUG  WindowsBackend: windows_username=John
12-10 03:56 DEBUG  WindowsBackend: user_full_name=John
12-10 03:56 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:56 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:56 DEBUG  WindowsBackend: windows_language=English
12-10 03:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:56 DEBUG  WindowsBackend: bootloader=vista
12-10 03:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69131.1914063 mb free ntfs)
12-10 03:56 DEBUG  WindowsBackend: drive=Drive(C: hd 69131.1914063 mb free ntfs)
12-10 03:56 DEBUG  WindowsBackend: drive=Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:56 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:56 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:56 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:56 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:56 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:56 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:56 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:56 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:56 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:56 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:56 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:56 DEBUG  CommonBackend: Searching for local CDs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:56 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 INFO   root: Running the installer...
12-10 03:56 DEBUG  WindowsFrontend: __init__...
12-10 03:56 DEBUG  WindowsFrontend: on_init...
12-10 03:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\translations, languages=['en_US', 'en']
12-10 03:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\translations, languages=['en_US', 'en']
12-10 03:56 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:56 INFO   root: Received settings
12-10 03:56 DEBUG  CommonBackend: Searching for local CD
12-10 03:56 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl565E.tmp is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl565E.tmp\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:56 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:56 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:56 DEBUG  CommonBackend: Searching for local ISO
12-10 03:56 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:56 DEBUG  WindowsBackend:   extracting .disk\info from D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:56 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:56 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:56 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:56 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-10 03:56 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-10 03:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl565E.tmp\translations, languages=['en_US', 'en']
12-10 03:56 DEBUG  TaskList: # Running tasklist...
12-10 03:56 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:56 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:56 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:56 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:56 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:56 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:56 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:56 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:56 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:56 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:56 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:56 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:56 DEBUG  TaskList: New task download
12-10 03:56 DEBUG  TaskList: ### Running download...
12-10 03:56 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:56 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-10 03:56 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-10 03:56 DEBUG  TaskList: ### Finished download
12-10 03:56 DEBUG  TaskList: ## Finished get_diskimage
12-10 03:56 DEBUG  TaskList: ## Running extract_diskimage...
12-10 03:56 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:56 DEBUG  TaskList: # Cancelling tasklist
12-10 03:56 DEBUG  TaskList: # Finished tasklist
12-10 03:56 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:57 INFO   root: === wubi 11.10 rev245 ===
12-10 03:57 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-10 03:57 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\data
12-10 03:57 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\bin\7z.exe
12-10 03:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:57 DEBUG  CommonBackend: Fetching basic info...
12-10 03:57 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-10 03:57 DEBUG  CommonBackend: platform=win32
12-10 03:57 DEBUG  CommonBackend: osname=nt
12-10 03:57 DEBUG  CommonBackend: language=en_US
12-10 03:57 DEBUG  CommonBackend: encoding=cp1252
12-10 03:57 DEBUG  WindowsBackend: arch=amd64
12-10 03:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\data\isolist.ini
12-10 03:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:57 DEBUG  WindowsBackend: Fetching host info...
12-10 03:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:57 DEBUG  WindowsBackend: windows version=vista
12-10 03:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:57 DEBUG  WindowsBackend: windows_sp=None
12-10 03:57 DEBUG  WindowsBackend: windows_build=7601
12-10 03:57 DEBUG  WindowsBackend: gmt=-6
12-10 03:57 DEBUG  WindowsBackend: country=US
12-10 03:57 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:57 DEBUG  WindowsBackend: windows_username=John
12-10 03:57 DEBUG  WindowsBackend: user_full_name=John
12-10 03:57 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:57 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:57 DEBUG  WindowsBackend: windows_language=English
12-10 03:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:57 DEBUG  WindowsBackend: bootloader=vista
12-10 03:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69128.3125 mb free ntfs)
12-10 03:57 DEBUG  WindowsBackend: drive=Drive(C: hd 69128.3125 mb free ntfs)
12-10 03:57 DEBUG  WindowsBackend: drive=Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:57 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:57 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:57 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:57 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:57 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:57 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:57 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:57 DEBUG  CommonBackend: Searching for local CDs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl1318.tmp is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl1318.tmp\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:57 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:57 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:57 INFO   root: Running the uninstaller...
12-10 03:57 INFO   CommonBackend: This is the uninstaller running
12-10 03:57 DEBUG  WindowsFrontend: __init__...
12-10 03:57 DEBUG  WindowsFrontend: on_init...
12-10 03:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\translations, languages=['en_US', 'en']
12-10 03:57 INFO   root: Received settings
12-10 03:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\translations, languages=['en_US', 'en']
12-10 03:57 DEBUG  TaskList: # Running tasklist...
12-10 03:57 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:57 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:57 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:57 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69128.3125 mb free ntfs)
12-10 03:57 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:57 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:57 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:57 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:57 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:57 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:57 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:57 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:57 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:57 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:57 DEBUG  TaskList: # Finished tasklist
12-10 03:57 INFO   root: Almost finished uninstalling
12-10 03:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl1318.tmp\translations, languages=['en_US', 'en']
12-10 03:57 INFO   root: Finished uninstallation
12-10 03:57 DEBUG  root: application.quit
12-10 03:57 DEBUG  WindowsFrontend: frontend.quit
12-10 03:57 DEBUG  WindowsFrontend: frontend.on_quit
12-10 03:57 DEBUG  root: application.on_quit
12-10 03:57 INFO   root: sys.exit
12-10 03:59 INFO   root: === wubi 11.10 rev245 ===
12-10 03:59 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-10 03:59 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\data
12-10 03:59 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\bin\7z.exe
12-10 03:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:59 DEBUG  CommonBackend: Fetching basic info...
12-10 03:59 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:59 DEBUG  CommonBackend: platform=win32
12-10 03:59 DEBUG  CommonBackend: osname=nt
12-10 03:59 DEBUG  CommonBackend: language=en_US
12-10 03:59 DEBUG  CommonBackend: encoding=cp1252
12-10 03:59 DEBUG  WindowsBackend: arch=amd64
12-10 03:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\data\isolist.ini
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:59 DEBUG  WindowsBackend: Fetching host info...
12-10 03:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:59 DEBUG  WindowsBackend: windows version=vista
12-10 03:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:59 DEBUG  WindowsBackend: windows_sp=None
12-10 03:59 DEBUG  WindowsBackend: windows_build=7601
12-10 03:59 DEBUG  WindowsBackend: gmt=-6
12-10 03:59 DEBUG  WindowsBackend: country=US
12-10 03:59 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:59 DEBUG  WindowsBackend: windows_username=John
12-10 03:59 DEBUG  WindowsBackend: user_full_name=John
12-10 03:59 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:59 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:59 DEBUG  WindowsBackend: windows_language=English
12-10 03:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:59 DEBUG  WindowsBackend: bootloader=vista
12-10 03:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69153.703125 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(C: hd 69153.703125 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:59 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:59 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:59 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:59 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:59 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:59 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:59 DEBUG  CommonBackend: Searching for local CDs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 INFO   root: Running the installer...
12-10 03:59 DEBUG  WindowsFrontend: __init__...
12-10 03:59 DEBUG  WindowsFrontend: on_init...
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 03:59 INFO   root: Received settings
12-10 03:59 DEBUG  CommonBackend: Searching for local CD
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl906C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl906C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  CommonBackend: Searching for local ISO
12-10 03:59 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:59 DEBUG  WindowsBackend:   extracting .disk\info from D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 03:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-10 03:59 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl906C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 DEBUG  TaskList: # Running tasklist...
12-10 03:59 DEBUG  TaskList: ## Running select_target_dir...
12-10 03:59 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 03:59 DEBUG  TaskList: ## Finished select_target_dir
12-10 03:59 DEBUG  TaskList: ## Running create_dir_structure...
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 03:59 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 03:59 DEBUG  TaskList: ## Finished create_dir_structure
12-10 03:59 DEBUG  TaskList: ## Running create_uninstaller...
12-10 03:59 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 03:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 03:59 DEBUG  TaskList: ## Finished create_uninstaller
12-10 03:59 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 03:59 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 03:59 DEBUG  TaskList: ## Running get_diskimage...
12-10 03:59 DEBUG  TaskList: New task download
12-10 03:59 DEBUG  TaskList: ### Running download...
12-10 03:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 03:59 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-10 03:59 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-10 03:59 DEBUG  TaskList: ### Finished download
12-10 03:59 DEBUG  TaskList: ## Finished get_diskimage
12-10 03:59 DEBUG  TaskList: ## Running extract_diskimage...
12-10 03:59 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:59 DEBUG  TaskList: # Cancelling tasklist
12-10 03:59 DEBUG  TaskList: # Finished tasklist
12-10 03:59 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 03:59 INFO   root: === wubi 11.10 rev245 ===
12-10 03:59 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 03:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\wubi.exe"']
12-10 03:59 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\data
12-10 03:59 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\bin\7z.exe
12-10 03:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 03:59 DEBUG  CommonBackend: Fetching basic info...
12-10 03:59 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:59 DEBUG  CommonBackend: platform=win32
12-10 03:59 DEBUG  CommonBackend: osname=nt
12-10 03:59 DEBUG  CommonBackend: language=en_US
12-10 03:59 DEBUG  CommonBackend: encoding=cp1252
12-10 03:59 DEBUG  WindowsBackend: arch=amd64
12-10 03:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\data\isolist.ini
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:59 DEBUG  WindowsBackend: Fetching host info...
12-10 03:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:59 DEBUG  WindowsBackend: windows version=vista
12-10 03:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:59 DEBUG  WindowsBackend: windows_sp=None
12-10 03:59 DEBUG  WindowsBackend: windows_build=7601
12-10 03:59 DEBUG  WindowsBackend: gmt=-6
12-10 03:59 DEBUG  WindowsBackend: country=US
12-10 03:59 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:59 DEBUG  WindowsBackend: windows_username=John
12-10 03:59 DEBUG  WindowsBackend: user_full_name=John
12-10 03:59 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:59 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:59 DEBUG  WindowsBackend: windows_language=English
12-10 03:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:59 DEBUG  WindowsBackend: bootloader=vista
12-10 03:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69146.09375 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(C: hd 69146.09375 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 03:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 03:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 03:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:59 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:59 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 03:59 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 03:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:59 DEBUG  CommonBackend: Searching for local CDs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 03:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 INFO   root: Already installed, running the uninstaller...
12-10 03:59 INFO   root: Running the uninstaller...
12-10 03:59 INFO   CommonBackend: This is the uninstaller running
12-10 03:59 DEBUG  WindowsFrontend: __init__...
12-10 03:59 DEBUG  WindowsFrontend: on_init...
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 INFO   root: Received settings
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 DEBUG  TaskList: # Running tasklist...
12-10 03:59 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 03:59 DEBUG  WindowsBackend: Could not find bcd id
12-10 03:59 DEBUG  WindowsBackend: undo_bootini C:
12-10 03:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69146.09375 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: undo_bootini D:
12-10 03:59 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: undo_bootini Q:
12-10 03:59 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 03:59 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 03:59 DEBUG  TaskList: ## Running Remove target dir...
12-10 03:59 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 03:59 DEBUG  TaskList: ## Finished Remove target dir
12-10 03:59 DEBUG  TaskList: ## Running Remove registry key...
12-10 03:59 DEBUG  TaskList: ## Finished Remove registry key
12-10 03:59 DEBUG  TaskList: # Finished tasklist
12-10 03:59 INFO   root: Almost finished uninstalling
12-10 03:59 INFO   root: Finished uninstallation
12-10 03:59 DEBUG  CommonBackend: Fetching basic info...
12-10 03:59 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\wubi.exe
12-10 03:59 DEBUG  CommonBackend: platform=win32
12-10 03:59 DEBUG  CommonBackend: osname=nt
12-10 03:59 DEBUG  WindowsBackend: arch=amd64
12-10 03:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\data\isolist.ini
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 03:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 03:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 03:59 DEBUG  WindowsBackend: Fetching host info...
12-10 03:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 03:59 DEBUG  WindowsBackend: windows version=vista
12-10 03:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 03:59 DEBUG  WindowsBackend: windows_sp=None
12-10 03:59 DEBUG  WindowsBackend: windows_build=7601
12-10 03:59 DEBUG  WindowsBackend: gmt=-6
12-10 03:59 DEBUG  WindowsBackend: country=US
12-10 03:59 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 03:59 DEBUG  WindowsBackend: windows_username=John
12-10 03:59 DEBUG  WindowsBackend: user_full_name=John
12-10 03:59 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 03:59 DEBUG  WindowsBackend: windows_language_code=1033
12-10 03:59 DEBUG  WindowsBackend: windows_language=English
12-10 03:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 03:59 DEBUG  WindowsBackend: bootloader=vista
12-10 03:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69148.4609375 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(C: hd 69148.4609375 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(D: hd 196223.492188 mb free ntfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 03:59 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 03:59 DEBUG  WindowsBackend: uninstaller_path=None
12-10 03:59 DEBUG  WindowsBackend: previous_target_dir=None
12-10 03:59 DEBUG  WindowsBackend: previous_distro_name=None
12-10 03:59 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 03:59 DEBUG  WindowsBackend: keyboard_layout=us
12-10 03:59 DEBUG  WindowsBackend: keyboard_variant=
12-10 03:59 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 03:59 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 03:59 DEBUG  CommonBackend: Searching for local CDs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 03:59 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 03:59 INFO   root: Running the installer...
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\translations, languages=['en_US', 'en']
12-10 03:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\translations, languages=['en_US', 'en']
12-10 04:00 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:00 INFO   root: Received settings
12-10 04:00 DEBUG  CommonBackend: Searching for local CD
12-10 04:00 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl584C.tmp is a valid Ubuntu CD
12-10 04:00 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl584C.tmp\casper\filesystem.squashfs
12-10 04:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:00 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:00 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:00 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:00 DEBUG  CommonBackend: Searching for local ISO
12-10 04:00 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 04:00 DEBUG  WindowsBackend:   extracting .disk\info from D:\Downloads\Download from Web\ubuntu-10.04.3-desktop-amd64.iso
12-10 04:00 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:00 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:00 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\ubuntu-10.04.3-server-amd64.iso
12-10 04:00 DEBUG  Distro:     does not contain casper\filesystem.squashfs
12-10 04:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl584C.tmp\translations, languages=['en_US', 'en']
12-10 04:00 DEBUG  TaskList: # Running tasklist...
12-10 04:00 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:00 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:00 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:00 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:00 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:00 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:00 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:00 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:00 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:00 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:00 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:00 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:00 DEBUG  TaskList: New task download
12-10 04:00 DEBUG  TaskList: ### Running download...
12-10 04:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:00 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:05 INFO   WindowsFrontend: Operation cancelled
12-10 04:05 DEBUG  WindowsFrontend: frontend.quit
12-10 04:05 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:05 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 04:05 DEBUG  TaskList: # Cancelling tasklist
12-10 04:05 DEBUG  downloader: download finished (read 259407872 bytes)
12-10 04:05 DEBUG  TaskList: ### Finished download
12-10 04:05 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 04:05 DEBUG  root: application.on_quit
12-10 04:05 DEBUG  root: Forceful exit
12-10 04:05 INFO   root: sys.exit
12-10 04:06 INFO   root: === wubi 11.10 rev245 ===
12-10 04:06 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
12-10 04:06 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\data
12-10 04:06 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\bin\7z.exe
12-10 04:06 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:06 DEBUG  CommonBackend: Fetching basic info...
12-10 04:06 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
12-10 04:06 DEBUG  CommonBackend: platform=win32
12-10 04:06 DEBUG  CommonBackend: osname=nt
12-10 04:06 DEBUG  CommonBackend: language=en_US
12-10 04:06 DEBUG  CommonBackend: encoding=cp1252
12-10 04:06 DEBUG  WindowsBackend: arch=amd64
12-10 04:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\data\isolist.ini
12-10 04:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:06 DEBUG  WindowsBackend: Fetching host info...
12-10 04:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:06 DEBUG  WindowsBackend: windows version=vista
12-10 04:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:06 DEBUG  WindowsBackend: windows_sp=None
12-10 04:06 DEBUG  WindowsBackend: windows_build=7601
12-10 04:06 DEBUG  WindowsBackend: gmt=-6
12-10 04:06 DEBUG  WindowsBackend: country=US
12-10 04:06 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:06 DEBUG  WindowsBackend: windows_username=John
12-10 04:06 DEBUG  WindowsBackend: user_full_name=John
12-10 04:06 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:06 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:06 DEBUG  WindowsBackend: windows_language=English
12-10 04:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:06 DEBUG  WindowsBackend: bootloader=vista
12-10 04:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69576.9882813 mb free ntfs)
12-10 04:06 DEBUG  WindowsBackend: drive=Drive(C: hd 69576.9882813 mb free ntfs)
12-10 04:06 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:06 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:06 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:06 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:06 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:06 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:06 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:06 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:06 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:06 DEBUG  CommonBackend: Searching for local CDs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFDBE.tmp is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:06 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:06 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:06 INFO   root: Running the uninstaller...
12-10 04:06 INFO   CommonBackend: This is the uninstaller running
12-10 04:06 DEBUG  WindowsFrontend: __init__...
12-10 04:06 DEBUG  WindowsFrontend: on_init...
12-10 04:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\translations, languages=['en_US', 'en']
12-10 04:06 INFO   root: Received settings
12-10 04:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\translations, languages=['en_US', 'en']
12-10 04:06 DEBUG  TaskList: # Running tasklist...
12-10 04:06 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:06 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:06 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69576.9882813 mb free ntfs)
12-10 04:06 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:06 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:06 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:06 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:06 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:06 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:06 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:06 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:06 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:06 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:06 DEBUG  TaskList: # Finished tasklist
12-10 04:06 INFO   root: Almost finished uninstalling
12-10 04:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFDBE.tmp\translations, languages=['en_US', 'en']
12-10 04:06 INFO   root: Finished uninstallation
12-10 04:06 DEBUG  root: application.quit
12-10 04:06 DEBUG  WindowsFrontend: frontend.quit
12-10 04:06 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:06 DEBUG  root: application.on_quit
12-10 04:06 INFO   root: sys.exit
12-10 04:07 INFO   root: === wubi 11.10 rev245 ===
12-10 04:07 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\wubi.exe"']
12-10 04:07 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\data
12-10 04:07 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\bin\7z.exe
12-10 04:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:07 DEBUG  CommonBackend: Fetching basic info...
12-10 04:07 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\wubi.exe
12-10 04:07 DEBUG  CommonBackend: platform=win32
12-10 04:07 DEBUG  CommonBackend: osname=nt
12-10 04:07 DEBUG  CommonBackend: language=en_US
12-10 04:07 DEBUG  CommonBackend: encoding=cp1252
12-10 04:07 DEBUG  WindowsBackend: arch=amd64
12-10 04:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\data\isolist.ini
12-10 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:07 DEBUG  WindowsBackend: Fetching host info...
12-10 04:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:07 DEBUG  WindowsBackend: windows version=vista
12-10 04:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:07 DEBUG  WindowsBackend: windows_sp=None
12-10 04:07 DEBUG  WindowsBackend: windows_build=7601
12-10 04:07 DEBUG  WindowsBackend: gmt=-6
12-10 04:07 DEBUG  WindowsBackend: country=US
12-10 04:07 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:07 DEBUG  WindowsBackend: windows_username=John
12-10 04:07 DEBUG  WindowsBackend: user_full_name=John
12-10 04:07 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:07 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:07 DEBUG  WindowsBackend: windows_language=English
12-10 04:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:07 DEBUG  WindowsBackend: bootloader=vista
12-10 04:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69824.015625 mb free ntfs)
12-10 04:07 DEBUG  WindowsBackend: drive=Drive(C: hd 69824.015625 mb free ntfs)
12-10 04:07 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:07 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:07 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:07 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:07 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:07 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:07 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:07 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:07 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:07 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:07 DEBUG  CommonBackend: Searching for local CDs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:07 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 INFO   root: Running the installer...
12-10 04:07 DEBUG  WindowsFrontend: __init__...
12-10 04:07 DEBUG  WindowsFrontend: on_init...
12-10 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\translations, languages=['en_US', 'en']
12-10 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\translations, languages=['en_US', 'en']
12-10 04:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:07 INFO   root: Received settings
12-10 04:07 DEBUG  CommonBackend: Searching for local CD
12-10 04:07 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylFAC2.tmp is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:07 DEBUG  CommonBackend: Searching for local ISO
12-10 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylFAC2.tmp\translations, languages=['en_US', 'en']
12-10 04:07 DEBUG  TaskList: # Running tasklist...
12-10 04:07 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:07 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:07 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:07 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:07 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:07 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:07 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:07 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:07 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:07 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:07 DEBUG  TaskList: New task download
12-10 04:07 DEBUG  TaskList: ### Running download...
12-10 04:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:07 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:07 INFO   WindowsFrontend: Operation cancelled
12-10 04:07 DEBUG  WindowsFrontend: frontend.quit
12-10 04:07 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:07 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 04:07 DEBUG  TaskList: # Cancelling tasklist
12-10 04:07 DEBUG  downloader: download finished (read 532480 bytes)
12-10 04:07 DEBUG  TaskList: ### Finished download
12-10 04:07 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 04:07 DEBUG  root: application.on_quit
12-10 04:07 DEBUG  root: Forceful exit
12-10 04:07 INFO   root: sys.exit
12-10 04:14 INFO   root: === wubi 11.10 rev245 ===
12-10 04:14 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 04:14 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\data
12-10 04:14 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\bin\7z.exe
12-10 04:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:14 DEBUG  CommonBackend: Fetching basic info...
12-10 04:14 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:14 DEBUG  CommonBackend: platform=win32
12-10 04:14 DEBUG  CommonBackend: osname=nt
12-10 04:14 DEBUG  CommonBackend: language=en_US
12-10 04:14 DEBUG  CommonBackend: encoding=cp1252
12-10 04:14 DEBUG  WindowsBackend: arch=amd64
12-10 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\data\isolist.ini
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:14 DEBUG  WindowsBackend: Fetching host info...
12-10 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:14 DEBUG  WindowsBackend: windows version=vista
12-10 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:14 DEBUG  WindowsBackend: windows_sp=None
12-10 04:14 DEBUG  WindowsBackend: windows_build=7601
12-10 04:14 DEBUG  WindowsBackend: gmt=-6
12-10 04:14 DEBUG  WindowsBackend: country=US
12-10 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:14 DEBUG  WindowsBackend: windows_username=John
12-10 04:14 DEBUG  WindowsBackend: user_full_name=John
12-10 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:14 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:14 DEBUG  WindowsBackend: windows_language=English
12-10 04:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:14 DEBUG  WindowsBackend: bootloader=vista
12-10 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69125.5195313 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 69125.5195313 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:14 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:14 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:14 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:14 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:14 DEBUG  CommonBackend: Searching for local CDs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 INFO   root: Already installed, running the uninstaller...
12-10 04:14 INFO   root: Running the uninstaller...
12-10 04:14 INFO   CommonBackend: This is the uninstaller running
12-10 04:14 DEBUG  WindowsFrontend: __init__...
12-10 04:14 DEBUG  WindowsFrontend: on_init...
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 INFO   root: Received settings
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  TaskList: # Running tasklist...
12-10 04:14 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:14 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:14 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69125.5195313 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:14 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:14 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:14 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:14 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:14 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:14 DEBUG  TaskList: # Finished tasklist
12-10 04:14 INFO   root: Almost finished uninstalling
12-10 04:14 INFO   root: Finished uninstallation
12-10 04:14 DEBUG  CommonBackend: Fetching basic info...
12-10 04:14 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:14 DEBUG  CommonBackend: platform=win32
12-10 04:14 DEBUG  CommonBackend: osname=nt
12-10 04:14 DEBUG  WindowsBackend: arch=amd64
12-10 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\data\isolist.ini
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:14 DEBUG  WindowsBackend: Fetching host info...
12-10 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:14 DEBUG  WindowsBackend: windows version=vista
12-10 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:14 DEBUG  WindowsBackend: windows_sp=None
12-10 04:14 DEBUG  WindowsBackend: windows_build=7601
12-10 04:14 DEBUG  WindowsBackend: gmt=-6
12-10 04:14 DEBUG  WindowsBackend: country=US
12-10 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:14 DEBUG  WindowsBackend: windows_username=John
12-10 04:14 DEBUG  WindowsBackend: user_full_name=John
12-10 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:14 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:14 DEBUG  WindowsBackend: windows_language=English
12-10 04:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:14 DEBUG  WindowsBackend: bootloader=vista
12-10 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69128.390625 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 69128.390625 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:14 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:14 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:14 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:14 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:14 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:14 DEBUG  CommonBackend: Searching for local CDs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 INFO   root: Running the installer...
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:14 INFO   root: Received settings
12-10 04:14 DEBUG  CommonBackend: Searching for local CD
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  CommonBackend: Searching for local ISO
12-10 04:14 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:14 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
12-10 04:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  TaskList: # Running tasklist...
12-10 04:14 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:14 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:14 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:14 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:14 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:14 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:14 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:14 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:14 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:14 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:14 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:14 DEBUG  TaskList: New task download
12-10 04:14 DEBUG  TaskList: ### Running download...
12-10 04:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:14 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-10 04:14 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-10 04:14 DEBUG  TaskList: ### Finished download
12-10 04:14 DEBUG  TaskList: ## Finished get_diskimage
12-10 04:14 DEBUG  TaskList: ## Running extract_diskimage...
12-10 04:14 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 04:14 DEBUG  TaskList: # Cancelling tasklist
12-10 04:14 DEBUG  TaskList: # Finished tasklist
12-10 04:14 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 04:14 INFO   root: === wubi 11.10 rev245 ===
12-10 04:14 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 04:14 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\data
12-10 04:14 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\bin\7z.exe
12-10 04:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:14 DEBUG  CommonBackend: Fetching basic info...
12-10 04:14 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:14 DEBUG  CommonBackend: platform=win32
12-10 04:14 DEBUG  CommonBackend: osname=nt
12-10 04:14 DEBUG  CommonBackend: language=en_US
12-10 04:14 DEBUG  CommonBackend: encoding=cp1252
12-10 04:14 DEBUG  WindowsBackend: arch=amd64
12-10 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\data\isolist.ini
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:14 DEBUG  WindowsBackend: Fetching host info...
12-10 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:14 DEBUG  WindowsBackend: windows version=vista
12-10 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:14 DEBUG  WindowsBackend: windows_sp=None
12-10 04:14 DEBUG  WindowsBackend: windows_build=7601
12-10 04:14 DEBUG  WindowsBackend: gmt=-6
12-10 04:14 DEBUG  WindowsBackend: country=US
12-10 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:14 DEBUG  WindowsBackend: windows_username=John
12-10 04:14 DEBUG  WindowsBackend: user_full_name=John
12-10 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:14 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:14 DEBUG  WindowsBackend: windows_language=English
12-10 04:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:14 DEBUG  WindowsBackend: bootloader=vista
12-10 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69126.0117188 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 69126.0117188 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:14 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:14 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:14 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:14 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:14 DEBUG  CommonBackend: Searching for local CDs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 INFO   root: Already installed, running the uninstaller...
12-10 04:14 INFO   root: Running the uninstaller...
12-10 04:14 INFO   CommonBackend: This is the uninstaller running
12-10 04:14 DEBUG  WindowsFrontend: __init__...
12-10 04:14 DEBUG  WindowsFrontend: on_init...
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 INFO   root: Received settings
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  TaskList: # Running tasklist...
12-10 04:14 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:14 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:14 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69126.0117188 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:14 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:14 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:14 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:14 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:14 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:14 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:14 DEBUG  TaskList: # Finished tasklist
12-10 04:14 INFO   root: Almost finished uninstalling
12-10 04:14 INFO   root: Finished uninstallation
12-10 04:14 DEBUG  CommonBackend: Fetching basic info...
12-10 04:14 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:14 DEBUG  CommonBackend: platform=win32
12-10 04:14 DEBUG  CommonBackend: osname=nt
12-10 04:14 DEBUG  WindowsBackend: arch=amd64
12-10 04:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\data\isolist.ini
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:14 DEBUG  WindowsBackend: Fetching host info...
12-10 04:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:14 DEBUG  WindowsBackend: windows version=vista
12-10 04:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:14 DEBUG  WindowsBackend: windows_sp=None
12-10 04:14 DEBUG  WindowsBackend: windows_build=7601
12-10 04:14 DEBUG  WindowsBackend: gmt=-6
12-10 04:14 DEBUG  WindowsBackend: country=US
12-10 04:14 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:14 DEBUG  WindowsBackend: windows_username=John
12-10 04:14 DEBUG  WindowsBackend: user_full_name=John
12-10 04:14 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:14 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:14 DEBUG  WindowsBackend: windows_language=English
12-10 04:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:14 DEBUG  WindowsBackend: bootloader=vista
12-10 04:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69128.3828125 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(C: hd 69128.3828125 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:14 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:14 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:14 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:14 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:14 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:14 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:14 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:14 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:14 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:14 DEBUG  CommonBackend: Searching for local CDs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 INFO   root: Running the installer...
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:14 INFO   root: Received settings
12-10 04:14 DEBUG  CommonBackend: Searching for local CD
12-10 04:14 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE88A.tmp is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE88A.tmp\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:14 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:14 DEBUG  CommonBackend: Searching for local ISO
12-10 04:14 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:14 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:14 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
12-10 04:14 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
12-10 04:14 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE88A.tmp\translations, languages=['en_US', 'en']
12-10 04:14 DEBUG  TaskList: # Running tasklist...
12-10 04:14 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:14 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:14 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:14 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:14 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:14 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:14 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:14 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:14 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:14 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:14 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:14 DEBUG  TaskList: New task download
12-10 04:14 DEBUG  TaskList: ### Running download...
12-10 04:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:14 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
12-10 04:14 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
12-10 04:14 DEBUG  TaskList: ### Finished download
12-10 04:14 DEBUG  TaskList: ## Finished get_diskimage
12-10 04:14 DEBUG  TaskList: ## Running extract_diskimage...
12-10 04:14 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 04:14 DEBUG  TaskList: # Cancelling tasklist
12-10 04:14 DEBUG  TaskList: # Finished tasklist
12-10 04:14 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
12-10 04:15 INFO   root: === wubi 11.10 rev245 ===
12-10 04:15 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\Desktop\\New folder\\wubi.exe"']
12-10 04:15 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\data
12-10 04:15 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\bin\7z.exe
12-10 04:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:15 DEBUG  CommonBackend: Fetching basic info...
12-10 04:15 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:15 DEBUG  CommonBackend: platform=win32
12-10 04:15 DEBUG  CommonBackend: osname=nt
12-10 04:15 DEBUG  CommonBackend: language=en_US
12-10 04:15 DEBUG  CommonBackend: encoding=cp1252
12-10 04:15 DEBUG  WindowsBackend: arch=amd64
12-10 04:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\data\isolist.ini
12-10 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:15 DEBUG  WindowsBackend: Fetching host info...
12-10 04:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:15 DEBUG  WindowsBackend: windows version=vista
12-10 04:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:15 DEBUG  WindowsBackend: windows_sp=None
12-10 04:15 DEBUG  WindowsBackend: windows_build=7601
12-10 04:15 DEBUG  WindowsBackend: gmt=-6
12-10 04:15 DEBUG  WindowsBackend: country=US
12-10 04:15 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:15 DEBUG  WindowsBackend: windows_username=John
12-10 04:15 DEBUG  WindowsBackend: user_full_name=John
12-10 04:15 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:15 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:15 DEBUG  WindowsBackend: windows_language=English
12-10 04:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:15 DEBUG  WindowsBackend: bootloader=vista
12-10 04:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69125.3632813 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(C: hd 69125.3632813 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:15 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:15 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:15 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:15 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:15 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:15 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:15 DEBUG  CommonBackend: Searching for local CDs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 INFO   root: Already installed, running the uninstaller...
12-10 04:15 INFO   root: Running the uninstaller...
12-10 04:15 INFO   CommonBackend: This is the uninstaller running
12-10 04:15 DEBUG  WindowsFrontend: __init__...
12-10 04:15 DEBUG  WindowsFrontend: on_init...
12-10 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\translations, languages=['en_US', 'en']
12-10 04:15 INFO   root: Received settings
12-10 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\translations, languages=['en_US', 'en']
12-10 04:15 DEBUG  TaskList: # Running tasklist...
12-10 04:15 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:15 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:15 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69125.3632813 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:15 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:15 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:15 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:15 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:15 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:15 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:15 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:15 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:15 DEBUG  TaskList: # Finished tasklist
12-10 04:15 INFO   root: Almost finished uninstalling
12-10 04:15 INFO   root: Finished uninstallation
12-10 04:15 DEBUG  CommonBackend: Fetching basic info...
12-10 04:15 DEBUG  CommonBackend: original_exe=C:\Users\John\Desktop\New folder\wubi.exe
12-10 04:15 DEBUG  CommonBackend: platform=win32
12-10 04:15 DEBUG  CommonBackend: osname=nt
12-10 04:15 DEBUG  WindowsBackend: arch=amd64
12-10 04:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\data\isolist.ini
12-10 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:15 DEBUG  WindowsBackend: Fetching host info...
12-10 04:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:15 DEBUG  WindowsBackend: windows version=vista
12-10 04:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:15 DEBUG  WindowsBackend: windows_sp=None
12-10 04:15 DEBUG  WindowsBackend: windows_build=7601
12-10 04:15 DEBUG  WindowsBackend: gmt=-6
12-10 04:15 DEBUG  WindowsBackend: country=US
12-10 04:15 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:15 DEBUG  WindowsBackend: windows_username=John
12-10 04:15 DEBUG  WindowsBackend: user_full_name=John
12-10 04:15 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:15 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:15 DEBUG  WindowsBackend: windows_language=English
12-10 04:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:15 DEBUG  WindowsBackend: bootloader=vista
12-10 04:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69127.7265625 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(C: hd 69127.7265625 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:15 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:15 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:15 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:15 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:15 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:15 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:15 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:15 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:15 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:15 DEBUG  CommonBackend: Searching for local CDs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 INFO   root: Running the installer...
12-10 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\translations, languages=['en_US', 'en']
12-10 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\translations, languages=['en_US', 'en']
12-10 04:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:15 INFO   root: Received settings
12-10 04:15 DEBUG  CommonBackend: Searching for local CD
12-10 04:15 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylE4D2.tmp is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:15 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:15 DEBUG  CommonBackend: Searching for local ISO
12-10 04:15 DEBUG  Distro:   checking Ubuntu ISO C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:15 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\John\Desktop\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
12-10 04:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
12-10 04:15 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylE4D2.tmp\translations, languages=['en_US', 'en']
12-10 04:15 DEBUG  TaskList: # Running tasklist...
12-10 04:15 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:15 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:15 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:15 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:15 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:15 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\Desktop\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:15 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:15 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:15 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:15 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:15 DEBUG  TaskList: New task download
12-10 04:15 DEBUG  TaskList: ### Running download...
12-10 04:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:15 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:16 INFO   WindowsFrontend: Operation cancelled
12-10 04:16 DEBUG  WindowsFrontend: frontend.quit
12-10 04:16 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:16 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 04:16 DEBUG  TaskList: # Cancelling tasklist
12-10 04:16 DEBUG  downloader: download finished (read 13623296 bytes)
12-10 04:16 DEBUG  TaskList: ### Finished download
12-10 04:16 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 04:16 DEBUG  root: application.on_quit
12-10 04:16 DEBUG  root: Forceful exit
12-10 04:16 INFO   root: sys.exit
12-10 04:16 INFO   root: === wubi 11.10 rev245 ===
12-10 04:16 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\6F0017FX\\wubi.exe"']
12-10 04:16 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\data
12-10 04:16 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\bin\7z.exe
12-10 04:16 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:16 DEBUG  CommonBackend: Fetching basic info...
12-10 04:16 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\6F0017FX\wubi.exe
12-10 04:16 DEBUG  CommonBackend: platform=win32
12-10 04:16 DEBUG  CommonBackend: osname=nt
12-10 04:16 DEBUG  CommonBackend: language=en_US
12-10 04:16 DEBUG  CommonBackend: encoding=cp1252
12-10 04:16 DEBUG  WindowsBackend: arch=amd64
12-10 04:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\data\isolist.ini
12-10 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:16 DEBUG  WindowsBackend: Fetching host info...
12-10 04:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:16 DEBUG  WindowsBackend: windows version=vista
12-10 04:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:16 DEBUG  WindowsBackend: windows_sp=None
12-10 04:16 DEBUG  WindowsBackend: windows_build=7601
12-10 04:16 DEBUG  WindowsBackend: gmt=-6
12-10 04:16 DEBUG  WindowsBackend: country=US
12-10 04:16 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:16 DEBUG  WindowsBackend: windows_username=John
12-10 04:16 DEBUG  WindowsBackend: user_full_name=John
12-10 04:16 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:16 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:16 DEBUG  WindowsBackend: windows_language=English
12-10 04:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:16 DEBUG  WindowsBackend: bootloader=vista
12-10 04:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69109.765625 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(C: hd 69109.765625 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:16 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:16 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:16 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:16 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:16 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:16 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:16 DEBUG  CommonBackend: Searching for local CDs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:16 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 INFO   root: Already installed, running the uninstaller...
12-10 04:16 INFO   root: Running the uninstaller...
12-10 04:16 INFO   CommonBackend: This is the uninstaller running
12-10 04:16 DEBUG  WindowsFrontend: __init__...
12-10 04:16 DEBUG  WindowsFrontend: on_init...
12-10 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\translations, languages=['en_US', 'en']
12-10 04:16 INFO   root: Received settings
12-10 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\translations, languages=['en_US', 'en']
12-10 04:16 DEBUG  TaskList: # Running tasklist...
12-10 04:16 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:16 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:16 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69109.765625 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:16 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:16 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:16 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:16 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:16 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:16 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:16 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:16 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:16 DEBUG  TaskList: # Finished tasklist
12-10 04:16 INFO   root: Almost finished uninstalling
12-10 04:16 INFO   root: Finished uninstallation
12-10 04:16 DEBUG  CommonBackend: Fetching basic info...
12-10 04:16 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\6F0017FX\wubi.exe
12-10 04:16 DEBUG  CommonBackend: platform=win32
12-10 04:16 DEBUG  CommonBackend: osname=nt
12-10 04:16 DEBUG  WindowsBackend: arch=amd64
12-10 04:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\data\isolist.ini
12-10 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:16 DEBUG  WindowsBackend: Fetching host info...
12-10 04:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:16 DEBUG  WindowsBackend: windows version=vista
12-10 04:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:16 DEBUG  WindowsBackend: windows_sp=None
12-10 04:16 DEBUG  WindowsBackend: windows_build=7601
12-10 04:16 DEBUG  WindowsBackend: gmt=-6
12-10 04:16 DEBUG  WindowsBackend: country=US
12-10 04:16 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:16 DEBUG  WindowsBackend: windows_username=John
12-10 04:16 DEBUG  WindowsBackend: user_full_name=John
12-10 04:16 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:16 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:16 DEBUG  WindowsBackend: windows_language=English
12-10 04:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:16 DEBUG  WindowsBackend: bootloader=vista
12-10 04:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69125.1132813 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(C: hd 69125.1132813 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:16 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:16 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:16 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:16 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:16 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:16 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:16 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:16 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:16 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:16 DEBUG  CommonBackend: Searching for local CDs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 INFO   root: Running the installer...
12-10 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\translations, languages=['en_US', 'en']
12-10 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\translations, languages=['en_US', 'en']
12-10 04:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:16 INFO   root: Received settings
12-10 04:16 DEBUG  CommonBackend: Searching for local CD
12-10 04:16 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylACF1.tmp is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylACF1.tmp\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:16 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:16 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:16 DEBUG  CommonBackend: Searching for local ISO
12-10 04:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylACF1.tmp\translations, languages=['en_US', 'en']
12-10 04:16 DEBUG  TaskList: # Running tasklist...
12-10 04:16 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:16 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:16 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:16 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:16 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:16 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\6F0017FX\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:16 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:16 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:16 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:16 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:16 DEBUG  TaskList: New task download
12-10 04:16 DEBUG  TaskList: ### Running download...
12-10 04:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:16 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:16 INFO   WindowsFrontend: Operation cancelled
12-10 04:16 DEBUG  WindowsFrontend: frontend.quit
12-10 04:16 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:16 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 04:16 DEBUG  TaskList: # Cancelling tasklist
12-10 04:16 DEBUG  downloader: download finished (read 1925120 bytes)
12-10 04:16 DEBUG  TaskList: ### Finished download
12-10 04:16 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 04:16 DEBUG  root: application.on_quit
12-10 04:16 DEBUG  root: Forceful exit
12-10 04:16 INFO   root: sys.exit
12-10 04:18 INFO   root: === wubi 11.10 rev245 ===
12-10 04:18 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\John\\AppData\\Local\\Microsoft\\Windows\\Temporary Internet Files\\Content.IE5\\HPE4RTLF\\wubi.exe"']
12-10 04:18 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\data
12-10 04:18 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\bin\7z.exe
12-10 04:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:18 DEBUG  CommonBackend: Fetching basic info...
12-10 04:18 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\HPE4RTLF\wubi.exe
12-10 04:18 DEBUG  CommonBackend: platform=win32
12-10 04:18 DEBUG  CommonBackend: osname=nt
12-10 04:18 DEBUG  CommonBackend: language=en_US
12-10 04:18 DEBUG  CommonBackend: encoding=cp1252
12-10 04:18 DEBUG  WindowsBackend: arch=amd64
12-10 04:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\data\isolist.ini
12-10 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:18 DEBUG  WindowsBackend: Fetching host info...
12-10 04:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:18 DEBUG  WindowsBackend: windows version=vista
12-10 04:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:18 DEBUG  WindowsBackend: windows_sp=None
12-10 04:18 DEBUG  WindowsBackend: windows_build=7601
12-10 04:18 DEBUG  WindowsBackend: gmt=-6
12-10 04:18 DEBUG  WindowsBackend: country=US
12-10 04:18 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:18 DEBUG  WindowsBackend: windows_username=John
12-10 04:18 DEBUG  WindowsBackend: user_full_name=John
12-10 04:18 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:18 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:18 DEBUG  WindowsBackend: windows_language=English
12-10 04:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:18 DEBUG  WindowsBackend: bootloader=vista
12-10 04:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69118.5664063 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(C: hd 69118.5664063 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:18 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:18 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:18 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:18 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:18 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:18 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:18 DEBUG  CommonBackend: Searching for local CDs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:18 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:18 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 INFO   root: Already installed, running the uninstaller...
12-10 04:18 INFO   root: Running the uninstaller...
12-10 04:18 INFO   CommonBackend: This is the uninstaller running
12-10 04:18 DEBUG  WindowsFrontend: __init__...
12-10 04:18 DEBUG  WindowsFrontend: on_init...
12-10 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\translations, languages=['en_US', 'en']
12-10 04:18 INFO   root: Received settings
12-10 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\translations, languages=['en_US', 'en']
12-10 04:18 DEBUG  TaskList: # Running tasklist...
12-10 04:18 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:18 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:18 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69118.5664063 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:18 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:18 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:18 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:18 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:18 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:18 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:18 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:18 DEBUG  TaskList: # Finished tasklist
12-10 04:18 INFO   root: Almost finished uninstalling
12-10 04:18 INFO   root: Finished uninstallation
12-10 04:18 DEBUG  CommonBackend: Fetching basic info...
12-10 04:18 DEBUG  CommonBackend: original_exe=C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\HPE4RTLF\wubi.exe
12-10 04:18 DEBUG  CommonBackend: platform=win32
12-10 04:18 DEBUG  CommonBackend: osname=nt
12-10 04:18 DEBUG  WindowsBackend: arch=amd64
12-10 04:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\data\isolist.ini
12-10 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:18 DEBUG  WindowsBackend: Fetching host info...
12-10 04:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:18 DEBUG  WindowsBackend: windows version=vista
12-10 04:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:18 DEBUG  WindowsBackend: windows_sp=None
12-10 04:18 DEBUG  WindowsBackend: windows_build=7601
12-10 04:18 DEBUG  WindowsBackend: gmt=-6
12-10 04:18 DEBUG  WindowsBackend: country=US
12-10 04:18 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:18 DEBUG  WindowsBackend: windows_username=John
12-10 04:18 DEBUG  WindowsBackend: user_full_name=John
12-10 04:18 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:18 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:18 DEBUG  WindowsBackend: windows_language=English
12-10 04:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:18 DEBUG  WindowsBackend: bootloader=vista
12-10 04:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69122.7578125 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(C: hd 69122.7578125 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(D: hd 195535.769531 mb free ntfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:18 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:18 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:18 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:18 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:18 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:18 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:18 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:18 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:18 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:18 DEBUG  CommonBackend: Searching for local CDs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 INFO   root: Running the installer...
12-10 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\translations, languages=['en_US', 'en']
12-10 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\translations, languages=['en_US', 'en']
12-10 04:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:18 INFO   root: Received settings
12-10 04:18 DEBUG  CommonBackend: Searching for local CD
12-10 04:18 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pyl8036.tmp is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pyl8036.tmp\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:18 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:18 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:18 DEBUG  CommonBackend: Searching for local ISO
12-10 04:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pyl8036.tmp\translations, languages=['en_US', 'en']
12-10 04:18 DEBUG  TaskList: # Running tasklist...
12-10 04:18 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:18 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:18 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:18 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:18 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:18 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\John\AppData\Local\Microsoft\Windows\Temporary Internet Files\Content.IE5\HPE4RTLF\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:18 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:18 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:18 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:18 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:18 DEBUG  TaskList: New task download
12-10 04:18 DEBUG  TaskList: ### Running download...
12-10 04:18 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:18 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:19 INFO   WindowsFrontend: Operation cancelled
12-10 04:19 DEBUG  WindowsFrontend: frontend.quit
12-10 04:19 DEBUG  WindowsFrontend: frontend.on_quit
12-10 04:19 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
12-10 04:19 DEBUG  TaskList: # Cancelling tasklist
12-10 04:19 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
12-10 04:19 DEBUG  root: application.on_quit
12-10 04:19 DEBUG  root: Forceful exit
12-10 04:19 INFO   root: sys.exit
12-10 04:27 INFO   root: === wubi 11.10 rev245 ===
12-10 04:27 DEBUG  root: Logfile is c:\users\john\appdata\local\temp\wubi-11.10-rev245.log
12-10 04:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Downloads\\Download from Web\\New folder\\wubi.exe"']
12-10 04:27 DEBUG  CommonBackend: data_dir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\data
12-10 04:27 DEBUG  WindowsBackend: 7z=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\bin\7z.exe
12-10 04:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
12-10 04:27 DEBUG  CommonBackend: Fetching basic info...
12-10 04:27 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\New folder\wubi.exe
12-10 04:27 DEBUG  CommonBackend: platform=win32
12-10 04:27 DEBUG  CommonBackend: osname=nt
12-10 04:27 DEBUG  CommonBackend: language=en_US
12-10 04:27 DEBUG  CommonBackend: encoding=cp1252
12-10 04:27 DEBUG  WindowsBackend: arch=amd64
12-10 04:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\data\isolist.ini
12-10 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:27 DEBUG  WindowsBackend: Fetching host info...
12-10 04:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:27 DEBUG  WindowsBackend: windows version=vista
12-10 04:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:27 DEBUG  WindowsBackend: windows_sp=None
12-10 04:27 DEBUG  WindowsBackend: windows_build=7601
12-10 04:27 DEBUG  WindowsBackend: gmt=-6
12-10 04:27 DEBUG  WindowsBackend: country=US
12-10 04:27 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:27 DEBUG  WindowsBackend: windows_username=John
12-10 04:27 DEBUG  WindowsBackend: user_full_name=John
12-10 04:27 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:27 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:27 DEBUG  WindowsBackend: windows_language=English
12-10 04:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:27 DEBUG  WindowsBackend: bootloader=vista
12-10 04:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69103.9765625 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(C: hd 69103.9765625 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(D: hd 194848.046875 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-10 04:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-10 04:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-10 04:27 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:27 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:27 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-10 04:27 DEBUG  CommonBackend: locale=en_US.UTF-8
12-10 04:27 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:27 DEBUG  CommonBackend: Searching for local CDs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release amd64 (20110720.1)
12-10 04:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 INFO   root: Already installed, running the uninstaller...
12-10 04:27 INFO   root: Running the uninstaller...
12-10 04:27 INFO   CommonBackend: This is the uninstaller running
12-10 04:27 DEBUG  WindowsFrontend: __init__...
12-10 04:27 DEBUG  WindowsFrontend: on_init...
12-10 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\translations, languages=['en_US', 'en']
12-10 04:27 INFO   root: Received settings
12-10 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\translations, languages=['en_US', 'en']
12-10 04:27 DEBUG  TaskList: # Running tasklist...
12-10 04:27 DEBUG  TaskList: ## Running Remove bootloader entry...
12-10 04:27 DEBUG  WindowsBackend: Could not find bcd id
12-10 04:27 DEBUG  WindowsBackend: undo_bootini C:
12-10 04:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 69103.9765625 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: undo_bootini D:
12-10 04:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 194848.046875 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: undo_bootini Q:
12-10 04:27 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
12-10 04:27 DEBUG  TaskList: ## Finished Remove bootloader entry
12-10 04:27 DEBUG  TaskList: ## Running Remove target dir...
12-10 04:27 DEBUG  CommonBackend: Deleting C:\ubuntu
12-10 04:27 DEBUG  TaskList: ## Finished Remove target dir
12-10 04:27 DEBUG  TaskList: ## Running Remove registry key...
12-10 04:27 DEBUG  TaskList: ## Finished Remove registry key
12-10 04:27 DEBUG  TaskList: # Finished tasklist
12-10 04:27 INFO   root: Almost finished uninstalling
12-10 04:27 INFO   root: Finished uninstallation
12-10 04:27 DEBUG  CommonBackend: Fetching basic info...
12-10 04:27 DEBUG  CommonBackend: original_exe=D:\Downloads\Download from Web\New folder\wubi.exe
12-10 04:27 DEBUG  CommonBackend: platform=win32
12-10 04:27 DEBUG  CommonBackend: osname=nt
12-10 04:27 DEBUG  WindowsBackend: arch=amd64
12-10 04:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\data\isolist.ini
12-10 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-10 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-10 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-10 04:27 DEBUG  WindowsBackend: Fetching host info...
12-10 04:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-10 04:27 DEBUG  WindowsBackend: windows version=vista
12-10 04:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-10 04:27 DEBUG  WindowsBackend: windows_sp=None
12-10 04:27 DEBUG  WindowsBackend: windows_build=7601
12-10 04:27 DEBUG  WindowsBackend: gmt=-6
12-10 04:27 DEBUG  WindowsBackend: country=US
12-10 04:27 DEBUG  WindowsBackend: timezone=America/Chicago
12-10 04:27 DEBUG  WindowsBackend: windows_username=John
12-10 04:27 DEBUG  WindowsBackend: user_full_name=John
12-10 04:27 DEBUG  WindowsBackend: user_directory=C:\Users\John
12-10 04:27 DEBUG  WindowsBackend: windows_language_code=1033
12-10 04:27 DEBUG  WindowsBackend: windows_language=English
12-10 04:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
12-10 04:27 DEBUG  WindowsBackend: bootloader=vista
12-10 04:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 69121.4804688 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(C: hd 69121.4804688 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(D: hd 194848.046875 mb free ntfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
12-10 04:27 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
12-10 04:27 DEBUG  WindowsBackend: uninstaller_path=None
12-10 04:27 DEBUG  WindowsBackend: previous_target_dir=None
12-10 04:27 DEBUG  WindowsBackend: previous_distro_name=None
12-10 04:27 DEBUG  WindowsBackend: keyboard_id=67699721
12-10 04:27 DEBUG  WindowsBackend: keyboard_layout=us
12-10 04:27 DEBUG  WindowsBackend: keyboard_variant=
12-10 04:27 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
12-10 04:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-10 04:27 DEBUG  CommonBackend: Searching for local CDs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 INFO   root: Running the installer...
12-10 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\translations, languages=['en_US', 'en']
12-10 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\translations, languages=['en_US', 'en']
12-10 04:27 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-10 04:27 INFO   root: Received settings
12-10 04:27 DEBUG  CommonBackend: Searching for local CD
12-10 04:27 DEBUG  Distro:   checking whether C:\Users\John\AppData\Local\Temp\pylCE08.tmp is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain C:\Users\John\AppData\Local\Temp\pylCE08.tmp\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-10 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
12-10 04:27 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
12-10 04:27 DEBUG  CommonBackend: Searching for local ISO
12-10 04:27 DEBUG  Distro:   checking Ubuntu ISO D:\Downloads\Download from Web\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:27 DEBUG  WindowsBackend:   extracting .disk\info from D:\Downloads\Download from Web\New folder\ubuntu-10.04.3-desktop-i386.iso
12-10 04:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.3 LTS "Lucid Lynx" - Release i386 (20110720.1)
12-10 04:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.3', 'build': '20110720.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
12-10 04:27 DEBUG  Distro: wrong version: 10.04.3 != 11.10
12-10 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\John\AppData\Local\Temp\pylCE08.tmp\translations, languages=['en_US', 'en']
12-10 04:27 DEBUG  TaskList: # Running tasklist...
12-10 04:27 DEBUG  TaskList: ## Running select_target_dir...
12-10 04:27 INFO   WindowsBackend: Installing into C:\ubuntu
12-10 04:27 DEBUG  TaskList: ## Finished select_target_dir
12-10 04:27 DEBUG  TaskList: ## Running create_dir_structure...
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-10 04:27 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-10 04:27 DEBUG  TaskList: ## Finished create_dir_structure
12-10 04:27 DEBUG  TaskList: ## Running create_uninstaller...
12-10 04:27 DEBUG  WindowsBackend: Copying uninstaller D:\Downloads\Download from Web\New folder\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-10 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-10 04:27 DEBUG  TaskList: ## Finished create_uninstaller
12-10 04:27 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-10 04:27 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-10 04:27 DEBUG  TaskList: ## Running get_diskimage...
12-10 04:27 DEBUG  TaskList: New task download
12-10 04:27 DEBUG  TaskList: ### Running download...
12-10 04:27 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-10 04:27 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-10 04:34 DEBUG  TaskList: ### Finished download
12-10 04:34 DEBUG  downloader: download finished (read 507143012 bytes)
12-10 04:34 DEBUG  TaskList: ## Finished get_diskimage
12-10 04:34 DEBUG  TaskList: ## Running extract_diskimage...
12-10 04:35 DEBUG  TaskList: ## Finished extract_diskimage
12-10 04:35 DEBUG  TaskList: ## Running choose_disk_sizes...
12-10 04:35 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-10 04:35 DEBUG  TaskList: ## Finished choose_disk_sizes
12-10 04:35 DEBUG  TaskList: ## Running expand_diskimage...
12-10 04:37 DEBUG  TaskList: ## Finished expand_diskimage
12-10 04:37 DEBUG  TaskList: ## Running create_swap_diskimage...
12-10 04:37 DEBUG  TaskList: ## Finished create_swap_diskimage
12-10 04:37 DEBUG  TaskList: ## Running modify_bootloader...
12-10 04:37 DEBUG  TaskList: New task modify_bcd
12-10 04:37 DEBUG  TaskList: ### Running modify_bcd...
12-10 04:37 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 69121.4804688 mb free ntfs)
12-10 04:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {8cb2d9b9-7c05-11de-842e-b4611d44fefa}
12-10 04:37 DEBUG  TaskList: ### Finished modify_bcd
12-10 04:37 DEBUG  TaskList: New task modify_bcd
12-10 04:37 DEBUG  TaskList: ### Running modify_bcd...
12-10 04:37 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 194848.046875 mb free ntfs)
12-10 04:37 DEBUG  WindowsBackend: BCD has already been modified
12-10 04:37 DEBUG  TaskList: ### Finished modify_bcd
12-10 04:37 DEBUG  TaskList: New task modify_bcd
12-10 04:37 DEBUG  TaskList: ### Running modify_bcd...
12-10 04:37 DEBUG  WindowsBackend: modify_bcd Drive(Q: hd 0.0 mb free )
12-10 04:37 DEBUG  WindowsBackend: BCD has already been modified
12-10 04:37 DEBUG  TaskList: ### Finished modify_bcd
12-10 04:37 DEBUG  TaskList: ## Finished modify_bootloader
12-10 04:37 DEBUG  TaskList: ## Running diskimage_bootloader...
12-10 04:37 DEBUG  WindowsBackend: Copying C:\Users\John\AppData\Local\Temp\pylCE08.tmp\winboot -> C:\ubuntu\winboot
12-10 04:37 ERROR  TaskList: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'
12-10 04:37 DEBUG  TaskList: # Cancelling tasklist
12-10 04:37 DEBUG  TaskList: # Finished tasklist
12-10 04:37 ERROR  root: [Errno 13] Permission denied: 'Q:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 13] Permission denied: 'Q:\\wubildr'

```
 
Thanks in advance! :)
 
JTL

---

### Post by darkod on 2011-12-10
I don't use wubi, and not sure how it works with win7 but have you tried when running it not to do it with double click. Instead right click and Run As Administrator?

Win7 might have limitations that doesn't allow wubi to create all the needed files unless run as administrator.

On another note, if you want to see the best performance using the SSD you should consider a proper dual boot. Wubi is like a virtual machine inside windows, that will affect the performance a bit. Also future updates (not only upgrades to next version) might mess with the wubi installation and temporarily break it.

Especially if you are decided to use ubuntu long term, I would forget about wubi.

---

### Post by johntland on 2011-12-10
I was able to get it to work. I wanted to install ubuntu 10 rather then 11. I found a wubi 10 and it went installed. I am not sure I am too okay with the way it installed. I am really, REALLY new to linux. So I am not sure how all this works. I know I have a pretty powerful machine and would like to have the option to run win 7 and Ubuntu on it. Just not sure which is the best route...

---

### Post by darkod on 2011-12-10
Yeah, the version of the ISO and the wubi.exe has to be the same. In fact, the wubi.exe is inside the ISO too so you just need any program that can "open" an ISO and extract a single file from it. The easiest free way I have found is to use 7-zip. I use it fro zip/rar too, and it can open ISO images. This is for windows.

In ubuntu the Archive Manager can open ISO and extract files.

The "best" route depends on whom you ask. :) Personally, for me, what ever OS we are talking about, I am always in favor of running it from its own partition, not from inside another one.

But wubi is good to start with. The next Long Term Supported release (LTS) is due April 2012, version 12.04 so you can get to know your new ubuntu/wubi and come April install the 12.04 as proper dual boot.

---

### Post by johntland on 2011-12-10
Well, I have installed it using a CD. Version 11. However, when I tried to just do the "install side by side with windows" it wanted to install it on my sata drive instead of my ssd drive. So, I did the "other" option (and not knowing really what I was doing). Now back in windows, I see that my OS "HD" partition is only 44GB and the Ubuntu partition is like 60GB and an 8GB partition I am not sure is what it's used for. I am thinking I might uninstall ubuntu, leave the ssd one in and try the install again and see if it figures it all out. If I do have to chose the size of the ubuntu partition, what size would you suggest?

---

### Post by darkod on 2011-12-10
The partition sizes depend on your use. However, few of my opinions:
1. The swap partition size. During auto install, the installer selects the swap size depending on your memory and available hdd space. It's much better to set it yourself by using Manual partitioning. If you use hibernate regularly the rule is about 1.5 x RAM but with you having 8GB of memory that would eat up 12GB of your SSD which is a waste. On top of that, with 8GB memory the swap will rarely get used. If you don't plan to hibernate you're good with 1GB or 2GB swap.
2. The main, root partition. The minimum you would need is 5-6GB but you should have at least 10GB. Take into account that linux programs are not as space demanding as windows, but you should still have 10-15GB for the root partition to allow space for programs.
3. Having a separate /home partition is very benefitial. You keep all your documents, settings, data, and you can do a clean install on / without formatting /home thus keeping all you data safe. Similar to having a D: partition in windows and when you format C: and reinstall the data on D: is still there.

When you select the manual partitioning during install (called Something Else in the latest version), it will show a list of all your disks and partitions. The window might be small so you might need to scroll down for other disks.
If you have unallocated space you can start creating partitions, if not you need to delete some first to make unallocated space.
Then you start creating them:
- for the root, 15GB, logical, filesystem ext4, mount point /
- for swap, 2GB, logical, swap area (no mount point for swap)
- for home, all the rest, logical, ext4, mount point /home

Note that the first time you do this, /home will be created and formatted as ext4. In the future when doing new clean installs make sure NOT TO FORMAT /home. You just reuse it as same filesystem ext4 and mount point /home.

Under the partitions list there is a field to select where the bootloader (grub2) goes. With two disks you can select /dev/sda or /dev/sdb. Note that if you don't set BIOS to boot from this disk you will not see grub2. It might keep booting windows directly or similar.

And that's it.

---

### Post by johntland on 2011-12-10
I can't thank you enough! I am not sure what part of the world you are in, but it was about 7:00 AM when I finally got the install on. I finally have slept a couple hours and am now going to try this route. My current problem is, since I didn't do the "windows" install, there is no "Uninstall" Ubuntu option in my "add/remove" windows app. I have looked around on my drive for an "uninstall" file for ubuntu, but since I have this new partition Windows won't even let me see anything. Any thoughts?
 
 
Thanks,
 
JTL
 
:D

---

### Post by darkod on 2011-12-10
Windows does not see linux partitions or the linux OS. So, if you have a dual boot (the right way), from this point on forget about windows knowing ubuntu exists. We are lucky windows knows windows exists at all. :)

If your dilemma is how to get rid of the current ubuntu partitions, as I said, during the manual partitioning it will allow you to delete them and create new ones in their place.
Just be careful which ones you delete. The partitions list will also show the filesystem type and make sure you don't delete any ntfs partition belonging to windows.
If you did the auto install last time, in most cases the root is /dev/sda5 and the swap /dev/sda6 but double check this. Don't just delete #5 and #6 because we can't know what you have there exactly. :)

---

### Post by johntland on 2011-12-10
> **darkod said:**
> The partition sizes depend on your use. However, few of my opinions:
1. The swap partition size. During auto install, the installer selects the swap size depending on your memory and available hdd space. It's much better to set it yourself by using Manual partitioning. If you use hibernate regularly the rule is about 1.5 x RAM but with you having 8GB of memory that would eat up 12GB of your SSD which is a waste. On top of that, with 8GB memory the swap will rarely get used. If you don't plan to hibernate you're good with 1GB or 2GB swap.
2. The main, root partition. The minimum you would need is 5-6GB but you should have at least 10GB. Take into account that linux programs are not as space demanding as windows, but you should still have 10-15GB for the root partition to allow space for programs.
3. Having a separate /home partition is very benefitial. You keep all your documents, settings, data, and you can do a clean install on / without formatting /home thus keeping all you data safe. Similar to having a D: partition in windows and when you format C: and reinstall the data on D: is still there.
 
When you select the manual partitioning during install (called Something Else in the latest version), it will show a list of all your disks and partitions. The window might be small so you might need to scroll down for other disks.
If you have unallocated space you can start creating partitions, if not you need to delete some first to make unallocated space.
Then you start creating them:
- for the root, 15GB, logical, filesystem ext4, mount point /
- for swap, 2GB, logical, swap area (no mount point for swap)
**_- for home, all the rest, logical, ext4, mount point /home_**
 
Note that the first time you do this, /home will be created and formatted as ext4. In the future when doing new clean installs make sure NOT TO FORMAT /home. You just reuse it as same filesystem ext4 and mount point /home.
 
Under the partitions list there is a field to select where the bootloader (grub2) goes. With two disks you can select /dev/sda or /dev/sdb. Note that if you don't set BIOS to boot from this disk you will not see grub2. It might keep booting windows directly or similar.
 
And that's it.
 
So for my /home partition how much space should I pick? That's part of the issue I had with my last install. I ate up too much real estate on the SSD. I want to keep the linux install as small as possible. I count 17GB for the first two partitions, but what do you think is a good size for /home? Keep in mind I have a 500GB sata drive with all my music, videos...documents on as well as another external 3.0 USB drive for storage. It's a 120GB (Windows only shows 111GB for whatever reason) drive, windows is already using 43GB. Add 17GB and I only have 50GB left or so. Knowing windows, if I plan on installing much...that can be eaten up pretty quick. Any thoughts?
 
Thanks,
 
JTL

---

### Post by darkod on 2011-12-10
In that case go to plan B.
Allocate just 5GB or 10GB max for /home, and you can always access all the ntfs partitions from ubuntu too. Windows can't read linux partitions by default, but ubuntu has no problem accessing ntfs.
That's a better solution. Leave the rest of the SSD to win7.

---

### Post by johntland on 2011-12-10
I got the old version off. Deleted the partition(s), fixed the MBR. Got back into windows to download the ISO to do the install. Double clicked on it (to "open" the folder....I thought) and it just started the install through windows. As of now, I am calling it good. It didn't make any new partitions and I have 50GB left on my SSD. So, now the fun begins! Thank you so much for your help!

---

