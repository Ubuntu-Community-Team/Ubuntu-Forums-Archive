---
title: "Problem installing ubuntu 13.04 log file error &quot;sub string not found&quot;"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by akbarrkhan on 2013-10-08
```
10-08 21:54 INFO   root: === wubi 13.04 rev279 ===
10-08 21:54 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 21:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-13\\wubi.exe"']
10-08 21:54 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\data
10-08 21:54 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\bin\7z.exe
10-08 21:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 21:54 DEBUG  CommonBackend: Fetching basic info...
10-08 21:54 DEBUG  CommonBackend: original_exe=C:\ubuntu-13\wubi.exe
10-08 21:54 DEBUG  CommonBackend: platform=win32
10-08 21:54 DEBUG  CommonBackend: osname=nt
10-08 21:54 DEBUG  CommonBackend: language=en_US
10-08 21:54 DEBUG  CommonBackend: encoding=cp1252
10-08 21:54 DEBUG  WindowsBackend: arch=amd64
10-08 21:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\data\isolist.ini
10-08 21:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 21:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 21:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 21:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 21:54 DEBUG  WindowsBackend: Fetching host info...
10-08 21:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 21:54 DEBUG  WindowsBackend: windows version=vista
10-08 21:54 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 21:54 DEBUG  WindowsBackend: windows_sp=None
10-08 21:54 DEBUG  WindowsBackend: windows_build=9200
10-08 21:54 DEBUG  WindowsBackend: gmt=5
10-08 21:54 DEBUG  WindowsBackend: country=US
10-08 21:54 DEBUG  WindowsBackend: timezone=America/New_York
10-08 21:54 DEBUG  WindowsBackend: windows_username=iiui
10-08 21:54 DEBUG  WindowsBackend: user_full_name=iiui
10-08 21:54 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 21:54 DEBUG  WindowsBackend: windows_language_code=1033
10-08 21:54 DEBUG  WindowsBackend: windows_language=English
10-08 21:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 21:54 DEBUG  WindowsBackend: bootloader=vista
10-08 21:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90145.3984375 mb free ntfs)
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(C: hd 90145.3984375 mb free ntfs)
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(D: hd 145217.488281 mb free ntfs)
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 21:54 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 21:54 DEBUG  WindowsBackend: uninstaller_path=None
10-08 21:54 DEBUG  WindowsBackend: previous_target_dir=None
10-08 21:54 DEBUG  WindowsBackend: previous_distro_name=None
10-08 21:54 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 21:54 DEBUG  WindowsBackend: keyboard_layout=us
10-08 21:54 DEBUG  WindowsBackend: keyboard_variant=
10-08 21:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 21:54 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 21:54 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 21:54 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 21:54 DEBUG  CommonBackend: Searching for local CDs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 21:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:54 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-08 21:54 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 21:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 21:54 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-08 21:54 INFO   root: Running the installer...
10-08 21:54 DEBUG  WindowsFrontend: __init__...
10-08 21:54 DEBUG  WindowsFrontend: on_init...
10-08 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\translations, languages=['en_US', 'en']
10-08 21:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\translations, languages=['en_US', 'en']
10-08 21:55 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=iiui
10-08 21:55 INFO   root: Received settings
10-08 21:55 DEBUG  CommonBackend: Searching for local CD
10-08 21:55 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp is a valid Ubuntu CD
10-08 21:55 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\casper\filesystem.squashfs
10-08 21:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 21:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 21:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 21:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-08 21:55 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-08 21:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\translations, languages=['en_US', 'en']
10-08 21:55 DEBUG  TaskList: # Running tasklist...
10-08 21:55 DEBUG  TaskList: ## Running select_target_dir...
10-08 21:55 INFO   WindowsBackend: Installing into C:\ubuntu
10-08 21:55 DEBUG  TaskList: ## Finished select_target_dir
10-08 21:55 DEBUG  TaskList: ## Running create_dir_structure...
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-08 21:55 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-08 21:55 DEBUG  TaskList: ## Finished create_dir_structure
10-08 21:55 DEBUG  TaskList: ## Running uncompress_target_dir...
10-08 21:55 DEBUG  TaskList: ## Finished uncompress_target_dir
10-08 21:55 DEBUG  TaskList: ## Running create_uninstaller...
10-08 21:55 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-13\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-08 21:55 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-08 21:55 DEBUG  TaskList: ## Finished create_uninstaller
10-08 21:55 DEBUG  TaskList: ## Running copy_installation_files...
10-08 21:55 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-08 21:55 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\winboot -> C:\ubuntu\winboot
10-08 21:55 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl431F.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
10-08 21:55 DEBUG  TaskList: ## Finished copy_installation_files
10-08 21:55 DEBUG  TaskList: ## Running get_iso...
10-08 21:55 DEBUG  TaskList: New task copy_file
10-08 21:55 DEBUG  TaskList: ### Running copy_file...
10-08 21:55 DEBUG  TaskList: ### Finished copy_file
10-08 21:55 DEBUG  TaskList: New task check_iso
10-08 21:55 DEBUG  TaskList: ### Running check_iso...
10-08 21:55 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
10-08 21:55 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
10-08 21:55 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
10-08 21:55 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 21:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 21:55 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
10-08 21:55 DEBUG  TaskList: New task get_metalink
10-08 21:55 DEBUG  TaskList: #### Running get_metalink...
10-08 21:55 DEBUG  downloader: downloading [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink) > C:\ubuntu\install
10-08 21:55 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink](http://releases.ubuntu.com/13.04/ubuntu-13.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 21:55 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.metalink) > C:\ubuntu\install
10-08 21:55 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 21:55 DEBUG  TaskList: #### Finished get_metalink
10-08 21:55 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\ubuntu\install\installation.iso, ignoring
10-08 21:55 DEBUG  TaskList: ### Finished check_iso
10-08 21:55 DEBUG  TaskList: ## Finished get_iso
10-08 21:55 DEBUG  TaskList: ## Running extract_kernel...
10-08 21:55 DEBUG  CommonBackend: Copying files from CD H:\
10-08 21:55 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-08 21:55 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz.efi
10-08 21:55 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz.efi md5 = 1919b5acd184538ecb978f6361f98bf1 == 1919b5acd184538ecb978f6361f98bf1
10-08 21:55 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
10-08 21:55 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 1a2c7a01a1d5e6b788bf8266ab55bac9 == 1a2c7a01a1d5e6b788bf8266ab55bac9
10-08 21:55 DEBUG  TaskList: ## Finished extract_kernel
10-08 21:55 DEBUG  TaskList: ## Running choose_disk_sizes...
10-08 21:55 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-08 21:55 DEBUG  TaskList: ## Finished choose_disk_sizes
10-08 21:55 DEBUG  TaskList: ## Running create_preseed...
10-08 21:55 DEBUG  TaskList: ## Finished create_preseed
10-08 21:55 DEBUG  TaskList: ## Running modify_bootloader...
10-08 21:55 DEBUG  TaskList: New task modify_bcd
10-08 21:55 DEBUG  TaskList: ### Running modify_bcd...
10-08 21:55 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 90145.3984375 mb free ntfs)
10-08 21:55 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 21:55 DEBUG  TaskList: # Cancelling tasklist
10-08 21:55 DEBUG  TaskList: New task modify_bcd
10-08 21:55 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 21:55 DEBUG  TaskList: New task modify_bcd
10-08 21:55 DEBUG  TaskList: New task modify_bcd
10-08 21:55 DEBUG  TaskList: ## Finished modify_bootloader
10-08 21:55 DEBUG  TaskList: # Finished tasklist
10-08 21:57 INFO   root: === wubi 13.04 rev279 ===
10-08 21:57 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 21:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-08 21:57 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\data
10-08 21:57 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\bin\7z.exe
10-08 21:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 21:57 DEBUG  CommonBackend: Fetching basic info...
10-08 21:57 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-08 21:57 DEBUG  CommonBackend: platform=win32
10-08 21:57 DEBUG  CommonBackend: osname=nt
10-08 21:57 DEBUG  CommonBackend: language=en_US
10-08 21:57 DEBUG  CommonBackend: encoding=cp1252
10-08 21:57 DEBUG  WindowsBackend: arch=amd64
10-08 21:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\data\isolist.ini
10-08 21:57 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 21:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 21:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 21:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 21:57 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 21:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 21:57 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 21:57 DEBUG  WindowsBackend: Fetching host info...
10-08 21:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 21:57 DEBUG  WindowsBackend: windows version=vista
10-08 21:57 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 21:57 DEBUG  WindowsBackend: windows_sp=None
10-08 21:57 DEBUG  WindowsBackend: windows_build=9200
10-08 21:57 DEBUG  WindowsBackend: gmt=5
10-08 21:57 DEBUG  WindowsBackend: country=US
10-08 21:57 DEBUG  WindowsBackend: timezone=America/New_York
10-08 21:57 DEBUG  WindowsBackend: windows_username=iiui
10-08 21:57 DEBUG  WindowsBackend: user_full_name=iiui
10-08 21:57 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 21:57 DEBUG  WindowsBackend: windows_language_code=1033
10-08 21:57 DEBUG  WindowsBackend: windows_language=English
10-08 21:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 21:57 DEBUG  WindowsBackend: bootloader=vista
10-08 21:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 89326.8125 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(C: hd 89326.8125 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(D: hd 145217.488281 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(G: removable 4879.12890625 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 21:57 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 21:57 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-08 21:57 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-08 21:57 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
10-08 21:57 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 21:57 DEBUG  WindowsBackend: keyboard_layout=us
10-08 21:57 DEBUG  WindowsBackend: keyboard_variant=
10-08 21:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 21:57 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 21:57 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 21:57 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 21:57 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 21:57 DEBUG  Distro:     does not contain casper\vmlinuz.efi
10-08 21:57 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 21:57 DEBUG  WindowsBackend:   extracting .disk\info from G:\kubuntu-13.04-desktop-amd64.iso
10-08 21:57 DEBUG  Distro:   parsing info from str=Kubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 21:57 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 21:57 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-08 21:57 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 21:57 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 21:57 DEBUG  CommonBackend: Searching for local CDs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylC814.tmp is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 21:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 21:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 21:57 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 21:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 21:57 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-08 21:57 INFO   root: Running the uninstaller...
10-08 21:57 INFO   CommonBackend: This is the uninstaller running
10-08 21:57 DEBUG  WindowsFrontend: __init__...
10-08 21:57 DEBUG  WindowsFrontend: on_init...
10-08 21:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\translations, languages=['en_US', 'en']
10-08 21:57 INFO   root: Received settings
10-08 21:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\translations, languages=['en_US', 'en']
10-08 21:57 DEBUG  TaskList: # Running tasklist...
10-08 21:57 DEBUG  TaskList: ## Running Remove bootloader entry...
10-08 21:57 DEBUG  WindowsBackend: Could not find bcd id
10-08 21:57 DEBUG  WindowsBackend: undo_bootini C:
10-08 21:57 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 89326.8125 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: undo_bootini D:
10-08 21:57 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 145217.488281 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: undo_bootini E:
10-08 21:57 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 169251.5625 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: undo_bootini G:
10-08 21:57 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 4879.12890625 mb free ntfs)
10-08 21:57 DEBUG  WindowsBackend: undo_bootini I:
10-08 21:57 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-08 21:57 DEBUG  TaskList: ## Finished Remove bootloader entry
10-08 21:57 DEBUG  TaskList: ## Running Remove target dir...
10-08 21:57 DEBUG  CommonBackend: Deleting C:\ubuntu
10-08 21:57 DEBUG  TaskList: ## Finished Remove target dir
10-08 21:57 DEBUG  TaskList: ## Running Remove registry key...
10-08 21:57 DEBUG  TaskList: ## Finished Remove registry key
10-08 21:57 DEBUG  TaskList: # Finished tasklist
10-08 21:57 INFO   root: Almost finished uninstalling
10-08 21:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylC814.tmp\translations, languages=['en_US', 'en']
10-08 21:57 INFO   root: Finished uninstallation
10-08 21:57 DEBUG  root: application.quit
10-08 21:57 DEBUG  WindowsFrontend: frontend.quit
10-08 21:57 DEBUG  WindowsFrontend: frontend.on_quit
10-08 21:57 DEBUG  root: application.on_quit
10-08 21:57 INFO   root: sys.exit
10-08 22:02 INFO   root: === wubi 13.04 rev279 ===
10-08 22:02 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 22:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-13.04-desktop-amd64\\wubi.exe"']
10-08 22:02 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\data
10-08 22:02 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\bin\7z.exe
10-08 22:02 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 22:02 DEBUG  CommonBackend: Fetching basic info...
10-08 22:02 DEBUG  CommonBackend: original_exe=C:\ubuntu-13.04-desktop-amd64\wubi.exe
10-08 22:02 DEBUG  CommonBackend: platform=win32
10-08 22:02 DEBUG  CommonBackend: osname=nt
10-08 22:02 DEBUG  CommonBackend: language=en_US
10-08 22:02 DEBUG  CommonBackend: encoding=cp1252
10-08 22:02 DEBUG  WindowsBackend: arch=amd64
10-08 22:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\data\isolist.ini
10-08 22:02 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 22:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 22:02 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 22:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 22:02 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 22:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 22:02 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 22:02 DEBUG  WindowsBackend: Fetching host info...
10-08 22:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 22:02 DEBUG  WindowsBackend: windows version=vista
10-08 22:02 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 22:02 DEBUG  WindowsBackend: windows_sp=None
10-08 22:02 DEBUG  WindowsBackend: windows_build=9200
10-08 22:02 DEBUG  WindowsBackend: gmt=5
10-08 22:02 DEBUG  WindowsBackend: country=US
10-08 22:02 DEBUG  WindowsBackend: timezone=America/New_York
10-08 22:02 DEBUG  WindowsBackend: windows_username=iiui
10-08 22:02 DEBUG  WindowsBackend: user_full_name=iiui
10-08 22:02 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 22:02 DEBUG  WindowsBackend: windows_language_code=1033
10-08 22:02 DEBUG  WindowsBackend: windows_language=English
10-08 22:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 22:02 DEBUG  WindowsBackend: bootloader=vista
10-08 22:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87795.7421875 mb free ntfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(C: hd 87795.7421875 mb free ntfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(D: hd 145217.488281 mb free ntfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(G: removable 4879.12890625 mb free ntfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 22:02 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 22:02 DEBUG  WindowsBackend: uninstaller_path=None
10-08 22:02 DEBUG  WindowsBackend: previous_target_dir=None
10-08 22:02 DEBUG  WindowsBackend: previous_distro_name=None
10-08 22:02 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 22:02 DEBUG  WindowsBackend: keyboard_layout=us
10-08 22:02 DEBUG  WindowsBackend: keyboard_variant=
10-08 22:02 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 22:02 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 22:02 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 22:02 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 22:02 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  Distro:     does not contain casper\vmlinuz.efi
10-08 22:02 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  WindowsBackend:   extracting .disk\info from G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  Distro:   parsing info from str=Kubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:02 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:02 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-08 22:02 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  CommonBackend: Searching for local CDs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:02 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:02 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-08 22:02 INFO   root: Running the installer...
10-08 22:02 DEBUG  WindowsFrontend: __init__...
10-08 22:02 DEBUG  WindowsFrontend: on_init...
10-08 22:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\translations, languages=['en_US', 'en']
10-08 22:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\translations, languages=['en_US', 'en']
10-08 22:02 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=iiui
10-08 22:02 INFO   root: Received settings
10-08 22:02 DEBUG  CommonBackend: Searching for local CD
10-08 22:02 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain G:\casper\vmlinuz
10-08 22:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain H:\casper\vmlinuz
10-08 22:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-08 22:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-08 22:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\translations, languages=['en_US', 'en']
10-08 22:02 DEBUG  TaskList: # Running tasklist...
10-08 22:02 DEBUG  TaskList: ## Running select_target_dir...
10-08 22:02 INFO   WindowsBackend: Installing into C:\ubuntu
10-08 22:02 DEBUG  TaskList: ## Finished select_target_dir
10-08 22:02 DEBUG  TaskList: ## Running create_dir_structure...
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-08 22:02 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-08 22:02 DEBUG  TaskList: ## Finished create_dir_structure
10-08 22:02 DEBUG  TaskList: ## Running uncompress_target_dir...
10-08 22:02 DEBUG  TaskList: ## Finished uncompress_target_dir
10-08 22:02 DEBUG  TaskList: ## Running create_uninstaller...
10-08 22:02 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-13.04-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
10-08 22:02 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-08 22:02 DEBUG  TaskList: ## Finished create_uninstaller
10-08 22:02 DEBUG  TaskList: ## Running copy_installation_files...
10-08 22:02 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-08 22:02 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\winboot -> C:\ubuntu\winboot
10-08 22:02 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pyl1585.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
10-08 22:02 DEBUG  TaskList: ## Finished copy_installation_files
10-08 22:02 DEBUG  TaskList: ## Running get_iso...
10-08 22:02 DEBUG  CommonBackend: Trying to use pre-specified ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  TaskList: New task is_valid_iso
10-08 22:02 DEBUG  TaskList: ### Running is_valid_iso...
10-08 22:02 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  TaskList: ### Finished is_valid_iso
10-08 22:02 DEBUG  TaskList: New task check_iso
10-08 22:02 DEBUG  TaskList: ### Running check_iso...
10-08 22:02 DEBUG  CommonBackend: Checking G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:02 DEBUG  TaskList: New task get_metalink
10-08 22:02 DEBUG  TaskList: #### Running get_metalink...
10-08 22:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) > C:\ubuntu\install
10-08 22:02 ERROR  CommonBackend: Cannot download metalink file [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) > C:\ubuntu\install
10-08 22:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:02 DEBUG  TaskList: #### Finished get_metalink
10-08 22:02 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\kubuntu-13.04-desktop-amd64.iso, ignoring
10-08 22:02 DEBUG  TaskList: ### Finished check_iso
10-08 22:02 DEBUG  TaskList: New task copy_file
10-08 22:02 DEBUG  CommonBackend: Copying G:\kubuntu-13.04-desktop-amd64.iso > C:\ubuntu\install\installation.iso
10-08 22:02 DEBUG  TaskList: ### Running copy_file...
10-08 22:03 DEBUG  TaskList: ### Finished copy_file
10-08 22:03 DEBUG  TaskList: ## Finished get_iso
10-08 22:03 DEBUG  TaskList: ## Running extract_kernel...
10-08 22:03 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
10-08 22:03 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
10-08 22:03 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
10-08 22:03 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
10-08 22:03 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-08 22:03 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
10-08 22:03 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = deacc3c3a21beb4913c43a00bb6d5e01 == deacc3c3a21beb4913c43a00bb6d5e01
10-08 22:03 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
10-08 22:03 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = ff0212a8cdbaecde3326ce9c032d4a75 == ff0212a8cdbaecde3326ce9c032d4a75
10-08 22:03 DEBUG  TaskList: ## Finished extract_kernel
10-08 22:03 DEBUG  TaskList: ## Running choose_disk_sizes...
10-08 22:03 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-08 22:03 DEBUG  TaskList: ## Finished choose_disk_sizes
10-08 22:03 DEBUG  TaskList: ## Running create_preseed...
10-08 22:03 DEBUG  TaskList: ## Finished create_preseed
10-08 22:03 DEBUG  TaskList: ## Running modify_bootloader...
10-08 22:03 DEBUG  TaskList: New task modify_bcd
10-08 22:03 DEBUG  TaskList: ### Running modify_bcd...
10-08 22:03 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 87795.7421875 mb free ntfs)
10-08 22:03 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:03 DEBUG  TaskList: # Cancelling tasklist
10-08 22:03 DEBUG  TaskList: New task modify_bcd
10-08 22:03 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:03 DEBUG  TaskList: New task modify_bcd
10-08 22:03 DEBUG  TaskList: New task modify_bcd
10-08 22:03 DEBUG  TaskList: New task modify_bcd
10-08 22:03 DEBUG  TaskList: ## Finished modify_bootloader
10-08 22:03 DEBUG  TaskList: # Finished tasklist
10-08 22:03 INFO   root: === wubi 13.04 rev279 ===
10-08 22:03 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 22:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
10-08 22:03 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\data
10-08 22:03 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\bin\7z.exe
10-08 22:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 22:03 DEBUG  CommonBackend: Fetching basic info...
10-08 22:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
10-08 22:03 DEBUG  CommonBackend: platform=win32
10-08 22:03 DEBUG  CommonBackend: osname=nt
10-08 22:03 DEBUG  CommonBackend: language=en_US
10-08 22:03 DEBUG  CommonBackend: encoding=cp1252
10-08 22:03 DEBUG  WindowsBackend: arch=amd64
10-08 22:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\data\isolist.ini
10-08 22:03 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 22:03 DEBUG  WindowsBackend: Fetching host info...
10-08 22:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 22:03 DEBUG  WindowsBackend: windows version=vista
10-08 22:03 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 22:03 DEBUG  WindowsBackend: windows_sp=None
10-08 22:03 DEBUG  WindowsBackend: windows_build=9200
10-08 22:03 DEBUG  WindowsBackend: gmt=5
10-08 22:03 DEBUG  WindowsBackend: country=US
10-08 22:03 DEBUG  WindowsBackend: timezone=America/New_York
10-08 22:03 DEBUG  WindowsBackend: windows_username=iiui
10-08 22:03 DEBUG  WindowsBackend: user_full_name=iiui
10-08 22:03 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 22:03 DEBUG  WindowsBackend: windows_language_code=1033
10-08 22:03 DEBUG  WindowsBackend: windows_language=English
10-08 22:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 22:03 DEBUG  WindowsBackend: bootloader=vista
10-08 22:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 86837.3671875 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(C: hd 86837.3671875 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(D: hd 145217.488281 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(G: removable 4879.12890625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 22:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
10-08 22:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
10-08 22:03 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
10-08 22:03 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 22:03 DEBUG  WindowsBackend: keyboard_layout=us
10-08 22:03 DEBUG  WindowsBackend: keyboard_variant=
10-08 22:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 22:03 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 22:03 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 22:03 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 22:03 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  Distro:     does not contain casper\vmlinuz.efi
10-08 22:03 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  WindowsBackend:   extracting .disk\info from G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  Distro:   parsing info from str=Kubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:03 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:03 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-08 22:03 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  CommonBackend: Searching for local CDs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:03 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-08 22:03 INFO   root: Running the uninstaller...
10-08 22:03 INFO   CommonBackend: This is the uninstaller running
10-08 22:03 DEBUG  WindowsFrontend: __init__...
10-08 22:03 DEBUG  WindowsFrontend: on_init...
10-08 22:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\translations, languages=['en_US', 'en']
10-08 22:03 INFO   root: Received settings
10-08 22:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\translations, languages=['en_US', 'en']
10-08 22:03 DEBUG  TaskList: # Running tasklist...
10-08 22:03 DEBUG  TaskList: ## Running Remove bootloader entry...
10-08 22:03 DEBUG  WindowsBackend: Could not find bcd id
10-08 22:03 DEBUG  WindowsBackend: undo_bootini C:
10-08 22:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 86837.3671875 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: undo_bootini D:
10-08 22:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 145217.488281 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: undo_bootini E:
10-08 22:03 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: undo_bootini G:
10-08 22:03 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 4879.12890625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: undo_bootini I:
10-08 22:03 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-08 22:03 DEBUG  TaskList: ## Finished Remove bootloader entry
10-08 22:03 DEBUG  TaskList: ## Running Remove target dir...
10-08 22:03 DEBUG  CommonBackend: Deleting C:\ubuntu
10-08 22:03 DEBUG  TaskList: ## Finished Remove target dir
10-08 22:03 DEBUG  TaskList: ## Running Remove registry key...
10-08 22:03 DEBUG  TaskList: ## Finished Remove registry key
10-08 22:03 DEBUG  TaskList: # Finished tasklist
10-08 22:03 INFO   root: Almost finished uninstalling
10-08 22:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl8939.tmp\translations, languages=['en_US', 'en']
10-08 22:03 INFO   root: Finished uninstallation
10-08 22:03 DEBUG  root: application.quit
10-08 22:03 DEBUG  WindowsFrontend: frontend.quit
10-08 22:03 DEBUG  WindowsFrontend: frontend.on_quit
10-08 22:03 DEBUG  root: application.on_quit
10-08 22:03 INFO   root: sys.exit
10-08 22:03 INFO   root: === wubi 13.04 rev279 ===
10-08 22:03 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 22:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu-13.04-desktop-amd64\\wubi.exe"']
10-08 22:03 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\data
10-08 22:03 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\bin\7z.exe
10-08 22:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 22:03 DEBUG  CommonBackend: Fetching basic info...
10-08 22:03 DEBUG  CommonBackend: original_exe=C:\ubuntu-13.04-desktop-amd64\wubi.exe
10-08 22:03 DEBUG  CommonBackend: platform=win32
10-08 22:03 DEBUG  CommonBackend: osname=nt
10-08 22:03 DEBUG  CommonBackend: language=en_US
10-08 22:03 DEBUG  CommonBackend: encoding=cp1252
10-08 22:03 DEBUG  WindowsBackend: arch=amd64
10-08 22:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\data\isolist.ini
10-08 22:03 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 22:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 22:03 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 22:03 DEBUG  WindowsBackend: Fetching host info...
10-08 22:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 22:03 DEBUG  WindowsBackend: windows version=vista
10-08 22:03 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 22:03 DEBUG  WindowsBackend: windows_sp=None
10-08 22:03 DEBUG  WindowsBackend: windows_build=9200
10-08 22:03 DEBUG  WindowsBackend: gmt=5
10-08 22:03 DEBUG  WindowsBackend: country=US
10-08 22:03 DEBUG  WindowsBackend: timezone=America/New_York
10-08 22:03 DEBUG  WindowsBackend: windows_username=iiui
10-08 22:03 DEBUG  WindowsBackend: user_full_name=iiui
10-08 22:03 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 22:03 DEBUG  WindowsBackend: windows_language_code=1033
10-08 22:03 DEBUG  WindowsBackend: windows_language=English
10-08 22:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 22:03 DEBUG  WindowsBackend: bootloader=vista
10-08 22:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 87794.4492188 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(C: hd 87794.4492188 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(D: hd 145217.488281 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(G: removable 4879.12890625 mb free ntfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 22:03 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 22:03 DEBUG  WindowsBackend: uninstaller_path=None
10-08 22:03 DEBUG  WindowsBackend: previous_target_dir=None
10-08 22:03 DEBUG  WindowsBackend: previous_distro_name=None
10-08 22:03 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 22:03 DEBUG  WindowsBackend: keyboard_layout=us
10-08 22:03 DEBUG  WindowsBackend: keyboard_variant=
10-08 22:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 22:03 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 22:03 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 22:03 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 22:03 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  Distro:     does not contain casper\vmlinuz.efi
10-08 22:03 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  WindowsBackend:   extracting .disk\info from G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  Distro:   parsing info from str=Kubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:03 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:03 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-08 22:03 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:03 DEBUG  CommonBackend: Searching for local CDs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:03 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:03 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:03 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-08 22:03 INFO   root: Running the installer...
10-08 22:03 DEBUG  WindowsFrontend: __init__...
10-08 22:03 DEBUG  WindowsFrontend: on_init...
10-08 22:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\translations, languages=['en_US', 'en']
10-08 22:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\translations, languages=['en_US', 'en']
10-08 22:04 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=iiui
10-08 22:04 INFO   root: Received settings
10-08 22:04 DEBUG  CommonBackend: Searching for local CD
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\vmlinuz
10-08 22:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain H:\casper\vmlinuz
10-08 22:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-08 22:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\translations, languages=['en_US', 'en']
10-08 22:04 DEBUG  TaskList: # Running tasklist...
10-08 22:04 DEBUG  TaskList: ## Running select_target_dir...
10-08 22:04 INFO   WindowsBackend: Installing into D:\ubuntu
10-08 22:04 DEBUG  TaskList: ## Finished select_target_dir
10-08 22:04 DEBUG  TaskList: ## Running create_dir_structure...
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
10-08 22:04 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
10-08 22:04 DEBUG  TaskList: ## Finished create_dir_structure
10-08 22:04 DEBUG  TaskList: ## Running uncompress_target_dir...
10-08 22:04 DEBUG  TaskList: ## Finished uncompress_target_dir
10-08 22:04 DEBUG  TaskList: ## Running create_uninstaller...
10-08 22:04 DEBUG  WindowsBackend: Copying uninstaller C:\ubuntu-13.04-desktop-amd64\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Kubuntu.ico
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
10-08 22:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-08 22:04 DEBUG  TaskList: ## Finished create_uninstaller
10-08 22:04 DEBUG  TaskList: ## Running copy_installation_files...
10-08 22:04 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
10-08 22:04 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\winboot -> D:\ubuntu\winboot
10-08 22:04 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylCAB7.tmp\data\images\Kubuntu.ico -> D:\ubuntu\Kubuntu.ico
10-08 22:04 DEBUG  TaskList: ## Finished copy_installation_files
10-08 22:04 DEBUG  TaskList: ## Running get_iso...
10-08 22:04 DEBUG  CommonBackend: Trying to use pre-specified ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 DEBUG  TaskList: New task is_valid_iso
10-08 22:04 DEBUG  TaskList: ### Running is_valid_iso...
10-08 22:04 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 DEBUG  TaskList: ### Finished is_valid_iso
10-08 22:04 DEBUG  TaskList: New task check_iso
10-08 22:04 DEBUG  TaskList: ### Running check_iso...
10-08 22:04 DEBUG  CommonBackend: Checking G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:04 DEBUG  TaskList: New task get_metalink
10-08 22:04 DEBUG  TaskList: #### Running get_metalink...
10-08 22:04 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) > D:\ubuntu\install
10-08 22:04 ERROR  CommonBackend: Cannot download metalink file [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:04 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) > D:\ubuntu\install
10-08 22:04 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:04 DEBUG  TaskList: #### Finished get_metalink
10-08 22:04 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\kubuntu-13.04-desktop-amd64.iso, ignoring
10-08 22:04 DEBUG  TaskList: ### Finished check_iso
10-08 22:04 DEBUG  TaskList: New task copy_file
10-08 22:04 DEBUG  CommonBackend: Copying G:\kubuntu-13.04-desktop-amd64.iso > D:\ubuntu\install\installation.iso
10-08 22:04 DEBUG  TaskList: ### Running copy_file...
10-08 22:04 DEBUG  TaskList: ### Finished copy_file
10-08 22:04 DEBUG  TaskList: ## Finished get_iso
10-08 22:04 DEBUG  TaskList: ## Running extract_kernel...
10-08 22:04 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\installation.iso
10-08 22:04 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\installation.iso
10-08 22:04 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\installation.iso
10-08 22:04 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\installation.iso
10-08 22:04 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-08 22:04 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
10-08 22:04 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = deacc3c3a21beb4913c43a00bb6d5e01 == deacc3c3a21beb4913c43a00bb6d5e01
10-08 22:04 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
10-08 22:04 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = ff0212a8cdbaecde3326ce9c032d4a75 == ff0212a8cdbaecde3326ce9c032d4a75
10-08 22:04 DEBUG  TaskList: ## Finished extract_kernel
10-08 22:04 DEBUG  TaskList: ## Running choose_disk_sizes...
10-08 22:04 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-08 22:04 DEBUG  TaskList: ## Finished choose_disk_sizes
10-08 22:04 DEBUG  TaskList: ## Running create_preseed...
10-08 22:04 DEBUG  TaskList: ## Finished create_preseed
10-08 22:04 DEBUG  TaskList: ## Running modify_bootloader...
10-08 22:04 DEBUG  TaskList: New task modify_bcd
10-08 22:04 DEBUG  TaskList: ### Running modify_bcd...
10-08 22:04 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 87794.4492188 mb free ntfs)
10-08 22:04 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:04 DEBUG  TaskList: # Cancelling tasklist
10-08 22:04 DEBUG  TaskList: New task modify_bcd
10-08 22:04 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:04 DEBUG  TaskList: New task modify_bcd
10-08 22:04 DEBUG  TaskList: New task modify_bcd
10-08 22:04 DEBUG  TaskList: New task modify_bcd
10-08 22:04 DEBUG  TaskList: ## Finished modify_bootloader
10-08 22:04 DEBUG  TaskList: # Finished tasklist
10-08 22:04 INFO   root: === wubi 13.04 rev279 ===
10-08 22:04 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 22:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
10-08 22:04 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\data
10-08 22:04 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\bin\7z.exe
10-08 22:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 22:04 DEBUG  CommonBackend: Fetching basic info...
10-08 22:04 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
10-08 22:04 DEBUG  CommonBackend: platform=win32
10-08 22:04 DEBUG  CommonBackend: osname=nt
10-08 22:04 DEBUG  CommonBackend: language=en_US
10-08 22:04 DEBUG  CommonBackend: encoding=cp1252
10-08 22:04 DEBUG  WindowsBackend: arch=amd64
10-08 22:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\data\isolist.ini
10-08 22:04 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 22:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 22:04 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 22:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 22:04 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 22:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 22:04 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 22:04 DEBUG  WindowsBackend: Fetching host info...
10-08 22:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 22:04 DEBUG  WindowsBackend: windows version=vista
10-08 22:04 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 22:04 DEBUG  WindowsBackend: windows_sp=None
10-08 22:04 DEBUG  WindowsBackend: windows_build=9200
10-08 22:04 DEBUG  WindowsBackend: gmt=5
10-08 22:04 DEBUG  WindowsBackend: country=US
10-08 22:04 DEBUG  WindowsBackend: timezone=America/New_York
10-08 22:04 DEBUG  WindowsBackend: windows_username=iiui
10-08 22:04 DEBUG  WindowsBackend: user_full_name=iiui
10-08 22:04 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 22:04 DEBUG  WindowsBackend: windows_language_code=1033
10-08 22:04 DEBUG  WindowsBackend: windows_language=English
10-08 22:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 22:04 DEBUG  WindowsBackend: bootloader=vista
10-08 22:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 89361.8515625 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(C: hd 89361.8515625 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(D: hd 144260.457031 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(G: removable 10234.9179688 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 22:04 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 22:04 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
10-08 22:04 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
10-08 22:04 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
10-08 22:04 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 22:04 DEBUG  WindowsBackend: keyboard_layout=us
10-08 22:04 DEBUG  WindowsBackend: keyboard_variant=
10-08 22:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 22:04 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 22:04 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 22:04 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 22:04 DEBUG  CommonBackend: Searching for local CDs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
10-08 22:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
10-08 22:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
10-08 22:04 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:04 INFO   Distro: Found a valid CD for Ubuntu: H:\
10-08 22:04 INFO   root: Running the uninstaller...
10-08 22:04 INFO   CommonBackend: This is the uninstaller running
10-08 22:04 DEBUG  WindowsFrontend: __init__...
10-08 22:04 DEBUG  WindowsFrontend: on_init...
10-08 22:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\translations, languages=['en_US', 'en']
10-08 22:04 INFO   root: Received settings
10-08 22:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\translations, languages=['en_US', 'en']
10-08 22:04 DEBUG  TaskList: # Running tasklist...
10-08 22:04 DEBUG  TaskList: ## Running Remove bootloader entry...
10-08 22:04 DEBUG  WindowsBackend: Could not find bcd id
10-08 22:04 DEBUG  WindowsBackend: undo_bootini C:
10-08 22:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 89361.8515625 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: undo_bootini D:
10-08 22:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 144260.457031 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: undo_bootini E:
10-08 22:04 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: undo_bootini G:
10-08 22:04 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 10234.9179688 mb free ntfs)
10-08 22:04 DEBUG  WindowsBackend: undo_bootini I:
10-08 22:04 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
10-08 22:04 DEBUG  TaskList: ## Finished Remove bootloader entry
10-08 22:04 DEBUG  TaskList: ## Running Remove target dir...
10-08 22:04 DEBUG  CommonBackend: Deleting D:\ubuntu
10-08 22:04 DEBUG  TaskList: ## Finished Remove target dir
10-08 22:04 DEBUG  TaskList: ## Running Remove registry key...
10-08 22:04 DEBUG  TaskList: ## Finished Remove registry key
10-08 22:04 DEBUG  TaskList: # Finished tasklist
10-08 22:04 INFO   root: Almost finished uninstalling
10-08 22:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pyl7946.tmp\translations, languages=['en_US', 'en']
10-08 22:04 INFO   root: Finished uninstallation
10-08 22:04 DEBUG  root: application.quit
10-08 22:04 DEBUG  WindowsFrontend: frontend.quit
10-08 22:04 DEBUG  WindowsFrontend: frontend.on_quit
10-08 22:04 DEBUG  root: application.on_quit
10-08 22:04 INFO   root: sys.exit
10-08 22:12 INFO   root: === wubi 13.04 rev279 ===
10-08 22:12 DEBUG  root: Logfile is c:\users\iiui\appdata\local\temp\wubi-13.04-rev279.log
10-08 22:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu-13.04-desktop-amd64\\wubi.exe"']
10-08 22:12 DEBUG  CommonBackend: data_dir=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\data
10-08 22:12 DEBUG  WindowsBackend: 7z=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\bin\7z.exe
10-08 22:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
10-08 22:12 DEBUG  CommonBackend: Fetching basic info...
10-08 22:12 DEBUG  CommonBackend: original_exe=D:\ubuntu-13.04-desktop-amd64\wubi.exe
10-08 22:12 DEBUG  CommonBackend: platform=win32
10-08 22:12 DEBUG  CommonBackend: osname=nt
10-08 22:12 DEBUG  CommonBackend: language=en_US
10-08 22:12 DEBUG  CommonBackend: encoding=cp1252
10-08 22:12 DEBUG  WindowsBackend: arch=amd64
10-08 22:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\data\isolist.ini
10-08 22:12 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-08 22:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
10-08 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
10-08 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-08 22:12 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-08 22:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
10-08 22:12 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
10-08 22:12 DEBUG  WindowsBackend: Fetching host info...
10-08 22:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-08 22:12 DEBUG  WindowsBackend: windows version=vista
10-08 22:12 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
10-08 22:12 DEBUG  WindowsBackend: windows_sp=None
10-08 22:12 DEBUG  WindowsBackend: windows_build=9200
10-08 22:12 DEBUG  WindowsBackend: gmt=5
10-08 22:12 DEBUG  WindowsBackend: country=US
10-08 22:12 DEBUG  WindowsBackend: timezone=America/New_York
10-08 22:12 DEBUG  WindowsBackend: windows_username=iiui
10-08 22:12 DEBUG  WindowsBackend: user_full_name=iiui
10-08 22:12 DEBUG  WindowsBackend: user_directory=C:\Users\iiui
10-08 22:12 DEBUG  WindowsBackend: windows_language_code=1033
10-08 22:12 DEBUG  WindowsBackend: windows_language=English
10-08 22:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2670QM CPU @ 2.20GHz
10-08 22:12 DEBUG  WindowsBackend: bootloader=vista
10-08 22:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90058.1328125 mb free ntfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(C: hd 90058.1328125 mb free ntfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(D: hd 143648.507813 mb free ntfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(E: hd 169251.5625 mb free ntfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(G: removable 4879.12890625 mb free ntfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free cdfs)
10-08 22:12 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
10-08 22:12 DEBUG  WindowsBackend: uninstaller_path=None
10-08 22:12 DEBUG  WindowsBackend: previous_target_dir=None
10-08 22:12 DEBUG  WindowsBackend: previous_distro_name=None
10-08 22:12 DEBUG  WindowsBackend: keyboard_id=67699721
10-08 22:12 DEBUG  WindowsBackend: keyboard_layout=us
10-08 22:12 DEBUG  WindowsBackend: keyboard_variant=
10-08 22:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
10-08 22:12 DEBUG  CommonBackend: locale=en_US.UTF-8
10-08 22:12 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
10-08 22:12 DEBUG  CommonBackend: Searching ISOs on USB devices
10-08 22:12 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:12 DEBUG  Distro:     does not contain casper\vmlinuz.efi
10-08 22:12 DEBUG  Distro:   checking Ubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:12 DEBUG  WindowsBackend:   extracting .disk\info from G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:12 DEBUG  Distro:   parsing info from str=Kubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:12 DEBUG  Distro:   parsed info={'name': 'Kubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:12 DEBUG  Distro: wrong name: Kubuntu != Ubuntu
10-08 22:12 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:12 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:12 DEBUG  CommonBackend: Searching for local CDs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
10-08 22:12 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:12 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
10-08 22:12 DEBUG  Distro:   parsing info from str=Ubuntu 13.04 "Raring Ringtail" - Release amd64 (20130424)
10-08 22:12 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '13.04', 'build': '20130424', 'codename': 'Raring Ringtail', 'arch': 'amd64'}
10-08 22:12 INFO   Distro: Found a valid CD for Ubuntu: G:\
10-08 22:12 INFO   root: Running the installer...
10-08 22:12 DEBUG  WindowsFrontend: __init__...
10-08 22:12 DEBUG  WindowsFrontend: on_init...
10-08 22:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\translations, languages=['en_US', 'en']
10-08 22:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\translations, languages=['en_US', 'en']
10-08 22:13 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=iiui
10-08 22:13 INFO   root: Received settings
10-08 22:13 DEBUG  CommonBackend: Searching for local CD
10-08 22:13 DEBUG  Distro:   checking whether C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\casper\filesystem.squashfs
10-08 22:13 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
10-08 22:13 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
10-08 22:13 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
10-08 22:13 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain G:\casper\vmlinuz
10-08 22:13 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain H:\casper\vmlinuz
10-08 22:13 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
10-08 22:13 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
10-08 22:13 INFO   WinuiPage: appname=wubi, localedir=C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\translations, languages=['en_US', 'en']
10-08 22:13 DEBUG  TaskList: # Running tasklist...
10-08 22:13 DEBUG  TaskList: ## Running select_target_dir...
10-08 22:13 INFO   WindowsBackend: Installing into C:\ubuntu
10-08 22:13 DEBUG  TaskList: ## Finished select_target_dir
10-08 22:13 DEBUG  TaskList: ## Running create_dir_structure...
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
10-08 22:13 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
10-08 22:13 DEBUG  TaskList: ## Finished create_dir_structure
10-08 22:13 DEBUG  TaskList: ## Running uncompress_target_dir...
10-08 22:13 DEBUG  TaskList: ## Finished uncompress_target_dir
10-08 22:13 DEBUG  TaskList: ## Running create_uninstaller...
10-08 22:13 DEBUG  WindowsBackend: Copying uninstaller D:\ubuntu-13.04-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.04-rev279
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
10-08 22:13 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-08 22:13 DEBUG  TaskList: ## Finished create_uninstaller
10-08 22:13 DEBUG  TaskList: ## Running copy_installation_files...
10-08 22:13 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
10-08 22:13 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\winboot -> C:\ubuntu\winboot
10-08 22:13 DEBUG  WindowsBackend: Copying C:\Users\iiui\AppData\Local\Temp\pylF6A2.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
10-08 22:13 DEBUG  TaskList: ## Finished copy_installation_files
10-08 22:13 DEBUG  TaskList: ## Running get_iso...
10-08 22:13 DEBUG  CommonBackend: Trying to use pre-specified ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 DEBUG  TaskList: New task is_valid_iso
10-08 22:13 DEBUG  TaskList: ### Running is_valid_iso...
10-08 22:13 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 DEBUG  TaskList: ### Finished is_valid_iso
10-08 22:13 DEBUG  TaskList: New task check_iso
10-08 22:13 DEBUG  TaskList: ### Running check_iso...
10-08 22:13 DEBUG  CommonBackend: Checking G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 DEBUG  Distro:   checking Kubuntu ISO G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 INFO   Distro: Found a valid iso for Kubuntu: G:\kubuntu-13.04-desktop-amd64.iso
10-08 22:13 DEBUG  TaskList: New task get_metalink
10-08 22:13 DEBUG  TaskList: #### Running get_metalink...
10-08 22:13 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) > C:\ubuntu\install
10-08 22:13 ERROR  CommonBackend: Cannot download metalink file [http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.04/release/kubuntu-13.04-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:13 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) > C:\ubuntu\install
10-08 22:13 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
10-08 22:13 DEBUG  TaskList: #### Finished get_metalink
10-08 22:13 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\kubuntu-13.04-desktop-amd64.iso, ignoring
10-08 22:13 DEBUG  TaskList: ### Finished check_iso
10-08 22:13 DEBUG  TaskList: New task copy_file
10-08 22:13 DEBUG  CommonBackend: Copying G:\kubuntu-13.04-desktop-amd64.iso > C:\ubuntu\install\installation.iso
10-08 22:13 DEBUG  TaskList: ### Running copy_file...
10-08 22:13 DEBUG  TaskList: ### Finished copy_file
10-08 22:13 DEBUG  TaskList: ## Finished get_iso
10-08 22:13 DEBUG  TaskList: ## Running extract_kernel...
10-08 22:13 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
10-08 22:13 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
10-08 22:13 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
10-08 22:13 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
10-08 22:13 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
10-08 22:13 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
10-08 22:13 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = deacc3c3a21beb4913c43a00bb6d5e01 == deacc3c3a21beb4913c43a00bb6d5e01
10-08 22:13 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
10-08 22:13 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = ff0212a8cdbaecde3326ce9c032d4a75 == ff0212a8cdbaecde3326ce9c032d4a75
10-08 22:13 DEBUG  TaskList: ## Finished extract_kernel
10-08 22:13 DEBUG  TaskList: ## Running choose_disk_sizes...
10-08 22:13 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
10-08 22:13 DEBUG  TaskList: ## Finished choose_disk_sizes
10-08 22:13 DEBUG  TaskList: ## Running create_preseed...
10-08 22:13 DEBUG  TaskList: ## Finished create_preseed
10-08 22:13 DEBUG  TaskList: ## Running modify_bootloader...
10-08 22:13 DEBUG  TaskList: New task modify_bcd
10-08 22:13 DEBUG  TaskList: ### Running modify_bcd...
10-08 22:13 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 90058.1328125 mb free ntfs)
10-08 22:13 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:13 DEBUG  TaskList: # Cancelling tasklist
10-08 22:13 DEBUG  TaskList: New task modify_bcd
10-08 22:13 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 695, in modify_bcd
ValueError: substring not found
10-08 22:13 DEBUG  TaskList: New task modify_bcd
10-08 22:13 DEBUG  TaskList: New task modify_bcd
10-08 22:13 DEBUG  TaskList: New task modify_bcd
10-08 22:13 DEBUG  TaskList: ## Finished modify_bootloader
10-08 22:13 DEBUG  TaskList: # Finished tasklist

```

