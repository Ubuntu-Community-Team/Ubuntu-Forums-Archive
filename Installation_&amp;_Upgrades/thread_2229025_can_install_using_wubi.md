---
title: "can install using wubi"
date: 2014-06-10
forum: Installation &amp; Upgrades
---

### Post by ashok_saini on 2014-06-10
i downloaded amd iso and extracted it to a folder run wubi as admin
and got this error
running win7 pro 32bit on hp pavilion g6 amd A8

```
log in this error is wubi-14.04-rev286.log --------
06-09 21:45 INFO   root: === wubi 14.04 rev286 ===
06-09 21:45 DEBUG  root: Logfile is c:\users\manu\appdata\local\temp\wubi-14.04-rev286.log
06-09 21:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="Z:\\ashok data\\soft\\linux\\linux\\ubuntu\\ubuntu-14.04-desktop-amd64\\wubi.exe"']
06-09 21:45 DEBUG  CommonBackend: data_dir=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\data
06-09 21:45 DEBUG  WindowsBackend: 7z=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\bin\7z.exe
06-09 21:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-09 21:45 DEBUG  CommonBackend: Fetching basic info...
06-09 21:45 DEBUG  CommonBackend: original_exe=Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\wubi.exe
06-09 21:45 DEBUG  CommonBackend: platform=win32
06-09 21:45 DEBUG  CommonBackend: osname=nt
06-09 21:45 DEBUG  CommonBackend: language=en_US
06-09 21:45 DEBUG  CommonBackend: encoding=cp1252
06-09 21:45 DEBUG  WindowsBackend: arch=amd64
06-09 21:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\data\isolist.ini
06-09 21:45 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-09 21:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
06-09 21:45 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
06-09 21:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-09 21:45 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-09 21:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
06-09 21:45 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
06-09 21:45 DEBUG  WindowsBackend: Fetching host info...
06-09 21:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-09 21:45 DEBUG  WindowsBackend: windows version=vista
06-09 21:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
06-09 21:45 DEBUG  WindowsBackend: windows_sp=None
06-09 21:45 DEBUG  WindowsBackend: windows_build=7600
06-09 21:45 DEBUG  WindowsBackend: gmt=5
06-09 21:45 DEBUG  WindowsBackend: country=US
06-09 21:45 DEBUG  WindowsBackend: timezone=America/New_York
06-09 21:45 DEBUG  WindowsBackend: windows_username=manu
06-09 21:45 DEBUG  WindowsBackend: user_full_name=manu
06-09 21:45 DEBUG  WindowsBackend: user_directory=C:\Users\manu
06-09 21:45 DEBUG  WindowsBackend: windows_language_code=1033
06-09 21:45 DEBUG  WindowsBackend: windows_language=English
06-09 21:45 DEBUG  WindowsBackend: processor_name=AMD A8-4500M APU with Radeon(tm) HD Graphics   
06-09 21:45 DEBUG  WindowsBackend: bootloader=vista
06-09 21:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62407.65625 mb free ntfs)
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(C: hd 62407.65625 mb free ntfs)
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(D: hd 2223.1171875 mb free ntfs)
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(E: hd 87.4541015625 mb free fat32)
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(U: hd 21409.59375 mb free ntfs)
06-09 21:45 DEBUG  WindowsBackend: drive=Drive(Z: hd 71843.6757813 mb free ntfs)
06-09 21:45 DEBUG  WindowsBackend: uninstaller_path=None
06-09 21:45 DEBUG  WindowsBackend: previous_target_dir=None
06-09 21:45 DEBUG  WindowsBackend: previous_distro_name=None
06-09 21:45 DEBUG  WindowsBackend: keyboard_id=67699721
06-09 21:45 DEBUG  WindowsBackend: keyboard_layout=us
06-09 21:45 DEBUG  WindowsBackend: keyboard_variant=
06-09 21:45 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-09 21:45 DEBUG  CommonBackend: locale=en_US.UTF-8
06-09 21:45 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
06-09 21:45 DEBUG  CommonBackend: Searching ISOs on USB devices
06-09 21:45 DEBUG  CommonBackend: Searching for local CDs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Kubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Mythbuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Edubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Lubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu Studio CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 INFO   root: Running the installer...
06-09 21:45 DEBUG  WindowsFrontend: __init__...
06-09 21:45 DEBUG  WindowsFrontend: on_init...
06-09 21:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\translations, languages=['en_US', 'en']
06-09 21:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\translations, languages=['en_US', 'en']
06-09 21:45 DEBUG  WinuiInstallationPage: target_drive=U:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=manu
06-09 21:45 INFO   root: Received settings
06-09 21:45 DEBUG  CommonBackend: Searching for local CD
06-09 21:45 DEBUG  Distro:   checking whether C:\Users\manu\AppData\Local\Temp\pyl785D.tmp is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether U:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain U:\casper\filesystem.squashfs
06-09 21:45 DEBUG  Distro:   checking whether Z:\ is a valid Ubuntu CD
06-09 21:45 DEBUG  Distro:     does not contain Z:\casper\filesystem.squashfs
06-09 21:45 DEBUG  CommonBackend: Searching for local ISO
06-09 21:45 DEBUG  Distro:   checking Ubuntu ISO Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 DEBUG  WindowsBackend:   extracting .disk\info from Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 DEBUG  Distro:   parsing info from str=Ubuntu 14.04 LTS "Trusty Tahr" - Release amd64 (20140417)
06-09 21:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140417', 'codename': 'Trusty Tahr', 'arch': 'amd64'}
06-09 21:45 INFO   Distro: Found a valid iso for Ubuntu: Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\translations, languages=['en_US', 'en']
06-09 21:45 DEBUG  TaskList: # Running tasklist...
06-09 21:45 DEBUG  TaskList: ## Running select_target_dir...
06-09 21:45 INFO   WindowsBackend: Installing into U:\ubuntu
06-09 21:45 DEBUG  TaskList: ## Finished select_target_dir
06-09 21:45 DEBUG  TaskList: ## Running create_dir_structure...
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\install
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\disks\boot\grub
06-09 21:45 DEBUG  CommonBackend: Creating dir U:\ubuntu\install\boot\grub
06-09 21:45 DEBUG  TaskList: ## Finished create_dir_structure
06-09 21:45 DEBUG  TaskList: ## Running uncompress_target_dir...
06-09 21:45 DEBUG  TaskList: ## Finished uncompress_target_dir
06-09 21:45 DEBUG  TaskList: ## Running create_uninstaller...
06-09 21:45 DEBUG  WindowsBackend: Copying uninstaller Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\wubi.exe -> U:\ubuntu\uninstall-wubi.exe
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString U:\ubuntu\uninstall-wubi.exe
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir U:\ubuntu
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon U:\ubuntu\Ubuntu.ico
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-09 21:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-09 21:45 DEBUG  TaskList: ## Finished create_uninstaller
06-09 21:45 DEBUG  TaskList: ## Running copy_installation_files...
06-09 21:45 DEBUG  WindowsBackend: Copying C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\data\custom-installation -> U:\ubuntu\install\custom-installation
06-09 21:45 DEBUG  WindowsBackend: Copying C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\winboot -> U:\ubuntu\winboot
06-09 21:45 DEBUG  WindowsBackend: Copying C:\Users\manu\AppData\Local\Temp\pyl785D.tmp\data\images\Ubuntu.ico -> U:\ubuntu\Ubuntu.ico
06-09 21:45 DEBUG  TaskList: ## Finished copy_installation_files
06-09 21:45 DEBUG  TaskList: ## Running get_iso...
06-09 21:45 DEBUG  CommonBackend: Trying to use ISO Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 DEBUG  TaskList: New task check_iso
06-09 21:45 DEBUG  TaskList: ### Running check_iso...
06-09 21:45 DEBUG  CommonBackend: Checking Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 DEBUG  Distro:   checking Ubuntu ISO Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 INFO   Distro: Found a valid iso for Ubuntu: Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso
06-09 21:45 DEBUG  TaskList: New task get_metalink
06-09 21:45 DEBUG  TaskList: #### Running get_metalink...
06-09 21:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink](http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink) > U:\ubuntu\install
06-09 21:45 DEBUG  downloader: Download start filename=U:\ubuntu\install\ubuntu-14.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink, basename=ubuntu-14.04-desktop-amd64.metalink, length=41450, text=None
06-09 21:45 DEBUG  downloader: download finished (read 41450 bytes)
06-09 21:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink](http://releases.ubuntu.com/14.04/MD5SUMS-metalink) > U:\ubuntu\install
06-09 21:45 DEBUG  downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=276, text=None
06-09 21:45 DEBUG  downloader: download finished (read 276 bytes)
06-09 21:45 DEBUG  downloader: downloading [http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg) > U:\ubuntu\install
06-09 21:45 DEBUG  downloader: Download start filename=U:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/14.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
06-09 21:45 DEBUG  downloader: download finished (read 198 bytes)
06-09 21:45 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-09 21:45 INFO   saplog: Checking block bindings..
06-09 21:45 INFO   saplog: Key verified successfully.
06-09 21:45 DEBUG  CommonBackend: metalink md5sums:
c7522c09a4beadfd0969c8338249f126 *ubuntu-14.04-desktop-amd64.metalink
96c7de9d1c56ddf7c0f43888ab9af575 *ubuntu-14.04-desktop-i386.metalink
ac3206dd1eb05205e193767314683520 *ubuntu-14.04-server-amd64.metalink
d1c27a6e4c3dfc5d9f5ef75e46d78ca6 *ubuntu-14.04-server-i386.metalink


06-09 21:45 ERROR  CommonBackend: The md5 of the metalink does match
06-09 21:45 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
06-09 21:45 DEBUG  TaskList: #### Finished get_metalink
06-09 21:45 DEBUG  TaskList: New task get_file_md5
06-09 21:45 DEBUG  TaskList: #### Running get_file_md5...
06-09 21:46 DEBUG  TaskList: #### Finished get_file_md5
06-09 21:46 DEBUG  TaskList: ### Finished check_iso
06-09 21:46 DEBUG  TaskList: New task copy_file
06-09 21:46 DEBUG  CommonBackend: Copying Z:\ashok data\soft\linux\linux\ubuntu\ubuntu-14.04-desktop-amd64\ubuntu-14.04-desktop-amd64.iso > U:\ubuntu\install\installation.iso
06-09 21:46 DEBUG  TaskList: ### Running copy_file...
06-09 21:46 DEBUG  TaskList: ### Finished copy_file
06-09 21:46 DEBUG  TaskList: ## Finished get_iso
06-09 21:46 DEBUG  TaskList: ## Running extract_kernel...
06-09 21:46 DEBUG  CommonBackend: Extracting files from ISO U:\ubuntu\install\installation.iso
06-09 21:46 DEBUG  WindowsBackend:   extracting md5sum.txt from U:\ubuntu\install\installation.iso
06-09 21:46 DEBUG  WindowsBackend:   extracting casper\vmlinuz.efi from U:\ubuntu\install\installation.iso
06-09 21:46 DEBUG  WindowsBackend:   extracting casper\initrd.lz from U:\ubuntu\install\installation.iso
06-09 21:46 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
06-09 21:46 DEBUG  CommonBackend:   checking U:\ubuntu\install\boot\vmlinuz.efi
06-09 21:46 DEBUG  CommonBackend:   U:\ubuntu\install\boot\vmlinuz.efi md5 = 3830553e4d2e1e040238a4317911d8ed == 3830553e4d2e1e040238a4317911d8ed
06-09 21:46 DEBUG  CommonBackend:   checking U:\ubuntu\install\boot\initrd.lz
06-09 21:46 DEBUG  CommonBackend:   U:\ubuntu\install\boot\initrd.lz md5 = add08a9be2fd6cb462f82a5b01810bb8 == add08a9be2fd6cb462f82a5b01810bb8
06-09 21:46 DEBUG  TaskList: ## Finished extract_kernel
06-09 21:46 DEBUG  TaskList: ## Running choose_disk_sizes...
06-09 21:46 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
06-09 21:46 DEBUG  TaskList: ## Finished choose_disk_sizes
06-09 21:46 DEBUG  TaskList: ## Running create_preseed...
06-09 21:46 DEBUG  TaskList: ## Finished create_preseed
06-09 21:46 DEBUG  TaskList: ## Running modify_bootloader...
06-09 21:46 DEBUG  TaskList: New task modify_bcd
06-09 21:46 DEBUG  TaskList: ### Running modify_bcd...
06-09 21:46 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 62407.65625 mb free ntfs)
06-09 21:46 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {aac947a8-8c57-11e3-92b9-c7ec9c899b34} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {aac947a8-8c57-11e3-92b9-c7ec9c899b34} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
06-09 21:46 DEBUG  TaskList: # Cancelling tasklist
06-09 21:46 DEBUG  TaskList: New task modify_bcd
06-09 21:46 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {aac947a8-8c57-11e3-92b9-c7ec9c899b34} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {aac947a8-8c57-11e3-92b9-c7ec9c899b34} device partition=U:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
06-09 21:46 DEBUG  TaskList: New task modify_bcd
06-09 21:46 DEBUG  TaskList: New task modify_bcd
06-09 21:46 DEBUG  TaskList: New task modify_bcd
06-09 21:46 DEBUG  TaskList: ## Finished modify_bootloader
06-09 21:46 DEBUG  TaskList: # Finished tasklist
```



[SIZE=5][ATTACH=CONFIG]253892[/ATTACH][/SIZE]

---

### Post by oldfred on 2014-06-11
Please use code tags on long terminal output. Easy to add with # icon in Advanced Editor.

Last supported version of wubi is 12.04. All new systems with UEFI use gpt partitioning and wubi does not work on gpt partitioning. 
Not many of us know wubi.

Most Windows 7 systems use all 4 primary partitions.
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

      
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

