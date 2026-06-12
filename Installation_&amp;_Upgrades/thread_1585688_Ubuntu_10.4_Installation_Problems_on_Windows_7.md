---
title: "Ubuntu 10.4 Installation Problems on Windows 7"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by vic4ever on 2010-09-30
Here is the error log. I'm trying to install Ubuntu 10.4 on my Windows 7 PC.
I did try install 9.4 but the same error messsage kept come in.

10-01 09:19 INFO   root: === wubi 10.04.1 rev190 ===
10-01 09:19 DEBUG  root: Logfile is c:\users\vic4ever\appdata\local\temp\wubi-10.04.1-rev190.log
10-01 09:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"', '--cdmenu']
10-01 09:19 DEBUG  CommonBackend: data_dir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\data
10-01 09:19 DEBUG  WindowsBackend: 7z=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\bin\7z.exe
10-01 09:19 DEBUG  CommonBackend: Fetching basic info...
10-01 09:19 DEBUG  CommonBackend: original_exe=D:\wubi.exe
10-01 09:19 DEBUG  CommonBackend: platform=win32
10-01 09:19 DEBUG  CommonBackend: osname=nt
10-01 09:19 DEBUG  CommonBackend: language=vi_VN
10-01 09:19 DEBUG  CommonBackend: encoding=cp1258
10-01 09:19 DEBUG  WindowsBackend: arch=amd64
10-01 09:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\data\isolist.ini
10-01 09:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
10-01 09:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
10-01 09:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
10-01 09:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
10-01 09:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
10-01 09:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
10-01 09:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
10-01 09:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
10-01 09:19 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
10-01 09:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
10-01 09:19 DEBUG  WindowsBackend: Fetching host info...
10-01 09:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
10-01 09:19 DEBUG  WindowsBackend: windows version=vista
10-01 09:19 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
10-01 09:19 DEBUG  WindowsBackend: windows_sp=None
10-01 09:19 DEBUG  WindowsBackend: windows_build=7600
10-01 09:19 DEBUG  WindowsBackend: gmt=7
10-01 09:19 DEBUG  WindowsBackend: country=VN
10-01 09:19 DEBUG  WindowsBackend: timezone=Asia/Saigon
10-01 09:19 DEBUG  WindowsBackend: windows_username=Vic4ever
10-01 09:19 DEBUG  WindowsBackend: user_full_name=Vic4ever
10-01 09:19 DEBUG  WindowsBackend: user_directory=C:\Users\Vic4ever
10-01 09:19 DEBUG  WindowsBackend: windows_language_code=None
10-01 09:19 DEBUG  WindowsBackend: windows_language=English
10-01 09:19 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5250  @ 1.50GHz
10-01 09:19 DEBUG  WindowsBackend: bootloader=vista
10-01 09:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 58972.8945313 mb free ntfs)
10-01 09:19 DEBUG  WindowsBackend: drive=Drive(C: hd 58972.8945313 mb free ntfs)
10-01 09:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
10-01 09:19 DEBUG  WindowsBackend: drive=Drive(F: hd 10475.3242188 mb free ntfs)
10-01 09:19 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
10-01 09:19 DEBUG  WindowsBackend: drive=Drive(I: hd 2673.51171875 mb free ntfs)
10-01 09:19 DEBUG  WindowsBackend: uninstaller_path=None
10-01 09:19 DEBUG  WindowsBackend: previous_target_dir=None
10-01 09:19 DEBUG  WindowsBackend: previous_distro_name=None
10-01 09:19 DEBUG  WindowsBackend: keyboard_id=67699721
10-01 09:19 DEBUG  WindowsBackend: keyboard_layout=us
10-01 09:19 DEBUG  WindowsBackend: keyboard_variant=
10-01 09:19 DEBUG  CommonBackend: python locale=('vi_VN', 'cp1258')
10-01 09:19 DEBUG  CommonBackend: locale=vi_VN
10-01 09:19 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
10-01 09:19 DEBUG  CommonBackend: Searching ISOs on USB devices
10-01 09:19 DEBUG  CommonBackend: Searching for local CDs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Ubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Ubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Ubuntu Netbook CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Kubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Kubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Kubuntu Netbook CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Xubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Xubuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Mythbuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp is a valid Mythbuntu CD
10-01 09:19 DEBUG  Distro:     does not contain C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\casper\filesystem.squashfs
10-01 09:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
10-01 09:19 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release i386 (20100816.1)
10-01 09:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-01 09:19 INFO   Distro: Found a valid CD for Ubuntu: D:\
10-01 09:19 INFO   root: Running the CD menu...
10-01 09:19 DEBUG  WindowsFrontend: __init__...
10-01 09:19 DEBUG  WindowsFrontend: on_init...
10-01 09:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\translations, languages=['vi_VN', 'vi']
10-01 09:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\translations, languages=['vi_VN', 'vi']
10-01 09:19 INFO   root: CD menu finished
10-01 09:19 INFO   root: Running the installer...
10-01 09:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\translations, languages=['vi_VN', 'vi']
10-01 09:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\translations, languages=['vi_VN', 'vi']
10-01 09:19 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=6000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=vic4ever
10-01 09:19 INFO   root: Received settings
10-01 09:19 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\translations, languages=['en_US', 'en']
10-01 09:19 DEBUG  TaskList: # Running tasklist...
10-01 09:19 DEBUG  TaskList: ## Running select_target_dir...
10-01 09:19 INFO   WindowsBackend: Installing into F:\ubuntu
10-01 09:19 DEBUG  TaskList: ## Finished select_target_dir
10-01 09:19 DEBUG  TaskList: ## Running create_dir_structure...
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
10-01 09:19 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
10-01 09:19 DEBUG  TaskList: ## Finished create_dir_structure
10-01 09:19 DEBUG  TaskList: ## Running uncompress_target_dir...
10-01 09:19 DEBUG  TaskList: ## Finished uncompress_target_dir
10-01 09:19 DEBUG  TaskList: ## Running create_uninstaller...
10-01 09:19 DEBUG  WindowsBackend: Copying uninstaller D:\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
10-01 09:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
10-01 09:19 DEBUG  TaskList: ## Finished create_uninstaller
10-01 09:19 DEBUG  TaskList: ## Running copy_installation_files...
10-01 09:19 DEBUG  WindowsBackend: Copying C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\data\custom-installation -> F:\ubuntu\install\custom-installation
10-01 09:19 DEBUG  WindowsBackend: Copying C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\winboot -> F:\ubuntu\winboot
10-01 09:19 DEBUG  WindowsBackend: Copying C:\Users\Vic4ever\AppData\Local\Temp\pyl9481.tmp\data\images\Ubuntu.ico -> F:\ubuntu\Ubuntu.ico
10-01 09:19 DEBUG  TaskList: ## Finished copy_installation_files
10-01 09:19 DEBUG  TaskList: ## Running get_iso...
10-01 09:19 DEBUG  TaskList: New task copy_file
10-01 09:19 DEBUG  TaskList: ### Running copy_file...
10-01 09:20 DEBUG  TaskList: ### Finished copy_file
10-01 09:20 DEBUG  TaskList: New task check_iso
10-01 09:20 DEBUG  TaskList: ### Running check_iso...
10-01 09:20 DEBUG  CommonBackend: Checking F:\ubuntu\install\installation.iso
10-01 09:20 DEBUG  Distro:   checking Ubuntu ISO F:\ubuntu\install\installation.iso
10-01 09:20 DEBUG  WindowsBackend:   extracting .disk\info from F:\ubuntu\install\installation.iso
10-01 09:20 DEBUG  Distro:   parsing info from str=Ubuntu 10.04.1 LTS "Lucid Lynx" - Release i386 (20100816.1)
10-01 09:20 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04.1', 'build': '20100816.1', 'codename': 'Lucid Lynx', 'arch': 'i386'}
10-01 09:20 INFO   Distro: Found a valid iso for Ubuntu: F:\ubuntu\install\installation.iso
10-01 09:20 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
10-01 09:20 DEBUG  TaskList: New task get_metalink
10-01 09:20 DEBUG  TaskList: #### Running get_metalink...
10-01 09:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink) > F:\ubuntu\install
10-01 09:20 DEBUG  downloader: Download start filename=F:\ubuntu\install\ubuntu-10.04.1-desktop-i386.metalink, url=http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-i386.metalink, basename=ubuntu-10.04.1-desktop-i386.metalink, length=43, text=None
10-01 09:20 DEBUG  downloader: download finished (read 43 bytes)
10-01 09:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink) > F:\ubuntu\install
10-01 09:20 DEBUG  downloader: Download start filename=F:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=43, text=None
10-01 09:20 DEBUG  downloader: download finished (read 43 bytes)
10-01 09:20 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg) > F:\ubuntu\install
10-01 09:20 DEBUG  downloader: Download start filename=F:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04.1/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=43, text=None
10-01 09:20 DEBUG  downloader: download finished (read 43 bytes)
10-01 09:20 ERROR  TaskList: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(G)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 378, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 244, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 42, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1190, in verify_str
  File "\lib\openpgp\sap\list.py", line 712, in list_as_signed
  File "\lib\openpgp\sap\list.py", line 618, in list_pkts
  File "\lib\openpgp\sap\pkt\Packet.py", line 67, in __init__
  File "\lib\openpgp\sap\pkt\Packet.py", line 110, in fill