i believe its a window error, can anybody tell me how to solve this ?
i have windows 8 intel core i 7 with 8 GB Ram with 750 Hard

---

### Post by hakuna_matata on 2013-10-08
> i believe its a window error, can anybody tell me how to solve this ?
I believe that this problem is that windows command 
```
bcdedit /create /d "Ubuntu" /application bootsector
```
fails. So there is no return value with an id within {}.

Maybe there is an existing menu entry with "Ubuntu" or something else.

---

### Post by akbarrkhan on 2013-10-08
> 
```
bcdedit /create /d "Ubuntu" /application bootsector
```
fails. So there is no return value with an id within {}.

Maybe there is an existing menu entry with "Ubuntu" or something else.

i am trying so hard from couple of hours to some how solve this error searched alot on internet but didnt found the solution

just waiting and waiting :'(

---

### Post by hakuna_matata on 2013-10-08
Are you familiar with bcdedit or tools like EasyBCD. Can you check, if there is an existing menu entry for ubuntu ? Can you delete this entry, if exists ?

---

### Post by akbarrkhan on 2013-10-08
> **hakuna_matata said:**
> Are you familiar with bcdedit or tools like EasyBCD. Can you check, if there is an existing menu entry for ubuntu ? Can you delete this entry, if exists ?

i tried bcdedit and also used EasyBCD but there was just one entry that was for windows 8 but none other :/

