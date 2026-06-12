---
title: "ubuntu will not load after wubi installation"
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by salviablue on 2012-02-27
After trying several things, I still cannot get ubuntu to install using wubi from within windows 7.

P5Q-PRO MB
64bit
Windows 7 64bit HE
On bootup it say stuff like:
error: couldn't read file
kernel panic: not syncing VFS unable to mount root fs on unknown block (0,0

pwconv failed to change mode  /etc/passwd-0600
status {DRDY}: SRST Failed errno:-16 ata6
error setting up swapspace exception Emask
Warniing: no support for locale:en_GB.uft.8


Iread somethign about sata and ata and windows not being able to read sata unless they are represented as ata (simulation via bios) or soemthing.
It seems windows is indeed regarding the sata hdd as a ata one. 
I don't know how to get around this. I can't afford to buy another sata drive just for a ubuntu install, and I don't have the key  or install disc to reinstall windows (my bro lent me his old comp).



contents of wubi-11.10-rev245.log

```
02-24 22:52 INFO   root: === wubi 11.10 rev245 ===
02-24 22:52 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-24 22:52 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-24 22:52 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\data
02-24 22:52 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\bin\7z.exe
02-24 22:52 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-24 22:52 DEBUG  CommonBackend: Fetching basic info...
02-24 22:52 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-24 22:52 DEBUG  CommonBackend: platform=win32
02-24 22:52 DEBUG  CommonBackend: osname=nt
02-24 22:52 DEBUG  CommonBackend: language=en_GB
02-24 22:52 DEBUG  CommonBackend: encoding=cp1252
02-24 22:52 DEBUG  WindowsBackend: arch=amd64
02-24 22:52 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\data\isolist.ini
02-24 22:52 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-24 22:52 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-24 22:52 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-24 22:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-24 22:52 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-24 22:52 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-24 22:52 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-24 22:52 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-24 22:52 DEBUG  WindowsBackend: Fetching host info...
02-24 22:52 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-24 22:52 DEBUG  WindowsBackend: windows version=vista
02-24 22:52 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-24 22:52 DEBUG  WindowsBackend: windows_sp=None
02-24 22:52 DEBUG  WindowsBackend: windows_build=7601
02-24 22:52 DEBUG  WindowsBackend: gmt=0
02-24 22:52 DEBUG  WindowsBackend: country=GB
02-24 22:52 DEBUG  WindowsBackend: timezone=Europe/London
02-24 22:52 DEBUG  WindowsBackend: windows_username=Dan
02-24 22:52 DEBUG  WindowsBackend: user_full_name=Dan
02-24 22:52 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-24 22:52 DEBUG  WindowsBackend: windows_language_code=1033
02-24 22:52 DEBUG  WindowsBackend: windows_language=English
02-24 22:52 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-24 22:52 DEBUG  WindowsBackend: bootloader=vista
02-24 22:52 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185892.253906 mb free ntfs)
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(C: hd 185892.253906 mb free ntfs)
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(F: hd 72.041015625 mb free ntfs)
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-24 22:52 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
02-24 22:52 DEBUG  WindowsBackend: uninstaller_path=None
02-24 22:52 DEBUG  WindowsBackend: previous_target_dir=None
02-24 22:52 DEBUG  WindowsBackend: previous_distro_name=None
02-24 22:52 DEBUG  WindowsBackend: keyboard_id=134809609
02-24 22:52 DEBUG  WindowsBackend: keyboard_layout=gb
02-24 22:52 DEBUG  WindowsBackend: keyboard_variant=
02-24 22:52 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-24 22:52 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-24 22:52 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-24 22:52 DEBUG  CommonBackend: Searching ISOs on USB devices
02-24 22:52 DEBUG  CommonBackend: Searching for local CDs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-24 22:52 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:52 INFO   root: Running the installer...
02-24 22:52 DEBUG  WindowsFrontend: __init__...
02-24 22:52 DEBUG  WindowsFrontend: on_init...
02-24 22:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\translations, languages=['en_GB', 'en']
02-24 22:52 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\translations, languages=['en_GB', 'en']
02-24 22:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=22000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=dan
02-24 22:53 INFO   root: Received settings
02-24 22:53 DEBUG  CommonBackend: Searching for local CD
02-24 22:53 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\casper\filesystem.squashfs
02-24 22:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-24 22:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-24 22:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-24 22:53 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-24 22:53 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-24 22:53 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-24 22:53 DEBUG  CommonBackend: Searching for local ISO
02-24 22:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\translations, languages=['en_GB', 'en']
02-24 22:53 DEBUG  TaskList: # Running tasklist...
02-24 22:53 DEBUG  TaskList: ## Running select_target_dir...
02-24 22:53 INFO   WindowsBackend: Installing into C:\ubuntu
02-24 22:53 DEBUG  TaskList: ## Finished select_target_dir
02-24 22:53 DEBUG  TaskList: ## Running create_dir_structure...
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-24 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-24 22:53 DEBUG  TaskList: ## Finished create_dir_structure
02-24 22:53 DEBUG  TaskList: ## Running create_uninstaller...
02-24 22:53 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-24 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-24 22:53 DEBUG  TaskList: ## Finished create_uninstaller
02-24 22:53 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-24 22:53 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-24 22:53 DEBUG  TaskList: ## Running get_diskimage...
02-24 22:53 DEBUG  TaskList: New task download
02-24 22:53 DEBUG  TaskList: ### Running download...
02-24 22:53 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-24 22:53 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-24 23:01 DEBUG  TaskList: ### Finished download
02-24 23:01 DEBUG  downloader: download finished (read 507143012 bytes)
02-24 23:01 DEBUG  TaskList: ## Finished get_diskimage
02-24 23:01 DEBUG  TaskList: ## Running extract_diskimage...
02-24 23:03 DEBUG  TaskList: ## Finished extract_diskimage
02-24 23:03 DEBUG  TaskList: ## Running choose_disk_sizes...
02-24 23:03 DEBUG  WindowsBackend: total size=22000
  root=21744
  swap=256
  home=0
  usr=0
02-24 23:03 DEBUG  TaskList: ## Finished choose_disk_sizes
02-24 23:03 DEBUG  TaskList: ## Running expand_diskimage...
02-24 23:07 DEBUG  TaskList: ## Finished expand_diskimage
02-24 23:07 DEBUG  TaskList: ## Running create_swap_diskimage...
02-24 23:07 DEBUG  TaskList: ## Finished create_swap_diskimage
02-24 23:07 DEBUG  TaskList: ## Running modify_bootloader...
02-24 23:07 DEBUG  TaskList: New task modify_bcd
02-24 23:07 DEBUG  TaskList: ### Running modify_bcd...
02-24 23:07 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 185892.253906 mb free ntfs)
02-24 23:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {1e2471c6-0326-11e0-8fd1-83330c7b2e7c}
02-24 23:07 DEBUG  TaskList: ### Finished modify_bcd
02-24 23:07 DEBUG  TaskList: New task modify_bcd
02-24 23:07 DEBUG  TaskList: ### Running modify_bcd...
02-24 23:07 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 72.041015625 mb free ntfs)
02-24 23:07 DEBUG  WindowsBackend: BCD has already been modified
02-24 23:07 DEBUG  TaskList: ### Finished modify_bcd
02-24 23:07 DEBUG  TaskList: New task modify_bcd
02-24 23:07 DEBUG  TaskList: ### Running modify_bcd...
02-24 23:07 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 0.0 mb free )
02-24 23:07 DEBUG  WindowsBackend: BCD has already been modified
02-24 23:07 DEBUG  TaskList: ### Finished modify_bcd
02-24 23:07 DEBUG  TaskList: ## Finished modify_bootloader
02-24 23:07 DEBUG  TaskList: ## Running diskimage_bootloader...
02-24 23:07 DEBUG  WindowsBackend: Copying C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\winboot -> C:\ubuntu\winboot
02-24 23:07 DEBUG  TaskList: ## Finished diskimage_bootloader
02-24 23:07 DEBUG  TaskList: # Finished tasklist
02-24 23:07 INFO   root: Almost finished installing
02-24 23:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl7619.tmp\translations, languages=['en_GB', 'en']
02-24 23:32 INFO   root: Finished installation
02-24 23:32 INFO   root: Rebooting
02-24 23:32 DEBUG  TaskList: # Running tasklist...
02-24 23:32 DEBUG  TaskList: ## Running reboot...
02-24 23:32 DEBUG  TaskList: ## Finished reboot
02-24 23:32 DEBUG  TaskList: # Finished tasklist
02-24 23:32 DEBUG  root: application.quit
02-24 23:32 DEBUG  WindowsFrontend: frontend.quit
02-24 23:32 DEBUG  WindowsFrontend: frontend.on_quit
02-24 23:32 DEBUG  root: application.on_quit
02-24 23:32 INFO   root: sys.exit
02-25 18:25 INFO   root: === wubi 11.10 rev245 ===
02-25 18:25 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 18:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-25 18:25 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\data
02-25 18:25 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\bin\7z.exe
02-25 18:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 18:25 DEBUG  CommonBackend: Fetching basic info...
02-25 18:25 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-25 18:25 DEBUG  CommonBackend: platform=win32
02-25 18:25 DEBUG  CommonBackend: osname=nt
02-25 18:25 DEBUG  CommonBackend: language=en_GB
02-25 18:25 DEBUG  CommonBackend: encoding=cp1252
02-25 18:25 DEBUG  WindowsBackend: arch=amd64
02-25 18:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\data\isolist.ini
02-25 18:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 18:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 18:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 18:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 18:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 18:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 18:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 18:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 18:25 DEBUG  WindowsBackend: Fetching host info...
02-25 18:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 18:25 DEBUG  WindowsBackend: windows version=vista
02-25 18:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 18:25 DEBUG  WindowsBackend: windows_sp=None
02-25 18:25 DEBUG  WindowsBackend: windows_build=7601
02-25 18:25 DEBUG  WindowsBackend: gmt=0
02-25 18:25 DEBUG  WindowsBackend: country=GB
02-25 18:25 DEBUG  WindowsBackend: timezone=Europe/London
02-25 18:25 DEBUG  WindowsBackend: windows_username=Dan
02-25 18:25 DEBUG  WindowsBackend: user_full_name=Dan
02-25 18:25 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 18:25 DEBUG  WindowsBackend: windows_language_code=1033
02-25 18:25 DEBUG  WindowsBackend: windows_language=English
02-25 18:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 18:25 DEBUG  WindowsBackend: bootloader=vista
02-25 18:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180975.984375 mb free ntfs)
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(C: hd 180975.984375 mb free ntfs)
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(F: hd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(I: hd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: drive=Drive(J: hd 0.0 mb free )
02-25 18:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 18:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 18:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 18:25 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 18:25 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 18:25 DEBUG  WindowsBackend: keyboard_variant=
02-25 18:25 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 18:25 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 18:25 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 18:25 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 18:25 DEBUG  CommonBackend: Searching for local CDs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 18:25 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 18:25 INFO   root: Already installed, running the uninstaller...
02-25 18:25 INFO   root: Running the uninstaller...
02-25 18:25 INFO   CommonBackend: This is the uninstaller running
02-25 18:25 DEBUG  WindowsFrontend: __init__...
02-25 18:25 DEBUG  WindowsFrontend: on_init...
02-25 18:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl1FDF.tmp\translations, languages=['en_GB', 'en']
02-25 18:25 INFO   WindowsFrontend: Operation cancelled
02-25 18:25 DEBUG  WindowsFrontend: frontend.quit
02-25 18:25 DEBUG  WindowsFrontend: frontend.on_quit
02-25 18:25 DEBUG  root: application.on_quit
02-25 18:25 INFO   root: sys.exit
02-25 20:17 INFO   root: === wubi 11.10 rev245 ===
02-25 20:17 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 20:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-25 20:17 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\data
02-25 20:17 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\bin\7z.exe
02-25 20:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 20:17 DEBUG  CommonBackend: Fetching basic info...
02-25 20:17 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-25 20:17 DEBUG  CommonBackend: platform=win32
02-25 20:17 DEBUG  CommonBackend: osname=nt
02-25 20:17 DEBUG  CommonBackend: language=en_GB
02-25 20:17 DEBUG  CommonBackend: encoding=cp1252
02-25 20:17 DEBUG  WindowsBackend: arch=amd64
02-25 20:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\data\isolist.ini
02-25 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 20:17 DEBUG  WindowsBackend: Fetching host info...
02-25 20:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 20:17 DEBUG  WindowsBackend: windows version=vista
02-25 20:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 20:17 DEBUG  WindowsBackend: windows_sp=None
02-25 20:17 DEBUG  WindowsBackend: windows_build=7601
02-25 20:17 DEBUG  WindowsBackend: gmt=0
02-25 20:17 DEBUG  WindowsBackend: country=GB
02-25 20:17 DEBUG  WindowsBackend: timezone=Europe/London
02-25 20:17 DEBUG  WindowsBackend: windows_username=Dan
02-25 20:17 DEBUG  WindowsBackend: user_full_name=Dan
02-25 20:17 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 20:17 DEBUG  WindowsBackend: windows_language_code=1033
02-25 20:17 DEBUG  WindowsBackend: windows_language=English
02-25 20:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 20:17 DEBUG  WindowsBackend: bootloader=vista
02-25 20:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180876.101563 mb free ntfs)
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(C: hd 180876.101563 mb free ntfs)
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(F: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(I: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(J: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 20:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 20:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 20:17 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 20:17 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 20:17 DEBUG  WindowsBackend: keyboard_variant=
02-25 20:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 20:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 20:17 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 20:17 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 20:17 DEBUG  CommonBackend: Searching for local CDs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 INFO   root: Already installed, running the uninstaller...
02-25 20:17 INFO   root: Running the uninstaller...
02-25 20:17 INFO   CommonBackend: This is the uninstaller running
02-25 20:17 DEBUG  WindowsFrontend: __init__...
02-25 20:17 DEBUG  WindowsFrontend: on_init...
02-25 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylDE21.tmp\translations, languages=['en_GB', 'en']
02-25 20:17 INFO   WindowsFrontend: Operation cancelled
02-25 20:17 DEBUG  WindowsFrontend: frontend.quit
02-25 20:17 DEBUG  WindowsFrontend: frontend.on_quit
02-25 20:17 DEBUG  root: application.on_quit
02-25 20:17 INFO   root: sys.exit
02-25 20:17 INFO   root: === wubi 11.10 rev245 ===
02-25 20:17 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 20:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-25 20:17 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\data
02-25 20:17 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\bin\7z.exe
02-25 20:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 20:17 DEBUG  CommonBackend: Fetching basic info...
02-25 20:17 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-25 20:17 DEBUG  CommonBackend: platform=win32
02-25 20:17 DEBUG  CommonBackend: osname=nt
02-25 20:17 DEBUG  CommonBackend: language=en_GB
02-25 20:17 DEBUG  CommonBackend: encoding=cp1252
02-25 20:17 DEBUG  WindowsBackend: arch=amd64
02-25 20:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\data\isolist.ini
02-25 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 20:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 20:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 20:17 DEBUG  WindowsBackend: Fetching host info...
02-25 20:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 20:17 DEBUG  WindowsBackend: windows version=vista
02-25 20:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 20:17 DEBUG  WindowsBackend: windows_sp=None
02-25 20:17 DEBUG  WindowsBackend: windows_build=7601
02-25 20:17 DEBUG  WindowsBackend: gmt=0
02-25 20:17 DEBUG  WindowsBackend: country=GB
02-25 20:17 DEBUG  WindowsBackend: timezone=Europe/London
02-25 20:17 DEBUG  WindowsBackend: windows_username=Dan
02-25 20:17 DEBUG  WindowsBackend: user_full_name=Dan
02-25 20:17 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 20:17 DEBUG  WindowsBackend: windows_language_code=1033
02-25 20:17 DEBUG  WindowsBackend: windows_language=English
02-25 20:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 20:17 DEBUG  WindowsBackend: bootloader=vista
02-25 20:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 180874.933594 mb free ntfs)
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(C: hd 180874.933594 mb free ntfs)
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(F: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(I: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: drive=Drive(J: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 20:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 20:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 20:17 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 20:17 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 20:17 DEBUG  WindowsBackend: keyboard_variant=
02-25 20:17 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 20:17 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 20:17 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 20:17 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 20:17 DEBUG  CommonBackend: Searching for local CDs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:17 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:17 INFO   root: Running the uninstaller...
02-25 20:17 INFO   CommonBackend: This is the uninstaller running
02-25 20:17 DEBUG  WindowsFrontend: __init__...
02-25 20:17 DEBUG  WindowsFrontend: on_init...
02-25 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\translations, languages=['en_GB', 'en']
02-25 20:17 INFO   root: Received settings
02-25 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\translations, languages=['en_GB', 'en']
02-25 20:17 DEBUG  TaskList: # Running tasklist...
02-25 20:17 DEBUG  TaskList: ## Running Remove bootloader entry....
02-25 20:17 DEBUG  WindowsBackend: Removing bcd entry {1e2471c6-0326-11e0-8fd1-83330c7b2e7c}
02-25 20:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-25 20:17 DEBUG  WindowsBackend: undo_bootini C:
02-25 20:17 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 180874.933594 mb free ntfs)
02-25 20:17 DEBUG  WindowsBackend: undo_bootini F:
02-25 20:17 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: undo_bootini H:
02-25 20:17 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: undo_bootini I:
02-25 20:17 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 0.0 mb free )
02-25 20:17 DEBUG  WindowsBackend: undo_bootini J:
02-25 20:17 DEBUG  WindowsBackend: undo_configsys Drive(J: hd 0.0 mb free )
02-25 20:17 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-25 20:17 DEBUG  TaskList: ## Running Remove target dir....
02-25 20:17 DEBUG  CommonBackend: Deleting C:\ubuntu
02-25 20:17 DEBUG  TaskList: ## Finished Remove target dir.
02-25 20:17 DEBUG  TaskList: ## Running Remove registry key....
02-25 20:17 DEBUG  TaskList: ## Finished Remove registry key.
02-25 20:17 DEBUG  TaskList: # Finished tasklist
02-25 20:17 INFO   root: Almost finished uninstalling
02-25 20:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl4491.tmp\translations, languages=['en_GB', 'en']
02-25 20:17 INFO   root: Finished uninstallation
02-25 20:17 DEBUG  root: application.quit
02-25 20:17 DEBUG  WindowsFrontend: frontend.quit
02-25 20:17 DEBUG  WindowsFrontend: frontend.on_quit
02-25 20:17 DEBUG  root: application.on_quit
02-25 20:17 INFO   root: sys.exit
02-25 20:18 INFO   root: === wubi 11.10 rev245 ===
02-25 20:18 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 20:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-25 20:18 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\data
02-25 20:18 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\bin\7z.exe
02-25 20:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 20:18 DEBUG  CommonBackend: Fetching basic info...
02-25 20:18 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-25 20:18 DEBUG  CommonBackend: platform=win32
02-25 20:18 DEBUG  CommonBackend: osname=nt
02-25 20:18 DEBUG  CommonBackend: language=en_GB
02-25 20:18 DEBUG  CommonBackend: encoding=cp1252
02-25 20:18 DEBUG  WindowsBackend: arch=amd64
02-25 20:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\data\isolist.ini
02-25 20:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 20:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 20:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 20:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 20:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 20:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 20:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 20:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 20:18 DEBUG  WindowsBackend: Fetching host info...
02-25 20:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 20:18 DEBUG  WindowsBackend: windows version=vista
02-25 20:18 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 20:18 DEBUG  WindowsBackend: windows_sp=None
02-25 20:18 DEBUG  WindowsBackend: windows_build=7601
02-25 20:18 DEBUG  WindowsBackend: gmt=0
02-25 20:18 DEBUG  WindowsBackend: country=GB
02-25 20:18 DEBUG  WindowsBackend: timezone=Europe/London
02-25 20:18 DEBUG  WindowsBackend: windows_username=Dan
02-25 20:18 DEBUG  WindowsBackend: user_full_name=Dan
02-25 20:18 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 20:18 DEBUG  WindowsBackend: windows_language_code=1033
02-25 20:18 DEBUG  WindowsBackend: windows_language=English
02-25 20:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 20:18 DEBUG  WindowsBackend: bootloader=vista
02-25 20:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 184167.410156 mb free ntfs)
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(C: hd 184167.410156 mb free ntfs)
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(F: hd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(I: hd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: drive=Drive(J: hd 0.0 mb free )
02-25 20:18 DEBUG  WindowsBackend: uninstaller_path=None
02-25 20:18 DEBUG  WindowsBackend: previous_target_dir=None
02-25 20:18 DEBUG  WindowsBackend: previous_distro_name=None
02-25 20:18 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 20:18 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 20:18 DEBUG  WindowsBackend: keyboard_variant=
02-25 20:18 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 20:18 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 20:18 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 20:18 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 20:18 DEBUG  CommonBackend: Searching for local CDs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 INFO   root: Running the installer...
02-25 20:18 DEBUG  WindowsFrontend: __init__...
02-25 20:18 DEBUG  WindowsFrontend: on_init...
02-25 20:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\translations, languages=['en_GB', 'en']
02-25 20:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\translations, languages=['en_GB', 'en']
02-25 20:18 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=dan
02-25 20:18 INFO   root: Received settings
02-25 20:18 DEBUG  CommonBackend: Searching for local CD
02-25 20:18 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB711.tmp is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
02-25 20:18 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
02-25 20:18 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
02-25 20:18 DEBUG  CommonBackend: Searching for local ISO
02-25 20:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\translations, languages=['en_GB', 'en']
02-25 20:18 DEBUG  TaskList: # Running tasklist...
02-25 20:18 DEBUG  TaskList: ## Running select_target_dir...
02-25 20:18 INFO   WindowsBackend: Installing into C:\ubuntu
02-25 20:18 DEBUG  TaskList: ## Finished select_target_dir
02-25 20:18 DEBUG  TaskList: ## Running create_dir_structure...
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-25 20:18 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-25 20:18 DEBUG  TaskList: ## Finished create_dir_structure
02-25 20:18 DEBUG  TaskList: ## Running create_uninstaller...
02-25 20:18 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-25 20:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-25 20:18 DEBUG  TaskList: ## Finished create_uninstaller
02-25 20:18 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-25 20:18 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-25 20:18 DEBUG  TaskList: ## Running get_diskimage...
02-25 20:18 DEBUG  TaskList: New task download
02-25 20:18 DEBUG  TaskList: ### Running download...
02-25 20:18 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-25 20:18 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-25 20:26 DEBUG  TaskList: ### Finished download
02-25 20:26 DEBUG  downloader: download finished (read 507143012 bytes)
02-25 20:26 DEBUG  TaskList: ## Finished get_diskimage
02-25 20:26 DEBUG  TaskList: ## Running extract_diskimage...
02-25 20:27 DEBUG  TaskList: ## Finished extract_diskimage
02-25 20:27 DEBUG  TaskList: ## Running choose_disk_sizes...
02-25 20:27 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
02-25 20:27 DEBUG  TaskList: ## Finished choose_disk_sizes
02-25 20:27 DEBUG  TaskList: ## Running expand_diskimage...
02-25 20:30 DEBUG  TaskList: ## Finished expand_diskimage
02-25 20:30 DEBUG  TaskList: ## Running create_swap_diskimage...
02-25 20:30 DEBUG  TaskList: ## Finished create_swap_diskimage
02-25 20:30 DEBUG  TaskList: ## Running modify_bootloader...
02-25 20:30 DEBUG  TaskList: New task modify_bcd
02-25 20:30 DEBUG  TaskList: ### Running modify_bcd...
02-25 20:30 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 184167.410156 mb free ntfs)
02-25 20:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {1e2471c7-0326-11e0-8fd1-83330c7b2e7c}
02-25 20:30 DEBUG  TaskList: ### Finished modify_bcd
02-25 20:30 DEBUG  TaskList: New task modify_bcd
02-25 20:30 DEBUG  TaskList: ### Running modify_bcd...
02-25 20:30 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 0.0 mb free )
02-25 20:30 DEBUG  WindowsBackend: BCD has already been modified
02-25 20:30 DEBUG  TaskList: ### Finished modify_bcd
02-25 20:30 DEBUG  TaskList: New task modify_bcd
02-25 20:30 DEBUG  TaskList: ### Running modify_bcd...
02-25 20:30 DEBUG  WindowsBackend: modify_bcd Drive(H: hd 0.0 mb free )
02-25 20:30 DEBUG  WindowsBackend: BCD has already been modified
02-25 20:30 DEBUG  TaskList: ### Finished modify_bcd
02-25 20:30 DEBUG  TaskList: New task modify_bcd
02-25 20:30 DEBUG  TaskList: ### Running modify_bcd...
02-25 20:30 DEBUG  WindowsBackend: modify_bcd Drive(I: hd 0.0 mb free )
02-25 20:30 DEBUG  WindowsBackend: BCD has already been modified
02-25 20:30 DEBUG  TaskList: ### Finished modify_bcd
02-25 20:30 DEBUG  TaskList: New task modify_bcd
02-25 20:30 DEBUG  TaskList: ### Running modify_bcd...
02-25 20:30 DEBUG  WindowsBackend: modify_bcd Drive(J: hd 0.0 mb free )
02-25 20:30 DEBUG  WindowsBackend: BCD has already been modified
02-25 20:30 DEBUG  TaskList: ### Finished modify_bcd
02-25 20:30 DEBUG  TaskList: ## Finished modify_bootloader
02-25 20:30 DEBUG  TaskList: ## Running diskimage_bootloader...
02-25 20:30 DEBUG  WindowsBackend: Copying C:\Users\Dan\AppData\Local\Temp\pylB711.tmp\winboot -> C:\ubuntu\winboot
02-25 20:30 ERROR  TaskList: [Errno 2] No such file or directory: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'F:\\wubildr'
02-25 20:30 DEBUG  TaskList: # Cancelling tasklist
02-25 20:30 DEBUG  TaskList: # Finished tasklist
02-25 20:30 ERROR  root: [Errno 2] No such file or directory: 'F:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 483, in diskimage_bootloader
  File "\lib\shutil.py", line 39, in copyfile
IOError: [Errno 2] No such file or directory: 'F:\\wubildr'
02-25 22:25 INFO   root: === wubi 11.10 rev245 ===
02-25 22:25 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 22:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-25 22:25 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\data
02-25 22:25 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\bin\7z.exe
02-25 22:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 22:25 DEBUG  CommonBackend: Fetching basic info...
02-25 22:25 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-25 22:25 DEBUG  CommonBackend: platform=win32
02-25 22:25 DEBUG  CommonBackend: osname=nt
02-25 22:25 DEBUG  CommonBackend: language=en_GB
02-25 22:25 DEBUG  CommonBackend: encoding=cp1252
02-25 22:25 DEBUG  WindowsBackend: arch=amd64
02-25 22:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\data\isolist.ini
02-25 22:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 22:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 22:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 22:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 22:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 22:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 22:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 22:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 22:25 DEBUG  WindowsBackend: Fetching host info...
02-25 22:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 22:25 DEBUG  WindowsBackend: windows version=vista
02-25 22:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 22:25 DEBUG  WindowsBackend: windows_sp=None
02-25 22:25 DEBUG  WindowsBackend: windows_build=7601
02-25 22:25 DEBUG  WindowsBackend: gmt=0
02-25 22:25 DEBUG  WindowsBackend: country=GB
02-25 22:25 DEBUG  WindowsBackend: timezone=Europe/London
02-25 22:25 DEBUG  WindowsBackend: windows_username=Dan
02-25 22:25 DEBUG  WindowsBackend: user_full_name=Dan
02-25 22:25 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 22:25 DEBUG  WindowsBackend: windows_language_code=1033
02-25 22:25 DEBUG  WindowsBackend: windows_language=English
02-25 22:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 22:25 DEBUG  WindowsBackend: bootloader=vista
02-25 22:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 181141.53125 mb free ntfs)
02-25 22:25 DEBUG  WindowsBackend: drive=Drive(C: hd 181141.53125 mb free ntfs)
02-25 22:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 22:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 22:25 DEBUG  WindowsBackend: drive=Drive(F: hd 8399.7265625 mb free fat32)
02-25 22:25 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 22:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-25 22:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-25 22:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-25 22:25 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 22:25 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 22:25 DEBUG  WindowsBackend: keyboard_variant=
02-25 22:25 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 22:25 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 22:25 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 22:25 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 22:25 DEBUG  Distro:   checking Ubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Ubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Kubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Kubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Xubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Xubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Mythbuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  Distro:   checking Mythbuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:25 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:25 DEBUG  CommonBackend: Searching for local CDs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 22:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:25 INFO   root: Running the uninstaller...
02-25 22:25 INFO   CommonBackend: This is the uninstaller running
02-25 22:25 DEBUG  WindowsFrontend: __init__...
02-25 22:25 DEBUG  WindowsFrontend: on_init...
02-25 22:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\translations, languages=['en_GB', 'en']
02-25 22:25 INFO   root: Received settings
02-25 22:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\translations, languages=['en_GB', 'en']
02-25 22:25 DEBUG  TaskList: # Running tasklist...
02-25 22:25 DEBUG  TaskList: ## Running Remove bootloader entry....
02-25 22:25 DEBUG  WindowsBackend: Removing bcd entry {1e2471c7-0326-11e0-8fd1-83330c7b2e7c}
02-25 22:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-25 22:25 DEBUG  WindowsBackend: undo_bootini C:
02-25 22:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 181141.53125 mb free ntfs)
02-25 22:25 DEBUG  WindowsBackend: undo_bootini F:
02-25 22:25 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 8399.7265625 mb free fat32)
02-25 22:25 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-25 22:25 DEBUG  TaskList: ## Running Remove target dir....
02-25 22:25 DEBUG  CommonBackend: Deleting C:\ubuntu
02-25 22:26 DEBUG  TaskList: ## Finished Remove target dir.
02-25 22:26 DEBUG  TaskList: ## Running Remove registry key....
02-25 22:26 DEBUG  TaskList: ## Finished Remove registry key.
02-25 22:26 DEBUG  TaskList: # Finished tasklist
02-25 22:26 INFO   root: Almost finished uninstalling
02-25 22:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl8D94.tmp\translations, languages=['en_GB', 'en']
02-25 22:26 INFO   root: Finished uninstallation
02-25 22:26 DEBUG  root: application.quit
02-25 22:26 DEBUG  WindowsFrontend: frontend.quit
02-25 22:26 DEBUG  WindowsFrontend: frontend.on_quit
02-25 22:26 DEBUG  root: application.on_quit
02-25 22:26 INFO   root: sys.exit
02-25 22:31 INFO   root: === wubi 11.10 rev245 ===
02-25 22:31 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-25 22:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-25 22:31 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\data
02-25 22:31 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\bin\7z.exe
02-25 22:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-25 22:31 DEBUG  CommonBackend: Fetching basic info...
02-25 22:31 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-25 22:31 DEBUG  CommonBackend: platform=win32
02-25 22:31 DEBUG  CommonBackend: osname=nt
02-25 22:31 DEBUG  CommonBackend: language=en_GB
02-25 22:31 DEBUG  CommonBackend: encoding=cp1252
02-25 22:31 DEBUG  WindowsBackend: arch=amd64
02-25 22:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\data\isolist.ini
02-25 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-25 22:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-25 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-25 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-25 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-25 22:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-25 22:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-25 22:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-25 22:31 DEBUG  WindowsBackend: Fetching host info...
02-25 22:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-25 22:31 DEBUG  WindowsBackend: windows version=vista
02-25 22:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-25 22:31 DEBUG  WindowsBackend: windows_sp=None
02-25 22:31 DEBUG  WindowsBackend: windows_build=7601
02-25 22:31 DEBUG  WindowsBackend: gmt=0
02-25 22:31 DEBUG  WindowsBackend: country=GB
02-25 22:31 DEBUG  WindowsBackend: timezone=Europe/London
02-25 22:31 DEBUG  WindowsBackend: windows_username=Dan
02-25 22:31 DEBUG  WindowsBackend: user_full_name=Dan
02-25 22:31 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-25 22:31 DEBUG  WindowsBackend: windows_language_code=1033
02-25 22:31 DEBUG  WindowsBackend: windows_language=English
02-25 22:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-25 22:31 DEBUG  WindowsBackend: bootloader=vista
02-25 22:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 184227.148438 mb free ntfs)
02-25 22:31 DEBUG  WindowsBackend: drive=Drive(C: hd 184227.148438 mb free ntfs)
02-25 22:31 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-25 22:31 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-25 22:31 DEBUG  WindowsBackend: drive=Drive(F: hd 8399.7265625 mb free fat32)
02-25 22:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-25 22:31 DEBUG  WindowsBackend: uninstaller_path=None
02-25 22:31 DEBUG  WindowsBackend: previous_target_dir=None
02-25 22:31 DEBUG  WindowsBackend: previous_distro_name=None
02-25 22:31 DEBUG  WindowsBackend: keyboard_id=134809609
02-25 22:31 DEBUG  WindowsBackend: keyboard_layout=gb
02-25 22:31 DEBUG  WindowsBackend: keyboard_variant=
02-25 22:31 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-25 22:31 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-25 22:31 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-25 22:31 DEBUG  CommonBackend: Searching ISOs on USB devices
02-25 22:31 DEBUG  Distro:   checking Ubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Ubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Kubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Kubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Xubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Xubuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Mythbuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  Distro:   checking Mythbuntu ISO F:\opengeu-8.04.1-desktop-i386.iso
02-25 22:31 DEBUG  Distro:     does not contain casper\initrd.lz
02-25 22:31 DEBUG  CommonBackend: Searching for local CDs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 INFO   root: Running the installer...
02-25 22:31 DEBUG  WindowsFrontend: __init__...
02-25 22:31 DEBUG  WindowsFrontend: on_init...
02-25 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\translations, languages=['en_GB', 'en']
02-25 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\translations, languages=['en_GB', 'en']
02-25 22:31 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=dan
02-25 22:31 INFO   root: Received settings
02-25 22:31 DEBUG  CommonBackend: Searching for local CD
02-25 22:31 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
02-25 22:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-25 22:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-25 22:31 DEBUG  CommonBackend: Searching for local ISO
02-25 22:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\translations, languages=['en_GB', 'en']
02-25 22:31 DEBUG  TaskList: # Running tasklist...
02-25 22:31 DEBUG  TaskList: ## Running select_target_dir...
02-25 22:31 INFO   WindowsBackend: Installing into C:\ubuntu
02-25 22:31 DEBUG  TaskList: ## Finished select_target_dir
02-25 22:31 DEBUG  TaskList: ## Running create_dir_structure...
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-25 22:31 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-25 22:31 DEBUG  TaskList: ## Finished create_dir_structure
02-25 22:31 DEBUG  TaskList: ## Running create_uninstaller...
02-25 22:31 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-25 22:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-25 22:31 DEBUG  TaskList: ## Finished create_uninstaller
02-25 22:31 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-25 22:31 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-25 22:31 DEBUG  TaskList: ## Running get_diskimage...
02-25 22:31 DEBUG  TaskList: New task download
02-25 22:31 DEBUG  TaskList: ### Running download...
02-25 22:31 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-25 22:31 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-25 22:39 DEBUG  TaskList: ### Finished download
02-25 22:39 DEBUG  downloader: download finished (read 507143012 bytes)
02-25 22:39 DEBUG  TaskList: ## Finished get_diskimage
02-25 22:39 DEBUG  TaskList: ## Running extract_diskimage...
02-25 22:40 DEBUG  TaskList: ## Finished extract_diskimage
02-25 22:40 DEBUG  TaskList: ## Running choose_disk_sizes...
02-25 22:40 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
02-25 22:40 DEBUG  TaskList: ## Finished choose_disk_sizes
02-25 22:40 DEBUG  TaskList: ## Running expand_diskimage...
02-25 22:43 DEBUG  TaskList: ## Finished expand_diskimage
02-25 22:43 DEBUG  TaskList: ## Running create_swap_diskimage...
02-25 22:43 DEBUG  TaskList: ## Finished create_swap_diskimage
02-25 22:43 DEBUG  TaskList: ## Running modify_bootloader...
02-25 22:43 DEBUG  TaskList: New task modify_bcd
02-25 22:43 DEBUG  TaskList: ### Running modify_bcd...
02-25 22:43 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 184227.148438 mb free ntfs)
02-25 22:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {1e2471c8-0326-11e0-8fd1-83330c7b2e7c}
02-25 22:43 DEBUG  TaskList: ### Finished modify_bcd
02-25 22:43 DEBUG  TaskList: New task modify_bcd
02-25 22:43 DEBUG  TaskList: ### Running modify_bcd...
02-25 22:43 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 8399.7265625 mb free fat32)
02-25 22:43 DEBUG  WindowsBackend: BCD has already been modified
02-25 22:43 DEBUG  TaskList: ### Finished modify_bcd
02-25 22:43 DEBUG  TaskList: ## Finished modify_bootloader
02-25 22:43 DEBUG  TaskList: ## Running diskimage_bootloader...
02-25 22:43 DEBUG  WindowsBackend: Copying C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\winboot -> C:\ubuntu\winboot
02-25 22:43 DEBUG  TaskList: ## Finished diskimage_bootloader
02-25 22:43 DEBUG  TaskList: # Finished tasklist
02-25 22:43 INFO   root: Almost finished installing
02-25 22:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl9706.tmp\translations, languages=['en_GB', 'en']
02-25 22:43 INFO   root: Finished installation
02-25 22:43 DEBUG  root: application.quit
02-25 22:43 DEBUG  WindowsFrontend: frontend.quit
02-25 22:43 DEBUG  WindowsFrontend: frontend.on_quit
02-25 22:43 DEBUG  root: application.on_quit
02-25 22:43 INFO   root: sys.exit
02-26 01:05 INFO   root: === wubi 11.10 rev245 ===
02-26 01:05 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-26 01:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-26 01:05 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\data
02-26 01:05 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\bin\7z.exe
02-26 01:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-26 01:05 DEBUG  CommonBackend: Fetching basic info...
02-26 01:05 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-26 01:05 DEBUG  CommonBackend: platform=win32
02-26 01:05 DEBUG  CommonBackend: osname=nt
02-26 01:05 DEBUG  CommonBackend: language=en_GB
02-26 01:05 DEBUG  CommonBackend: encoding=cp1252
02-26 01:05 DEBUG  WindowsBackend: arch=amd64
02-26 01:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\data\isolist.ini
02-26 01:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 01:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 01:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 01:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 01:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 01:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 01:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 01:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 01:05 DEBUG  WindowsBackend: Fetching host info...
02-26 01:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 01:05 DEBUG  WindowsBackend: windows version=vista
02-26 01:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-26 01:05 DEBUG  WindowsBackend: windows_sp=None
02-26 01:05 DEBUG  WindowsBackend: windows_build=7601
02-26 01:05 DEBUG  WindowsBackend: gmt=0
02-26 01:05 DEBUG  WindowsBackend: country=GB
02-26 01:05 DEBUG  WindowsBackend: timezone=Europe/London
02-26 01:05 DEBUG  WindowsBackend: windows_username=Dan
02-26 01:05 DEBUG  WindowsBackend: user_full_name=Dan
02-26 01:05 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-26 01:05 DEBUG  WindowsBackend: windows_language_code=1033
02-26 01:05 DEBUG  WindowsBackend: windows_language=English
02-26 01:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-26 01:05 DEBUG  WindowsBackend: bootloader=vista
02-26 01:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 182113.132813 mb free ntfs)
02-26 01:05 DEBUG  WindowsBackend: drive=Drive(C: hd 182113.132813 mb free ntfs)
02-26 01:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-26 01:05 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 01:05 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-26 01:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-26 01:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-26 01:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-26 01:05 DEBUG  WindowsBackend: keyboard_id=134809609
02-26 01:05 DEBUG  WindowsBackend: keyboard_layout=gb
02-26 01:05 DEBUG  WindowsBackend: keyboard_variant=
02-26 01:05 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-26 01:05 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-26 01:05 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-26 01:05 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 01:05 DEBUG  CommonBackend: Searching for local CDs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-26 01:05 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:05 INFO   root: Running the uninstaller...
02-26 01:05 INFO   CommonBackend: This is the uninstaller running
02-26 01:05 DEBUG  WindowsFrontend: __init__...
02-26 01:05 DEBUG  WindowsFrontend: on_init...
02-26 01:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\translations, languages=['en_GB', 'en']
02-26 01:05 INFO   root: Received settings
02-26 01:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\translations, languages=['en_GB', 'en']
02-26 01:05 DEBUG  TaskList: # Running tasklist...
02-26 01:05 DEBUG  TaskList: ## Running Remove bootloader entry....
02-26 01:05 DEBUG  WindowsBackend: Removing bcd entry {1e2471c8-0326-11e0-8fd1-83330c7b2e7c}
02-26 01:05 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-26 01:05 DEBUG  WindowsBackend: undo_bootini C:
02-26 01:05 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 182113.132813 mb free ntfs)
02-26 01:05 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-26 01:05 DEBUG  TaskList: ## Running Remove target dir....
02-26 01:05 DEBUG  CommonBackend: Deleting C:\ubuntu
02-26 01:05 DEBUG  TaskList: ## Finished Remove target dir.
02-26 01:05 DEBUG  TaskList: ## Running Remove registry key....
02-26 01:05 DEBUG  TaskList: ## Finished Remove registry key.
02-26 01:05 DEBUG  TaskList: # Finished tasklist
02-26 01:05 INFO   root: Almost finished uninstalling
02-26 01:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pyl361D.tmp\translations, languages=['en_GB', 'en']
02-26 01:05 INFO   root: Finished uninstallation
02-26 01:05 DEBUG  root: application.quit
02-26 01:05 DEBUG  WindowsFrontend: frontend.quit
02-26 01:05 DEBUG  WindowsFrontend: frontend.on_quit
02-26 01:05 DEBUG  root: application.on_quit
02-26 01:05 INFO   root: sys.exit
02-26 01:07 INFO   root: === wubi 11.10 rev245 ===
02-26 01:07 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-26 01:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-26 01:07 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\data
02-26 01:07 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\bin\7z.exe
02-26 01:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-26 01:07 DEBUG  CommonBackend: Fetching basic info...
02-26 01:07 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-26 01:07 DEBUG  CommonBackend: platform=win32
02-26 01:07 DEBUG  CommonBackend: osname=nt
02-26 01:07 DEBUG  CommonBackend: language=en_GB
02-26 01:07 DEBUG  CommonBackend: encoding=cp1252
02-26 01:07 DEBUG  WindowsBackend: arch=amd64
02-26 01:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\data\isolist.ini
02-26 01:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-26 01:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-26 01:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-26 01:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-26 01:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-26 01:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-26 01:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-26 01:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-26 01:07 DEBUG  WindowsBackend: Fetching host info...
02-26 01:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-26 01:07 DEBUG  WindowsBackend: windows version=vista
02-26 01:07 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
02-26 01:07 DEBUG  WindowsBackend: windows_sp=None
02-26 01:07 DEBUG  WindowsBackend: windows_build=6000
02-26 01:07 DEBUG  WindowsBackend: gmt=0
02-26 01:07 DEBUG  WindowsBackend: country=GB
02-26 01:07 DEBUG  WindowsBackend: timezone=Europe/London
02-26 01:07 DEBUG  WindowsBackend: windows_username=Dan
02-26 01:07 DEBUG  WindowsBackend: user_full_name=Dan
02-26 01:07 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-26 01:07 DEBUG  WindowsBackend: windows_language_code=1033
02-26 01:07 DEBUG  WindowsBackend: windows_language=English
02-26 01:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-26 01:07 DEBUG  WindowsBackend: bootloader=vista
02-26 01:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185327.636719 mb free ntfs)
02-26 01:07 DEBUG  WindowsBackend: drive=Drive(C: hd 185327.636719 mb free ntfs)
02-26 01:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-26 01:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-26 01:07 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-26 01:07 DEBUG  WindowsBackend: uninstaller_path=None
02-26 01:07 DEBUG  WindowsBackend: previous_target_dir=None
02-26 01:07 DEBUG  WindowsBackend: previous_distro_name=None
02-26 01:07 DEBUG  WindowsBackend: keyboard_id=134809609
02-26 01:07 DEBUG  WindowsBackend: keyboard_layout=gb
02-26 01:07 DEBUG  WindowsBackend: keyboard_variant=
02-26 01:07 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-26 01:07 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-26 01:07 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
02-26 01:07 DEBUG  CommonBackend: Searching ISOs on USB devices
02-26 01:07 DEBUG  CommonBackend: Searching for local CDs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 INFO   root: Running the installer...
02-26 01:07 DEBUG  WindowsFrontend: __init__...
02-26 01:07 DEBUG  WindowsFrontend: on_init...
02-26 01:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\translations, languages=['en_GB', 'en']
02-26 01:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\translations, languages=['en_GB', 'en']
02-26 01:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=dan
02-26 01:07 INFO   root: Received settings
02-26 01:07 DEBUG  CommonBackend: Searching for local CD
02-26 01:07 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-26 01:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-26 01:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-26 01:07 DEBUG  CommonBackend: Searching for local ISO
02-26 01:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\translations, languages=['en_GB', 'en']
02-26 01:07 DEBUG  TaskList: # Running tasklist...
02-26 01:07 DEBUG  TaskList: ## Running select_target_dir...
02-26 01:07 INFO   WindowsBackend: Installing into C:\ubuntu
02-26 01:07 DEBUG  TaskList: ## Finished select_target_dir
02-26 01:07 DEBUG  TaskList: ## Running create_dir_structure...
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-26 01:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-26 01:07 DEBUG  TaskList: ## Finished create_dir_structure
02-26 01:07 DEBUG  TaskList: ## Running create_uninstaller...
02-26 01:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-26 01:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-26 01:07 DEBUG  TaskList: ## Finished create_uninstaller
02-26 01:07 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-26 01:07 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-26 01:07 DEBUG  TaskList: ## Running get_diskimage...
02-26 01:07 DEBUG  TaskList: New task download
02-26 01:07 DEBUG  TaskList: ### Running download...
02-26 01:07 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-26 01:07 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-26 01:14 DEBUG  TaskList: ### Finished download
02-26 01:14 DEBUG  downloader: download finished (read 507143012 bytes)
02-26 01:14 DEBUG  TaskList: ## Finished get_diskimage
02-26 01:14 DEBUG  TaskList: ## Running extract_diskimage...
02-26 01:16 DEBUG  TaskList: ## Finished extract_diskimage
02-26 01:16 DEBUG  TaskList: ## Running choose_disk_sizes...
02-26 01:16 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
02-26 01:16 DEBUG  TaskList: ## Finished choose_disk_sizes
02-26 01:16 DEBUG  TaskList: ## Running expand_diskimage...
02-26 01:18 DEBUG  TaskList: ## Finished expand_diskimage
02-26 01:18 DEBUG  TaskList: ## Running create_swap_diskimage...
02-26 01:18 DEBUG  TaskList: ## Finished create_swap_diskimage
02-26 01:18 DEBUG  TaskList: ## Running modify_bootloader...
02-26 01:18 DEBUG  TaskList: New task modify_bcd
02-26 01:18 DEBUG  TaskList: ### Running modify_bcd...
02-26 01:18 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 185327.636719 mb free ntfs)
02-26 01:18 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {1e2471c9-0326-11e0-8fd1-83330c7b2e7c}
02-26 01:18 DEBUG  TaskList: ### Finished modify_bcd
02-26 01:18 DEBUG  TaskList: ## Finished modify_bootloader
02-26 01:18 DEBUG  TaskList: ## Running diskimage_bootloader...
02-26 01:18 DEBUG  WindowsBackend: Copying C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\winboot -> C:\ubuntu\winboot
02-26 01:18 DEBUG  TaskList: ## Finished diskimage_bootloader
02-26 01:18 DEBUG  TaskList: # Finished tasklist
02-26 01:18 INFO   root: Almost finished installing
02-26 01:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylAEA6.tmp\translations, languages=['en_GB', 'en']
02-26 01:25 INFO   root: Finished installation
02-26 01:25 INFO   root: Rebooting
02-26 01:25 DEBUG  TaskList: # Running tasklist...
02-26 01:25 DEBUG  TaskList: ## Running reboot...
02-26 01:25 DEBUG  TaskList: ## Finished reboot
02-26 01:25 DEBUG  TaskList: # Finished tasklist
02-26 01:25 DEBUG  root: application.quit
02-26 01:25 DEBUG  WindowsFrontend: frontend.quit
02-26 01:25 DEBUG  WindowsFrontend: frontend.on_quit
02-26 01:25 DEBUG  root: application.on_quit
02-26 01:25 INFO   root: sys.exit
02-27 09:40 INFO   root: === wubi 11.10 rev245 ===
02-27 09:40 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-27 09:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
02-27 09:40 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\data
02-27 09:40 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\bin\7z.exe
02-27 09:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-27 09:40 DEBUG  CommonBackend: Fetching basic info...
02-27 09:40 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
02-27 09:40 DEBUG  CommonBackend: platform=win32
02-27 09:40 DEBUG  CommonBackend: osname=nt
02-27 09:40 DEBUG  CommonBackend: language=en_GB
02-27 09:40 DEBUG  CommonBackend: encoding=cp1252
02-27 09:40 DEBUG  WindowsBackend: arch=amd64
02-27 09:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\data\isolist.ini
02-27 09:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 09:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 09:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 09:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 09:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 09:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 09:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 09:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 09:40 DEBUG  WindowsBackend: Fetching host info...
02-27 09:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 09:40 DEBUG  WindowsBackend: windows version=vista
02-27 09:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
02-27 09:40 DEBUG  WindowsBackend: windows_sp=None
02-27 09:40 DEBUG  WindowsBackend: windows_build=7601
02-27 09:40 DEBUG  WindowsBackend: gmt=0
02-27 09:40 DEBUG  WindowsBackend: country=GB
02-27 09:40 DEBUG  WindowsBackend: timezone=Europe/London
02-27 09:40 DEBUG  WindowsBackend: windows_username=Dan
02-27 09:40 DEBUG  WindowsBackend: user_full_name=Dan
02-27 09:40 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-27 09:40 DEBUG  WindowsBackend: windows_language_code=1033
02-27 09:40 DEBUG  WindowsBackend: windows_language=English
02-27 09:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-27 09:40 DEBUG  WindowsBackend: bootloader=vista
02-27 09:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 181891.136719 mb free ntfs)
02-27 09:40 DEBUG  WindowsBackend: drive=Drive(C: hd 181891.136719 mb free ntfs)
02-27 09:40 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-27 09:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 09:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-27 09:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-27 09:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-27 09:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-27 09:40 DEBUG  WindowsBackend: keyboard_id=134809609
02-27 09:40 DEBUG  WindowsBackend: keyboard_layout=gb
02-27 09:40 DEBUG  WindowsBackend: keyboard_variant=
02-27 09:40 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-27 09:40 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-27 09:40 DEBUG  WindowsBackend: total_memory_mb=4095.046875
02-27 09:40 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 09:40 DEBUG  CommonBackend: Searching for local CDs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 09:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:40 INFO   root: Running the uninstaller...
02-27 09:40 INFO   CommonBackend: This is the uninstaller running
02-27 09:40 DEBUG  WindowsFrontend: __init__...
02-27 09:40 DEBUG  WindowsFrontend: on_init...
02-27 09:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_GB', 'en']
02-27 09:40 INFO   root: Received settings
02-27 09:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_GB', 'en']
02-27 09:40 DEBUG  TaskList: # Running tasklist...
02-27 09:40 DEBUG  TaskList: ## Running Remove bootloader entry....
02-27 09:40 DEBUG  WindowsBackend: Removing bcd entry {1e2471c9-0326-11e0-8fd1-83330c7b2e7c}
02-27 09:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
02-27 09:40 DEBUG  WindowsBackend: undo_bootini C:
02-27 09:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 181891.136719 mb free ntfs)
02-27 09:40 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-27 09:40 DEBUG  TaskList: ## Running Remove target dir....
02-27 09:40 DEBUG  CommonBackend: Deleting C:\ubuntu
02-27 09:40 DEBUG  TaskList: ## Finished Remove target dir.
02-27 09:40 DEBUG  TaskList: ## Running Remove registry key....
02-27 09:40 DEBUG  TaskList: ## Finished Remove registry key.
02-27 09:40 DEBUG  TaskList: # Finished tasklist
02-27 09:40 INFO   root: Almost finished uninstalling
02-27 09:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylB53A.tmp\translations, languages=['en_GB', 'en']
02-27 09:41 INFO   root: Finished uninstallation
02-27 09:41 DEBUG  root: application.quit
02-27 09:41 DEBUG  WindowsFrontend: frontend.quit
02-27 09:41 DEBUG  WindowsFrontend: frontend.on_quit
02-27 09:41 DEBUG  root: application.on_quit
02-27 09:41 INFO   root: sys.exit
02-27 09:41 INFO   root: === wubi 11.10 rev245 ===
02-27 09:41 DEBUG  root: Logfile is c:\users\dan\appdata\local\temp\wubi-11.10-rev245.log
02-27 09:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Dan\\Downloads\\wubi.exe"']
02-27 09:41 DEBUG  CommonBackend: data_dir=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\data
02-27 09:41 DEBUG  WindowsBackend: 7z=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\bin\7z.exe
02-27 09:41 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
02-27 09:41 DEBUG  CommonBackend: Fetching basic info...
02-27 09:41 DEBUG  CommonBackend: original_exe=C:\Users\Dan\Downloads\wubi.exe
02-27 09:41 DEBUG  CommonBackend: platform=win32
02-27 09:41 DEBUG  CommonBackend: osname=nt
02-27 09:41 DEBUG  CommonBackend: language=en_GB
02-27 09:41 DEBUG  CommonBackend: encoding=cp1252
02-27 09:41 DEBUG  WindowsBackend: arch=amd64
02-27 09:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\data\isolist.ini
02-27 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-27 09:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-27 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-27 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-27 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-27 09:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-27 09:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-27 09:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-27 09:41 DEBUG  WindowsBackend: Fetching host info...
02-27 09:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-27 09:41 DEBUG  WindowsBackend: windows version=vista
02-27 09:41 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
02-27 09:41 DEBUG  WindowsBackend: windows_sp=None
02-27 09:41 DEBUG  WindowsBackend: windows_build=6000
02-27 09:41 DEBUG  WindowsBackend: gmt=0
02-27 09:41 DEBUG  WindowsBackend: country=GB
02-27 09:41 DEBUG  WindowsBackend: timezone=Europe/London
02-27 09:41 DEBUG  WindowsBackend: windows_username=Dan
02-27 09:41 DEBUG  WindowsBackend: user_full_name=Dan
02-27 09:41 DEBUG  WindowsBackend: user_directory=C:\Users\Dan
02-27 09:41 DEBUG  WindowsBackend: windows_language_code=1033
02-27 09:41 DEBUG  WindowsBackend: windows_language=English
02-27 09:41 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad  CPU   Q8200  @ 2.33GHz
02-27 09:41 DEBUG  WindowsBackend: bootloader=vista
02-27 09:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 185105.464844 mb free ntfs)
02-27 09:41 DEBUG  WindowsBackend: drive=Drive(C: hd 185105.464844 mb free ntfs)
02-27 09:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
02-27 09:41 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
02-27 09:41 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
02-27 09:41 DEBUG  WindowsBackend: uninstaller_path=None
02-27 09:41 DEBUG  WindowsBackend: previous_target_dir=None
02-27 09:41 DEBUG  WindowsBackend: previous_distro_name=None
02-27 09:41 DEBUG  WindowsBackend: keyboard_id=134809609
02-27 09:41 DEBUG  WindowsBackend: keyboard_layout=gb
02-27 09:41 DEBUG  WindowsBackend: keyboard_variant=
02-27 09:41 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-27 09:41 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-27 09:41 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
02-27 09:41 DEBUG  CommonBackend: Searching ISOs on USB devices
02-27 09:41 DEBUG  CommonBackend: Searching for local CDs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
02-27 09:41 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:41 INFO   root: Running the installer...
02-27 09:41 DEBUG  WindowsFrontend: __init__...
02-27 09:41 DEBUG  WindowsFrontend: on_init...
02-27 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\translations, languages=['en_GB', 'en']
02-27 09:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\translations, languages=['en_GB', 'en']
02-27 09:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=20000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=dan
02-27 09:42 INFO   root: Received settings
02-27 09:42 DEBUG  CommonBackend: Searching for local CD
02-27 09:42 DEBUG  Distro:   checking whether C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp is a valid Ubuntu CD
02-27 09:42 DEBUG  Distro:     does not contain C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\casper\filesystem.squashfs
02-27 09:42 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-27 09:42 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-27 09:42 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
02-27 09:42 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
02-27 09:42 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
02-27 09:42 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
02-27 09:42 DEBUG  CommonBackend: Searching for local ISO
02-27 09:42 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\translations, languages=['en_GB', 'en']
02-27 09:42 DEBUG  TaskList: # Running tasklist...
02-27 09:42 DEBUG  TaskList: ## Running select_target_dir...
02-27 09:42 INFO   WindowsBackend: Installing into C:\ubuntu
02-27 09:42 DEBUG  TaskList: ## Finished select_target_dir
02-27 09:42 DEBUG  TaskList: ## Running create_dir_structure...
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-27 09:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-27 09:42 DEBUG  TaskList: ## Finished create_dir_structure
02-27 09:42 DEBUG  TaskList: ## Running create_uninstaller...
02-27 09:42 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Dan\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
02-27 09:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
02-27 09:42 DEBUG  TaskList: ## Finished create_uninstaller
02-27 09:42 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-27 09:42 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-27 09:42 DEBUG  TaskList: ## Running get_diskimage...
02-27 09:42 DEBUG  TaskList: New task download
02-27 09:42 DEBUG  TaskList: ### Running download...
02-27 09:42 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-27 09:42 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
02-27 09:49 DEBUG  TaskList: ### Finished download
02-27 09:49 DEBUG  downloader: download finished (read 507143012 bytes)
02-27 09:49 DEBUG  TaskList: ## Finished get_diskimage
02-27 09:49 DEBUG  TaskList: ## Running extract_diskimage...
02-27 09:51 DEBUG  TaskList: ## Finished extract_diskimage
02-27 09:51 DEBUG  TaskList: ## Running choose_disk_sizes...
02-27 09:51 DEBUG  WindowsBackend: total size=20000
  root=19744
  swap=256
  home=0
  usr=0
02-27 09:51 DEBUG  TaskList: ## Finished choose_disk_sizes
02-27 09:51 DEBUG  TaskList: ## Running expand_diskimage...
02-27 09:55 DEBUG  TaskList: ## Finished expand_diskimage
02-27 09:55 DEBUG  TaskList: ## Running create_swap_diskimage...
02-27 09:55 DEBUG  TaskList: ## Finished create_swap_diskimage
02-27 09:55 DEBUG  TaskList: ## Running modify_bootloader...
02-27 09:55 DEBUG  TaskList: New task modify_bcd
02-27 09:55 DEBUG  TaskList: ### Running modify_bcd...
02-27 09:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 185105.464844 mb free ntfs)
02-27 09:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {1e2471ca-0326-11e0-8fd1-83330c7b2e7c}
02-27 09:55 DEBUG  TaskList: ### Finished modify_bcd
02-27 09:55 DEBUG  TaskList: ## Finished modify_bootloader
02-27 09:55 DEBUG  TaskList: ## Running diskimage_bootloader...
02-27 09:55 DEBUG  WindowsBackend: Copying C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\winboot -> C:\ubuntu\winboot
02-27 09:55 DEBUG  TaskList: ## Finished diskimage_bootloader
02-27 09:55 DEBUG  TaskList: # Finished tasklist
02-27 09:55 INFO   root: Almost finished installing
02-27 09:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Dan\AppData\Local\Temp\pylE31D.tmp\translations, languages=['en_GB', 'en']
02-27 09:55 INFO   root: Finished installation
02-27 09:55 INFO   root: Rebooting
02-27 09:55 DEBUG  TaskList: # Running tasklist...
02-27 09:55 DEBUG  TaskList: ## Running reboot...
02-27 09:55 DEBUG  TaskList: ## Finished reboot
02-27 09:55 DEBUG  TaskList: # Finished tasklist
02-27 09:55 DEBUG  root: application.quit
02-27 09:55 DEBUG  WindowsFrontend: frontend.quit
02-27 09:55 DEBUG  WindowsFrontend: frontend.on_quit
02-27 09:55 DEBUG  root: application.on_quit
02-27 09:55 INFO   root: sys.exit

```

---

