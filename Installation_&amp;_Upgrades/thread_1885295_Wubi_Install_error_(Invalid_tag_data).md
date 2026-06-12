---
title: "Wubi Install error (Invalid tag data)"
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by Wubi &gt; all on 2011-11-22
I've been trying to use Wubi to install Ubuntu but it keeps giving me error messages during installation (after inputting my username and password and selecting a version of ubuntu...). Is there an easy fix? I don't have a cd or usb with enough memory so I can't use that option. The error messages frequently say no such file or directory found or invalid tag data.

---

### Post by bcbc on 2011-11-22
What does the logfile say? Post the contents from the %temp% directory (called wubi-11.10-revxxx.log)

---

### Post by Wubi &gt; all on 2011-11-22
I deleted the old log file and created a new entry. Here it is.

11-22 21:25 INFO   root: === wubi 11.10 rev245 ===
11-22 21:25 DEBUG  root: Logfile is c:\users\luis\appdata\local\temp\wubi-11.10-rev245.log
11-22 21:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Luis\\Desktop\\wubi.exe"']
11-22 21:25 DEBUG  CommonBackend: data_dir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\data
11-22 21:25 DEBUG  WindowsBackend: 7z=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\bin\7z.exe
11-22 21:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-22 21:25 DEBUG  CommonBackend: Fetching basic info...
11-22 21:25 DEBUG  CommonBackend: original_exe=C:\Users\Luis\Desktop\wubi.exe
11-22 21:25 DEBUG  CommonBackend: platform=win32
11-22 21:25 DEBUG  CommonBackend: osname=nt
11-22 21:25 DEBUG  CommonBackend: language=en_US
11-22 21:25 DEBUG  CommonBackend: encoding=cp1252
11-22 21:25 DEBUG  WindowsBackend: arch=amd64
11-22 21:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\data\isolist.ini
11-22 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-22 21:25 DEBUG  WindowsBackend: Fetching host info...
11-22 21:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-22 21:25 DEBUG  WindowsBackend: windows version=vista
11-22 21:25 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
11-22 21:25 DEBUG  WindowsBackend: windows_sp=Service Pack 2
11-22 21:25 DEBUG  WindowsBackend: windows_build=6002
11-22 21:25 DEBUG  WindowsBackend: gmt=-8
11-22 21:25 DEBUG  WindowsBackend: country=US
11-22 21:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-22 21:25 DEBUG  WindowsBackend: windows_username=Luis
11-22 21:25 DEBUG  WindowsBackend: user_full_name=Luis
11-22 21:25 DEBUG  WindowsBackend: user_directory=C:\Users\Luis
11-22 21:25 DEBUG  WindowsBackend: windows_language_code=1033
11-22 21:25 DEBUG  WindowsBackend: windows_language=English
11-22 21:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
11-22 21:25 DEBUG  WindowsBackend: bootloader=vista
11-22 21:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 168359.652344 mb free ntfs)
11-22 21:25 DEBUG  WindowsBackend: drive=Drive(C: hd 168359.652344 mb free ntfs)
11-22 21:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-22 21:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-22 21:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-22 21:25 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-22 21:25 DEBUG  WindowsBackend: keyboard_id=67699721
11-22 21:25 DEBUG  WindowsBackend: keyboard_layout=us
11-22 21:25 DEBUG  WindowsBackend: keyboard_variant=
11-22 21:25 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-22 21:25 DEBUG  CommonBackend: locale=en_US.UTF-8
11-22 21:25 DEBUG  WindowsBackend: total_memory_mb=2045.33203125
11-22 21:25 DEBUG  CommonBackend: Searching ISOs on USB devices
11-22 21:25 DEBUG  CommonBackend: Searching for local CDs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 INFO   root: Already installed, running the uninstaller...
11-22 21:25 INFO   root: Running the uninstaller...
11-22 21:25 INFO   CommonBackend: This is the uninstaller running
11-22 21:25 DEBUG  WindowsFrontend: __init__...
11-22 21:25 DEBUG  WindowsFrontend: on_init...
11-22 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\translations, languages=['en_US', 'en']
11-22 21:25 INFO   root: Received settings
11-22 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\translations, languages=['en_US', 'en']
11-22 21:25 DEBUG  TaskList: # Running tasklist...
11-22 21:25 DEBUG  TaskList: ## Running Remove bootloader entry...
11-22 21:25 DEBUG  WindowsBackend: Could not find bcd id
11-22 21:25 DEBUG  WindowsBackend: undo_bootini C:
11-22 21:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 168359.652344 mb free ntfs)
11-22 21:25 DEBUG  TaskList: ## Finished Remove bootloader entry
11-22 21:25 DEBUG  TaskList: ## Running Remove target dir...
11-22 21:25 DEBUG  CommonBackend: Deleting C:\ubuntu
11-22 21:25 DEBUG  TaskList: ## Finished Remove target dir
11-22 21:25 DEBUG  TaskList: ## Running Remove registry key...
11-22 21:25 DEBUG  TaskList: ## Finished Remove registry key
11-22 21:25 DEBUG  TaskList: # Finished tasklist
11-22 21:25 INFO   root: Almost finished uninstalling
11-22 21:25 INFO   root: Finished uninstallation
11-22 21:25 DEBUG  CommonBackend: Fetching basic info...
11-22 21:25 DEBUG  CommonBackend: original_exe=C:\Users\Luis\Desktop\wubi.exe
11-22 21:25 DEBUG  CommonBackend: platform=win32
11-22 21:25 DEBUG  CommonBackend: osname=nt
11-22 21:25 DEBUG  WindowsBackend: arch=amd64
11-22 21:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\data\isolist.ini
11-22 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-22 21:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-22 21:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-22 21:25 DEBUG  WindowsBackend: Fetching host info...
11-22 21:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-22 21:25 DEBUG  WindowsBackend: windows version=vista
11-22 21:25 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Premium
11-22 21:25 DEBUG  WindowsBackend: windows_sp=Service Pack 2
11-22 21:25 DEBUG  WindowsBackend: windows_build=6002
11-22 21:25 DEBUG  WindowsBackend: gmt=-8
11-22 21:25 DEBUG  WindowsBackend: country=US
11-22 21:25 DEBUG  WindowsBackend: timezone=America/Los_Angeles
11-22 21:25 DEBUG  WindowsBackend: windows_username=Luis
11-22 21:25 DEBUG  WindowsBackend: user_full_name=Luis
11-22 21:25 DEBUG  WindowsBackend: user_directory=C:\Users\Luis
11-22 21:25 DEBUG  WindowsBackend: windows_language_code=1033
11-22 21:25 DEBUG  WindowsBackend: windows_language=English
11-22 21:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
11-22 21:25 DEBUG  WindowsBackend: bootloader=vista
11-22 21:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 168362.25 mb free ntfs)
11-22 21:25 DEBUG  WindowsBackend: drive=Drive(C: hd 168362.25 mb free ntfs)
11-22 21:25 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-22 21:25 DEBUG  WindowsBackend: uninstaller_path=None
11-22 21:25 DEBUG  WindowsBackend: previous_target_dir=None
11-22 21:25 DEBUG  WindowsBackend: previous_distro_name=None
11-22 21:25 DEBUG  WindowsBackend: keyboard_id=67699721
11-22 21:25 DEBUG  WindowsBackend: keyboard_layout=us
11-22 21:25 DEBUG  WindowsBackend: keyboard_variant=
11-22 21:25 DEBUG  WindowsBackend: total_memory_mb=2045.33203125
11-22 21:25 DEBUG  CommonBackend: Searching ISOs on USB devices
11-22 21:25 DEBUG  CommonBackend: Searching for local CDs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 INFO   root: Running the installer...
11-22 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\translations, languages=['en_US', 'en']
11-22 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\translations, languages=['en_US', 'en']
11-22 21:25 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=luis
11-22 21:25 INFO   root: Received settings
11-22 21:25 DEBUG  CommonBackend: Searching for local CD
11-22 21:25 DEBUG  Distro:   checking whether C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\casper\filesystem.squashfs
11-22 21:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-22 21:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-22 21:25 DEBUG  CommonBackend: Searching for local ISO
11-22 21:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\translations, languages=['en_US', 'en']
11-22 21:25 DEBUG  TaskList: # Running tasklist...
11-22 21:25 DEBUG  TaskList: ## Running select_target_dir...
11-22 21:25 INFO   WindowsBackend: Installing into C:\ubuntu
11-22 21:25 DEBUG  TaskList: ## Finished select_target_dir
11-22 21:25 DEBUG  TaskList: ## Running create_dir_structure...
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-22 21:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-22 21:25 DEBUG  TaskList: ## Finished create_dir_structure
11-22 21:25 DEBUG  TaskList: ## Running uncompress_target_dir...
11-22 21:25 DEBUG  TaskList: ## Finished uncompress_target_dir
11-22 21:25 DEBUG  TaskList: ## Running create_uninstaller...
11-22 21:25 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Luis\Desktop\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Kubuntu.ico
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
11-22 21:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-22 21:25 DEBUG  TaskList: ## Finished create_uninstaller
11-22 21:25 DEBUG  TaskList: ## Running copy_installation_files...
11-22 21:25 DEBUG  WindowsBackend: Copying C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-22 21:25 DEBUG  WindowsBackend: Copying C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\winboot -> C:\ubuntu\winboot
11-22 21:25 DEBUG  WindowsBackend: Copying C:\Users\Luis\AppData\Local\Temp\pyl9B94.tmp\data\images\Kubuntu.ico -> C:\ubuntu\Kubuntu.ico
11-22 21:25 DEBUG  TaskList: ## Finished copy_installation_files
11-22 21:25 DEBUG  TaskList: ## Running get_iso...
11-22 21:25 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-22 21:25 DEBUG  TaskList: New task get_metalink
11-22 21:25 DEBUG  TaskList: ### Running get_metalink...
11-22 21:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/11.10/kubuntu-11.10-desktop-amd64.metalink](http://releases.ubuntu.com/kubuntu/11.10/kubuntu-11.10-desktop-amd64.metalink) > C:\ubuntu\install
11-22 21:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\kubuntu-11.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/kubuntu/11.10/kubuntu-11.10-desktop-amd64.metalink, basename=kubuntu-11.10-desktop-amd64.metalink, length=4752, text=None
11-22 21:25 DEBUG  downloader: download finished (read 4752 bytes)
11-22 21:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink](http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink) > C:\ubuntu\install
11-22 21:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=4633, text=None
11-22 21:25 DEBUG  downloader: download finished (read 4633 bytes)
11-22 21:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
11-22 21:25 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/kubuntu/11.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=4641, text=None
11-22 21:25 DEBUG  downloader: download finished (read 4641 bytes)
11-22 21:25 ERROR  TaskList: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(<)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 451, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 268, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 41, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1190, in verify_str
  File "\lib\openpgp\sap\list.py", line 712, in list_as_signed
  File "\lib\openpgp\sap\list.py", line 618, in list_pkts
  File "\lib\openpgp\sap\pkt\Packet.py", line 67, in __init__
  File "\lib\openpgp\sap\pkt\Packet.py", line 110, in fill