---

### Post by hakuna_matata on 2013-10-08
OK. If you are familiar with bcdedit and EasyBCD. Can you try to run manually following command:

```
bcdedit /create /d "Kubuntu" /application bootsector
```

I believe this one should be used if you install "Kubuntu" with wubi.

---

### Post by akbarrkhan on 2013-10-08
> **hakuna_matata said:**
> OK. If you are familiar with bcdedit and EasyBCD. Can you try to run manually following command:

```
bcdedit /create /d "Kubuntu" /application bootsector
```

I believe this one should be used if you install "Kubuntu" with wubi.

when i enter this command it says that the entry has successfully been created but when i try to install ubuntu or kubuntu it give the same error in log file

---

### Post by hakuna_matata on 2013-10-08
> when i enter this command it says that the entry has successfully been created
OK. Is there also an ID within {} in the answer of the command? This is necessary for wubi.

BTW: You know that windows 8 with UEFI and GPT doesn't work ? if
```
bcedit /enum
```
says there are entries for bootmgfw.efi or winload.efi you have UEFI!

---

### Post by akbarrkhan on 2013-10-08
> **hakuna_matata said:**
> OK. Is there also an ID within {} in the answer of the command? This is necessary for wubi.

BTW: You know that windows 8 with UEFI and GPT doesn't work ? if
```
bcedit /enum
```
says there are entries for bootmgfw.efi or winload.efi you have UEFI!