PGPFormatError: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(G)
10-01 09:20 DEBUG  TaskList: # Cancelling tasklist
10-01 09:20 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for F:\ubuntu\install\installation.iso, ignoring
10-01 09:20 ERROR  root: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(G)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 378, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 244, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 42, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1190, in verify_str
  File "\lib\openpgp\sap\list.py", line 712, in list_as_signed
  File "\lib\openpgp\sap\list.py", line 618, in list_pkts
  File "\lib\openpgp\sap\pkt\Packet.py", line 67, in __init__
  File "\lib\openpgp\sap\pkt\Packet.py", line 110, in fill
PGPFormatError: Invalid tag data. Check len(d)=1, (ord(d) & 128)==128. Received->(G)
10-01 09:20 DEBUG  TaskList: ### Finished check_iso
10-01 09:20 DEBUG  TaskList: ## Finished get_iso
10-01 09:20 DEBUG  TaskList: # Finished tasklist

---

### Post by sanderd17 on 2010-10-01
It's just a debug log, nothing serious. How do you want to install it? 

From inside windows with wubi?

+ no repartition needed
+ easy to remove
- on crash, data is lost
- not that fast
- can't survive windows crash

Or next to windows

+ faster
+ more chance to recover data after crash
+ completely independent from windows
- repartition needed (ubuntu does this for you at install time)
- removing ubuntu is not that easy

I guess you are trying to do it with wubi, can you say what guide you follow and what steps you take?

---