PGPFormatError: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(<)
11-22 21:25 DEBUG  TaskList: # Cancelling tasklist
11-22 21:25 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 589, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 404, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-22 21:25 ERROR  root: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(<)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 451, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 268, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 41, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1190, in verify_str
  File "\lib\openpgp\sap\list.py", line 712, in list_as_signed
  File "\lib\openpgp\sap\list.py", line 618, in list_pkts
  File "\lib\openpgp\sap\pkt\Packet.py", line 67, in __init__
  File "\lib\openpgp\sap\pkt\Packet.py", line 110, in fill
PGPFormatError: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(<)
11-22 21:25 DEBUG  TaskList: # Cancelling tasklist
11-22 21:25 DEBUG  TaskList: # Finished tasklist

---

### Post by Wubi &gt; all on 2011-11-22
Wow the length is ridiculous :confused:

*For some reason it showed installation attempts dating back to the 28th of October. I edited it to show only one attempt to install so it's a lot shorter now. Let me know if I should include more info.

---

### Post by lisati on 2011-11-23
> **Wubi > all said:**
> Wow the length is ridiculous :confused:

Yup! I've added "code" tags to help keep the length managable

---

### Post by bcbc on 2011-11-23
Okay... create a [new wubi bug]("bugs.launchpad.net/wubi/+filebug") and attach that last log file or copy paste that single entry. That'll help someone fix this. 

To get around the issue:
Download the desktop CD ISO yourself ( [http://releases.ubuntu.com/kubuntu/11.10/kubuntu-11.10-desktop-amd64.iso](http://releases.ubuntu.com/kubuntu/11.10/kubuntu-11.10-desktop-amd64.iso) )and save it in the same folder as wubi.exe. Then disconnect from the internet and run wubi.exe. It will find and use that ISO. 
Before rebooting reconnect to the net.

---