ya there was id with {} in the answer with command

i dont know abt uefi ana gpt 

bcedit /enum  after using this there was a path for winload.exe

---

### Post by hakuna_matata on 2013-10-08
> **akbarrkhan said:**
> i dont know abt uefi ana gpt
Some infos for [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") and [GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table"). I don't believe that your problem is caused by UEFI and/or GPT, so I try to help you.

I try to interpret source code of wubi from [here]("http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/view/head:/src/wubi/backends/win32/backend.py") (line 693 - 695):
> ```

        command = [bcdedit, '/create', '/d', '%s' % self.info.distro.name, '/application', 'bootsector']
        id = run_command(command)
        id = id[id.index('{'):id.index('}')+1]

```
But I don't know what's wrong. IMHO wubi runs "bcdedit" and examines the answer for { and }. if { is not found or } is not found, the error "ValueError: substring not found" occurs.
        
Maybe, dual boot without wubi works fine for you.

---

### Post by akbarrkhan on 2013-10-08
> **hakuna_matata said:**
> Some infos for [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") and [GPT]("http://en.wikipedia.org/wiki/GUID_Partition_Table"). I don't believe that your problem is caused by UEFI and/or GPT, so I try to help you.

I try to interpret source code of wubi from [here]("http://bazaar.launchpad.net/~ubuntu-installer/wubi/trunk/view/head:/src/wubi/backends/win32/backend.py") (line 693 - 695):

But I don't know what's wrong. IMHO wubi runs "bcdedit" and examines the answer for { and }. if { is not found or } is not found, the error "ValueError: substring not found" occurs.
        
Maybe, dual boot without wubi works fine for you.

thx for the info abt UEFI and GPT

wt do u mean by dual boot ?

---

### Post by hakuna_matata on 2013-10-08
> wt do u mean by dual boot ? 		

[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by akbarrkhan on 2013-10-08
> **hakuna_matata said:**
> [WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
i tried the bootable usb though but my pc is not allowing to boot from cdrom :/

ill try this one too soon hope it works

---

### Post by carl4926 on 2013-10-09
Wubi?

I thought it had been shelved?

---

### Post by andrew64 on 2014-02-08
hi ppl i'm very new to ubuntu and having the same problem tbh. Also i'm just staring to learn code so please explain how i can fix this in the dumbest terms imaginable thanks.

---

