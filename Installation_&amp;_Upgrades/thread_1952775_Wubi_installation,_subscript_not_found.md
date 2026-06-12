---
title: "Wubi installation, subscript not found?"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by Livaud on 2012-04-04
Hey everyone, I'm new to the forum and to linux.  Finally got frustrated with windows so I'm trying to do a Wubi install of Ubuntu 11.10 to try it out. I first tried downloading just the wubi.exe file and letting it download/install, which didn't work, so I finally downloaded the 32bit Ubuntu and tried to install by placing the iso in the same file as wubi.exe. everything goes great for both methods until right at the end, then an error pops up and says "an error occurred: Subscript not found" and references a text file (found below) I have no idea what to do and I haven't found the problem on here either.  My suspicion is that this has something to do with my Windows 7 (which I know for a fact has corrupted files) but I'm hoping I'm wrong and that you guys can help me get the ball rolling.

It seems to me that nothing is wrong until the very end (like the last 20 or so lines depending on how the forum ends up formatting it) but like I said, I'm lost and most of this is kind of beyond me.  Help much appreciated, so very tired of windows lol.

04-04 22:57 INFO   root: === wubi 11.10 rev241 ===
04-04 22:57 DEBUG  root: Logfile is c:\users\danny\appdata\local\temp\wubi-11.10-rev241.log
04-04 22:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"', '--cdmenu']
04-04 22:57 DEBUG  CommonBackend: data_dir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\data
04-04 22:57 DEBUG  WindowsBackend: 7z=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\bin\7z.exe
04-04 22:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-04 22:57 DEBUG  CommonBackend: Fetching basic info...
04-04 22:57 DEBUG  CommonBackend: original_exe=F:\wubi.exe
04-04 22:57 DEBUG  CommonBackend: platform=win32
04-04 22:57 DEBUG  CommonBackend: osname=nt
04-04 22:57 DEBUG  CommonBackend: language=en_US
04-04 22:57 DEBUG  CommonBackend: encoding=cp1252
04-04 22:57 DEBUG  WindowsBackend: arch=amd64
04-04 22:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\data\isolist.ini
04-04 22:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-04 22:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-04 22:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-04 22:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-04 22:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-04 22:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-04 22:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-04 22:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-04 22:57 DEBUG  WindowsBackend: Fetching host info...
04-04 22:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-04 22:57 DEBUG  WindowsBackend: windows version=vista
04-04 22:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-04 22:57 DEBUG  WindowsBackend: windows_sp=None
04-04 22:57 DEBUG  WindowsBackend: windows_build=7600
04-04 22:57 DEBUG  WindowsBackend: gmt=-5
04-04 22:57 DEBUG  WindowsBackend: country=US
04-04 22:57 DEBUG  WindowsBackend: timezone=America/New_York
04-04 22:57 DEBUG  WindowsBackend: windows_username=Danny
04-04 22:57 DEBUG  WindowsBackend: user_full_name=Danny
04-04 22:57 DEBUG  WindowsBackend: user_directory=C:\Users\Danny
04-04 22:57 DEBUG  WindowsBackend: windows_language_code=1033
04-04 22:57 DEBUG  WindowsBackend: windows_language=English
04-04 22:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
04-04 22:57 DEBUG  WindowsBackend: bootloader=vista
04-04 22:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53091.6523438 mb free ntfs)
04-04 22:57 DEBUG  WindowsBackend: drive=Drive(C: hd 53091.6523438 mb free ntfs)
04-04 22:57 DEBUG  WindowsBackend: drive=Drive(D: hd 1854.96484375 mb free ntfs)
04-04 22:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
04-04 22:57 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-04 22:57 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-04 22:57 DEBUG  WindowsBackend: uninstaller_path=None
04-04 22:57 DEBUG  WindowsBackend: previous_target_dir=None
04-04 22:57 DEBUG  WindowsBackend: previous_distro_name=None
04-04 22:57 DEBUG  WindowsBackend: keyboard_id=67699721
04-04 22:57 DEBUG  WindowsBackend: keyboard_layout=us
04-04 22:57 DEBUG  WindowsBackend: keyboard_variant=
04-04 22:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-04 22:57 DEBUG  CommonBackend: locale=en_US.UTF-8
04-04 22:57 DEBUG  WindowsBackend: total_memory_mb=2046.4296875
04-04 22:57 DEBUG  CommonBackend: Searching ISOs on USB devices
04-04 22:57 DEBUG  CommonBackend: Searching for local CDs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Ubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Ubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Kubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Kubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Xubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Xubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Mythbuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp is a valid Mythbuntu CD
04-04 22:57 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 22:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 22:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 22:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
04-04 22:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
04-04 22:57 INFO   Distro: Found a valid CD for Ubuntu: F:\
04-04 22:57 INFO   root: Running the CD menu...
04-04 22:57 DEBUG  WindowsFrontend: __init__...
04-04 22:57 DEBUG  WindowsFrontend: on_init...
04-04 22:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
04-04 22:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
04-04 22:57 INFO   root: CD menu finished
04-04 22:57 INFO   root: Running the installer...
04-04 22:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
04-04 22:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
04-04 22:57 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=15000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danny
04-04 22:57 INFO   root: Received settings
04-04 22:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\translations, languages=['en_US', 'en']
04-04 22:57 DEBUG  TaskList: # Running tasklist...
04-04 22:57 DEBUG  TaskList: ## Running select_target_dir...
04-04 22:57 INFO   WindowsBackend: Installing into C:\ubuntu
04-04 22:57 DEBUG  TaskList: ## Finished select_target_dir
04-04 22:57 DEBUG  TaskList: ## Running create_dir_structure...
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-04 22:57 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-04 22:57 DEBUG  TaskList: ## Finished create_dir_structure
04-04 22:57 DEBUG  TaskList: ## Running uncompress_target_dir...
04-04 22:57 DEBUG  TaskList: ## Finished uncompress_target_dir
04-04 22:57 DEBUG  TaskList: ## Running create_uninstaller...
04-04 22:57 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-04 22:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-04 22:57 DEBUG  TaskList: ## Finished create_uninstaller
04-04 22:57 DEBUG  TaskList: ## Running copy_installation_files...
04-04 22:57 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-04 22:57 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\winboot -> C:\ubuntu\winboot
04-04 22:57 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylE80D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-04 22:57 DEBUG  TaskList: ## Finished copy_installation_files
04-04 22:57 DEBUG  TaskList: ## Running get_iso...
04-04 22:57 DEBUG  TaskList: New task copy_file
04-04 22:57 DEBUG  TaskList: ### Running copy_file...
04-04 22:59 DEBUG  TaskList: ### Finished copy_file
04-04 22:59 DEBUG  TaskList: New task check_iso
04-04 22:59 DEBUG  TaskList: ### Running check_iso...
04-04 22:59 DEBUG  CommonBackend: Checking C:\ubuntu\install\installation.iso
04-04 22:59 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\installation.iso
04-04 22:59 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\installation.iso
04-04 22:59 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
04-04 22:59 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
04-04 22:59 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\installation.iso
04-04 22:59 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-04 22:59 DEBUG  TaskList: New task get_metalink
04-04 22:59 DEBUG  TaskList: #### Running get_metalink...
04-04 22:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) > C:\ubuntu\install
04-04 22:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.10-desktop-i386.metalink, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink, basename=ubuntu-11.10-desktop-i386.metalink, length=4867, text=None
04-04 22:59 DEBUG  downloader: download finished (read 4867 bytes)
04-04 22:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink](http://releases.ubuntu.com/11.10/MD5SUMS-metalink) > C:\ubuntu\install
04-04 22:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
04-04 22:59 DEBUG  downloader: download finished (read 419 bytes)
04-04 22:59 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-04 22:59 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-04 22:59 DEBUG  downloader: download finished (read 198 bytes)
04-04 22:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-04 22:59 INFO   saplog: Checking block bindings..
04-04 22:59 INFO   saplog: Key verified successfully.
04-04 22:59 DEBUG  CommonBackend: metalink md5sums:
a65c220b437d6907ba9463b7f479fea5  ubuntu-11.10-alternate-amd64.metalink
bdbf5bf7dfa85cad2cd711f081b071ec  ubuntu-11.10-alternate-i386.metalink
4a4ddfa7d6eea4d9cf7a9f8d854e0418  ubuntu-11.10-desktop-amd64.metalink
a84050d7b00ff42b83a69ad7309b6f36  ubuntu-11.10-desktop-i386.metalink
c2f7e1f7352a8d3cd1c2dede0c709a1a  ubuntu-11.10-server-amd64.metalink
2b296035b3ba3f8536dc0efa49a52fc2  ubuntu-11.10-server-i386.metalink

04-04 22:59 DEBUG  TaskList: #### Finished get_metalink
04-04 22:59 DEBUG  TaskList: New task get_file_md5
04-04 22:59 DEBUG  TaskList: #### Running get_file_md5...
04-04 22:59 DEBUG  TaskList: #### Finished get_file_md5
04-04 22:59 DEBUG  TaskList: ### Finished check_iso
04-04 22:59 DEBUG  TaskList: ## Finished get_iso
04-04 22:59 DEBUG  TaskList: ## Running extract_kernel...
04-04 22:59 DEBUG  CommonBackend: Copying files from CD F:\
04-04 22:59 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-04 22:59 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
04-04 22:59 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
04-04 22:59 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
04-04 22:59 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = d6baee1e11f1d6de6eba6bd43dbde352 == d6baee1e11f1d6de6eba6bd43dbde352
04-04 22:59 DEBUG  TaskList: ## Finished extract_kernel
04-04 22:59 DEBUG  TaskList: ## Running choose_disk_sizes...
04-04 22:59 DEBUG  WindowsBackend: total size=15000
  root=14744
  swap=256
  home=0
  usr=0
04-04 22:59 DEBUG  TaskList: ## Finished choose_disk_sizes
04-04 22:59 DEBUG  TaskList: ## Running create_preseed...
04-04 22:59 DEBUG  TaskList: ## Finished create_preseed
04-04 22:59 DEBUG  TaskList: ## Running modify_bootloader...
04-04 22:59 DEBUG  TaskList: New task modify_bcd
04-04 22:59 DEBUG  TaskList: ### Running modify_bcd...
04-04 22:59 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 53091.6523438 mb free ntfs)
04-04 22:59 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 690, in modify_bcd
ValueError: substring not found
04-04 22:59 DEBUG  TaskList: # Cancelling tasklist
04-04 22:59 DEBUG  TaskList: New task modify_bcd
04-04 22:59 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 690, in modify_bcd
ValueError: substring not found
04-04 22:59 DEBUG  TaskList: ## Finished modify_bootloader
04-04 22:59 DEBUG  TaskList: # Finished tasklist
04-04 23:14 INFO   root: === wubi 11.10 rev241 ===
04-04 23:14 DEBUG  root: Logfile is c:\users\danny\appdata\local\temp\wubi-11.10-rev241.log
04-04 23:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Danny\\Desktop\\Wubi Ubuntu\\wubi.exe"']
04-04 23:14 DEBUG  CommonBackend: data_dir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\data
04-04 23:14 DEBUG  WindowsBackend: 7z=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\bin\7z.exe
04-04 23:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-04 23:14 DEBUG  CommonBackend: Fetching basic info...
04-04 23:14 DEBUG  CommonBackend: original_exe=C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe
04-04 23:14 DEBUG  CommonBackend: platform=win32
04-04 23:14 DEBUG  CommonBackend: osname=nt
04-04 23:14 DEBUG  CommonBackend: language=en_US
04-04 23:14 DEBUG  CommonBackend: encoding=cp1252
04-04 23:14 DEBUG  WindowsBackend: arch=amd64
04-04 23:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\data\isolist.ini
04-04 23:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-04 23:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-04 23:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-04 23:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-04 23:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-04 23:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-04 23:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-04 23:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-04 23:14 DEBUG  WindowsBackend: Fetching host info...
04-04 23:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-04 23:14 DEBUG  WindowsBackend: windows version=vista
04-04 23:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-04 23:14 DEBUG  WindowsBackend: windows_sp=None
04-04 23:14 DEBUG  WindowsBackend: windows_build=7600
04-04 23:14 DEBUG  WindowsBackend: gmt=-5
04-04 23:14 DEBUG  WindowsBackend: country=US
04-04 23:14 DEBUG  WindowsBackend: timezone=America/New_York
04-04 23:14 DEBUG  WindowsBackend: windows_username=Danny
04-04 23:14 DEBUG  WindowsBackend: user_full_name=Danny
04-04 23:14 DEBUG  WindowsBackend: user_directory=C:\Users\Danny
04-04 23:14 DEBUG  WindowsBackend: windows_language_code=1033
04-04 23:14 DEBUG  WindowsBackend: windows_language=English
04-04 23:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
04-04 23:14 DEBUG  WindowsBackend: bootloader=vista
04-04 23:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 52368.3632813 mb free ntfs)
04-04 23:14 DEBUG  WindowsBackend: drive=Drive(C: hd 52368.3632813 mb free ntfs)
04-04 23:14 DEBUG  WindowsBackend: drive=Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:14 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-04 23:14 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-04 23:14 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-04 23:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-04 23:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-04 23:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-04 23:14 DEBUG  WindowsBackend: keyboard_id=67699721
04-04 23:14 DEBUG  WindowsBackend: keyboard_layout=us
04-04 23:14 DEBUG  WindowsBackend: keyboard_variant=
04-04 23:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-04 23:14 DEBUG  CommonBackend: locale=en_US.UTF-8
04-04 23:14 DEBUG  WindowsBackend: total_memory_mb=2046.4296875
04-04 23:14 DEBUG  CommonBackend: Searching ISOs on USB devices
04-04 23:14 DEBUG  CommonBackend: Searching for local CDs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:14 INFO   root: Already installed, running the uninstaller...
04-04 23:14 INFO   root: Running the uninstaller...
04-04 23:14 INFO   CommonBackend: This is the uninstaller running
04-04 23:14 DEBUG  WindowsFrontend: __init__...
04-04 23:14 DEBUG  WindowsFrontend: on_init...
04-04 23:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\translations, languages=['en_US', 'en']
04-04 23:14 INFO   root: Received settings
04-04 23:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\translations, languages=['en_US', 'en']
04-04 23:14 DEBUG  TaskList: # Running tasklist...
04-04 23:14 DEBUG  TaskList: ## Running Remove bootloader entry...
04-04 23:14 DEBUG  WindowsBackend: Could not find bcd id
04-04 23:14 DEBUG  WindowsBackend: undo_bootini C:
04-04 23:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 52368.3632813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: undo_bootini D:
04-04 23:15 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:15 DEBUG  TaskList: ## Finished Remove bootloader entry
04-04 23:15 DEBUG  TaskList: ## Running Remove target dir...
04-04 23:15 DEBUG  CommonBackend: Deleting C:\ubuntu
04-04 23:15 DEBUG  TaskList: ## Finished Remove target dir
04-04 23:15 DEBUG  TaskList: ## Running Remove registry key...
04-04 23:15 DEBUG  TaskList: ## Finished Remove registry key
04-04 23:15 DEBUG  TaskList: # Finished tasklist
04-04 23:15 INFO   root: Almost finished uninstalling
04-04 23:15 INFO   root: Finished uninstallation
04-04 23:15 DEBUG  CommonBackend: Fetching basic info...
04-04 23:15 DEBUG  CommonBackend: original_exe=C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe
04-04 23:15 DEBUG  CommonBackend: platform=win32
04-04 23:15 DEBUG  CommonBackend: osname=nt
04-04 23:15 DEBUG  WindowsBackend: arch=amd64
04-04 23:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\data\isolist.ini
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-04 23:15 DEBUG  WindowsBackend: Fetching host info...
04-04 23:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-04 23:15 DEBUG  WindowsBackend: windows version=vista
04-04 23:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-04 23:15 DEBUG  WindowsBackend: windows_sp=None
04-04 23:15 DEBUG  WindowsBackend: windows_build=7600
04-04 23:15 DEBUG  WindowsBackend: gmt=-5
04-04 23:15 DEBUG  WindowsBackend: country=US
04-04 23:15 DEBUG  WindowsBackend: timezone=America/New_York
04-04 23:15 DEBUG  WindowsBackend: windows_username=Danny
04-04 23:15 DEBUG  WindowsBackend: user_full_name=Danny
04-04 23:15 DEBUG  WindowsBackend: user_directory=C:\Users\Danny
04-04 23:15 DEBUG  WindowsBackend: windows_language_code=1033
04-04 23:15 DEBUG  WindowsBackend: windows_language=English
04-04 23:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
04-04 23:15 DEBUG  WindowsBackend: bootloader=vista
04-04 23:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53084.5195313 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(C: hd 53084.5195313 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: uninstaller_path=None
04-04 23:15 DEBUG  WindowsBackend: previous_target_dir=None
04-04 23:15 DEBUG  WindowsBackend: previous_distro_name=None
04-04 23:15 DEBUG  WindowsBackend: keyboard_id=67699721
04-04 23:15 DEBUG  WindowsBackend: keyboard_layout=us
04-04 23:15 DEBUG  WindowsBackend: keyboard_variant=
04-04 23:15 DEBUG  WindowsBackend: total_memory_mb=2046.4296875
04-04 23:15 DEBUG  CommonBackend: Searching ISOs on USB devices
04-04 23:15 DEBUG  CommonBackend: Searching for local CDs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 INFO   root: Running the installer...
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\translations, languages=['en_US', 'en']
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\translations, languages=['en_US', 'en']
04-04 23:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=danny
04-04 23:15 INFO   root: Received settings
04-04 23:15 DEBUG  CommonBackend: Searching for local CD
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  CommonBackend: Searching for local ISO
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pyl14A9.tmp\translations, languages=['en_US', 'en']
04-04 23:15 DEBUG  TaskList: # Running tasklist...
04-04 23:15 DEBUG  TaskList: ## Running select_target_dir...
04-04 23:15 INFO   WindowsBackend: Installing into C:\ubuntu
04-04 23:15 DEBUG  TaskList: ## Finished select_target_dir
04-04 23:15 DEBUG  TaskList: ## Running create_dir_structure...
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-04 23:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-04 23:15 DEBUG  TaskList: ## Finished create_dir_structure
04-04 23:15 DEBUG  TaskList: ## Running create_uninstaller...
04-04 23:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-04 23:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-04 23:15 DEBUG  TaskList: ## Finished create_uninstaller
04-04 23:15 DEBUG  TaskList: ## Running create_preseed_diskimage...
04-04 23:15 DEBUG  TaskList: ## Finished create_preseed_diskimage
04-04 23:15 DEBUG  TaskList: ## Running get_diskimage...
04-04 23:15 DEBUG  TaskList: New task download
04-04 23:15 DEBUG  TaskList: ### Running download...
04-04 23:15 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz) > C:\ubuntu\disks\amd64.tar.xz
04-04 23:15 DEBUG  downloader: Download start filename=C:\ubuntu\disks\amd64.tar.xz, url=http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz, basename=amd64.tar.xz, length=515679844, text=None
04-04 23:15 INFO   WindowsFrontend: Operation cancelled
04-04 23:15 DEBUG  WindowsFrontend: frontend.quit
04-04 23:15 DEBUG  WindowsFrontend: frontend.on_quit
04-04 23:15 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
04-04 23:15 DEBUG  TaskList: # Cancelling tasklist
04-04 23:15 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
04-04 23:15 DEBUG  root: application.on_quit
04-04 23:15 DEBUG  root: Forceful exit
04-04 23:15 INFO   root: sys.exit
04-04 23:15 INFO   root: === wubi 11.10 rev241 ===
04-04 23:15 DEBUG  root: Logfile is c:\users\danny\appdata\local\temp\wubi-11.10-rev241.log
04-04 23:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Danny\\Desktop\\Wubi Ubuntu\\wubi.exe"']
04-04 23:15 DEBUG  CommonBackend: data_dir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\data
04-04 23:15 DEBUG  WindowsBackend: 7z=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\bin\7z.exe
04-04 23:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-04 23:15 DEBUG  CommonBackend: Fetching basic info...
04-04 23:15 DEBUG  CommonBackend: original_exe=C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe
04-04 23:15 DEBUG  CommonBackend: platform=win32
04-04 23:15 DEBUG  CommonBackend: osname=nt
04-04 23:15 DEBUG  CommonBackend: language=en_US
04-04 23:15 DEBUG  CommonBackend: encoding=cp1252
04-04 23:15 DEBUG  WindowsBackend: arch=amd64
04-04 23:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\data\isolist.ini
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-04 23:15 DEBUG  WindowsBackend: Fetching host info...
04-04 23:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-04 23:15 DEBUG  WindowsBackend: windows version=vista
04-04 23:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-04 23:15 DEBUG  WindowsBackend: windows_sp=None
04-04 23:15 DEBUG  WindowsBackend: windows_build=7600
04-04 23:15 DEBUG  WindowsBackend: gmt=-5
04-04 23:15 DEBUG  WindowsBackend: country=US
04-04 23:15 DEBUG  WindowsBackend: timezone=America/New_York
04-04 23:15 DEBUG  WindowsBackend: windows_username=Danny
04-04 23:15 DEBUG  WindowsBackend: user_full_name=Danny
04-04 23:15 DEBUG  WindowsBackend: user_directory=C:\Users\Danny
04-04 23:15 DEBUG  WindowsBackend: windows_language_code=1033
04-04 23:15 DEBUG  WindowsBackend: windows_language=English
04-04 23:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
04-04 23:15 DEBUG  WindowsBackend: bootloader=vista
04-04 23:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53080.6757813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(C: hd 53080.6757813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-04 23:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-04 23:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-04 23:15 DEBUG  WindowsBackend: keyboard_id=67699721
04-04 23:15 DEBUG  WindowsBackend: keyboard_layout=us
04-04 23:15 DEBUG  WindowsBackend: keyboard_variant=
04-04 23:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-04 23:15 DEBUG  CommonBackend: locale=en_US.UTF-8
04-04 23:15 DEBUG  WindowsBackend: total_memory_mb=2046.4296875
04-04 23:15 DEBUG  CommonBackend: Searching ISOs on USB devices
04-04 23:15 DEBUG  CommonBackend: Searching for local CDs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 INFO   root: Already installed, running the uninstaller...
04-04 23:15 INFO   root: Running the uninstaller...
04-04 23:15 INFO   CommonBackend: This is the uninstaller running
04-04 23:15 DEBUG  WindowsFrontend: __init__...
04-04 23:15 DEBUG  WindowsFrontend: on_init...
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\translations, languages=['en_US', 'en']
04-04 23:15 INFO   root: Received settings
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\translations, languages=['en_US', 'en']
04-04 23:15 DEBUG  TaskList: # Running tasklist...
04-04 23:15 DEBUG  TaskList: ## Running Remove bootloader entry...
04-04 23:15 DEBUG  WindowsBackend: Could not find bcd id
04-04 23:15 DEBUG  WindowsBackend: undo_bootini C:
04-04 23:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 53080.6757813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: undo_bootini D:
04-04 23:15 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:15 DEBUG  TaskList: ## Finished Remove bootloader entry
04-04 23:15 DEBUG  TaskList: ## Running Remove target dir...
04-04 23:15 DEBUG  CommonBackend: Deleting C:\ubuntu
04-04 23:15 DEBUG  TaskList: ## Finished Remove target dir
04-04 23:15 DEBUG  TaskList: ## Running Remove registry key...
04-04 23:15 DEBUG  TaskList: ## Finished Remove registry key
04-04 23:15 DEBUG  TaskList: # Finished tasklist
04-04 23:15 INFO   root: Almost finished uninstalling
04-04 23:15 INFO   root: Finished uninstallation
04-04 23:15 DEBUG  CommonBackend: Fetching basic info...
04-04 23:15 DEBUG  CommonBackend: original_exe=C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe
04-04 23:15 DEBUG  CommonBackend: platform=win32
04-04 23:15 DEBUG  CommonBackend: osname=nt
04-04 23:15 DEBUG  WindowsBackend: arch=amd64
04-04 23:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\data\isolist.ini
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-04 23:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-04 23:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-04 23:15 DEBUG  WindowsBackend: Fetching host info...
04-04 23:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-04 23:15 DEBUG  WindowsBackend: windows version=vista
04-04 23:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Professional
04-04 23:15 DEBUG  WindowsBackend: windows_sp=None
04-04 23:15 DEBUG  WindowsBackend: windows_build=7600
04-04 23:15 DEBUG  WindowsBackend: gmt=-5
04-04 23:15 DEBUG  WindowsBackend: country=US
04-04 23:15 DEBUG  WindowsBackend: timezone=America/New_York
04-04 23:15 DEBUG  WindowsBackend: windows_username=Danny
04-04 23:15 DEBUG  WindowsBackend: user_full_name=Danny
04-04 23:15 DEBUG  WindowsBackend: user_directory=C:\Users\Danny
04-04 23:15 DEBUG  WindowsBackend: windows_language_code=1033
04-04 23:15 DEBUG  WindowsBackend: windows_language=English
04-04 23:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
04-04 23:15 DEBUG  WindowsBackend: bootloader=vista
04-04 23:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53083.8632813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(C: hd 53083.8632813 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(D: hd 1854.96484375 mb free ntfs)
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
04-04 23:15 DEBUG  WindowsBackend: uninstaller_path=None
04-04 23:15 DEBUG  WindowsBackend: previous_target_dir=None
04-04 23:15 DEBUG  WindowsBackend: previous_distro_name=None
04-04 23:15 DEBUG  WindowsBackend: keyboard_id=67699721
04-04 23:15 DEBUG  WindowsBackend: keyboard_layout=us
04-04 23:15 DEBUG  WindowsBackend: keyboard_variant=
04-04 23:15 DEBUG  WindowsBackend: total_memory_mb=2046.4296875
04-04 23:15 DEBUG  CommonBackend: Searching ISOs on USB devices
04-04 23:15 DEBUG  CommonBackend: Searching for local CDs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
04-04 23:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:15 INFO   root: Running the installer...
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\translations, languages=['en_US', 'en']
04-04 23:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\translations, languages=['en_US', 'en']
04-04 23:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=livaud
04-04 23:16 INFO   root: Received settings
04-04 23:16 DEBUG  CommonBackend: Searching for local CD
04-04 23:16 DEBUG  Distro:   checking whether C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp is a valid Ubuntu CD
04-04 23:16 DEBUG  Distro:     does not contain C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\casper\filesystem.squashfs
04-04 23:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-04 23:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-04 23:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-04 23:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-04 23:16 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
04-04 23:16 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
04-04 23:16 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
04-04 23:16 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
04-04 23:16 DEBUG  CommonBackend: Searching for local ISO
04-04 23:16 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release i386 (20111012)
04-04 23:16 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'i386'}
04-04 23:16 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\translations, languages=['en_US', 'en']
04-04 23:16 DEBUG  TaskList: # Running tasklist...
04-04 23:16 DEBUG  TaskList: ## Running select_target_dir...
04-04 23:16 INFO   WindowsBackend: Installing into C:\ubuntu
04-04 23:16 DEBUG  TaskList: ## Finished select_target_dir
04-04 23:16 DEBUG  TaskList: ## Running create_dir_structure...
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-04 23:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-04 23:16 DEBUG  TaskList: ## Finished create_dir_structure
04-04 23:16 DEBUG  TaskList: ## Running uncompress_target_dir...
04-04 23:16 DEBUG  TaskList: ## Finished uncompress_target_dir
04-04 23:16 DEBUG  TaskList: ## Running create_uninstaller...
04-04 23:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Danny\Desktop\Wubi Ubuntu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-04 23:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-04 23:16 DEBUG  TaskList: ## Finished create_uninstaller
04-04 23:16 DEBUG  TaskList: ## Running copy_installation_files...
04-04 23:16 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-04 23:16 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\winboot -> C:\ubuntu\winboot
04-04 23:16 DEBUG  WindowsBackend: Copying C:\Users\Danny\AppData\Local\Temp\pylB2BB.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
04-04 23:16 DEBUG  TaskList: ## Finished copy_installation_files
04-04 23:16 DEBUG  TaskList: ## Running get_iso...
04-04 23:16 DEBUG  CommonBackend: Trying to use ISO C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 DEBUG  TaskList: New task check_iso
04-04 23:16 DEBUG  TaskList: ### Running check_iso...
04-04 23:16 DEBUG  CommonBackend: Checking C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 INFO   Distro: Found a valid iso for Ubuntu: C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso
04-04 23:16 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
04-04 23:16 DEBUG  TaskList: New task get_metalink
04-04 23:16 DEBUG  TaskList: #### Running get_metalink...
04-04 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink](http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink) > C:\ubuntu\install
04-04 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.10-desktop-i386.metalink, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-desktop-i386.metalink, basename=ubuntu-11.10-desktop-i386.metalink, length=4867, text=None
04-04 23:16 DEBUG  downloader: download finished (read 4867 bytes)
04-04 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink](http://releases.ubuntu.com/11.10/MD5SUMS-metalink) > C:\ubuntu\install
04-04 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=419, text=None
04-04 23:16 DEBUG  downloader: download finished (read 419 bytes)
04-04 23:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg) > C:\ubuntu\install
04-04 23:16 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
04-04 23:16 DEBUG  downloader: download finished (read 198 bytes)
04-04 23:16 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
04-04 23:16 INFO   saplog: Checking block bindings..
04-04 23:16 INFO   saplog: Key verified successfully.
04-04 23:16 DEBUG  CommonBackend: metalink md5sums:
a65c220b437d6907ba9463b7f479fea5  ubuntu-11.10-alternate-amd64.metalink
bdbf5bf7dfa85cad2cd711f081b071ec  ubuntu-11.10-alternate-i386.metalink
4a4ddfa7d6eea4d9cf7a9f8d854e0418  ubuntu-11.10-desktop-amd64.metalink
a84050d7b00ff42b83a69ad7309b6f36  ubuntu-11.10-desktop-i386.metalink
c2f7e1f7352a8d3cd1c2dede0c709a1a  ubuntu-11.10-server-amd64.metalink
2b296035b3ba3f8536dc0efa49a52fc2  ubuntu-11.10-server-i386.metalink

04-04 23:16 DEBUG  TaskList: #### Finished get_metalink
04-04 23:16 DEBUG  TaskList: New task get_file_md5
04-04 23:16 DEBUG  TaskList: #### Running get_file_md5...
04-04 23:16 DEBUG  TaskList: #### Finished get_file_md5
04-04 23:16 DEBUG  TaskList: ### Finished check_iso
04-04 23:16 DEBUG  TaskList: New task copy_file
04-04 23:16 DEBUG  CommonBackend: Copying C:\Users\Danny\Desktop\Wubi Ubuntu\ubuntu-11.10-desktop-i386.iso > C:\ubuntu\install\installation.iso
04-04 23:16 DEBUG  TaskList: ### Running copy_file...
04-04 23:17 DEBUG  TaskList: ### Finished copy_file
04-04 23:17 DEBUG  TaskList: ## Finished get_iso
04-04 23:17 DEBUG  TaskList: ## Running extract_kernel...
04-04 23:17 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
04-04 23:17 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
04-04 23:17 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
04-04 23:17 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
04-04 23:17 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
04-04 23:17 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
04-04 23:17 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = fde150f5c6fd2de66ed7876efbfcc4c7 == fde150f5c6fd2de66ed7876efbfcc4c7
04-04 23:17 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
04-04 23:17 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = d6baee1e11f1d6de6eba6bd43dbde352 == d6baee1e11f1d6de6eba6bd43dbde352
04-04 23:17 DEBUG  TaskList: ## Finished extract_kernel
04-04 23:17 DEBUG  TaskList: ## Running choose_disk_sizes...
04-04 23:17 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
04-04 23:17 DEBUG  TaskList: ## Finished choose_disk_sizes
04-04 23:17 DEBUG  TaskList: ## Running create_preseed...
04-04 23:17 DEBUG  TaskList: ## Finished create_preseed
04-04 23:17 DEBUG  TaskList: ## Running modify_bootloader...
04-04 23:17 DEBUG  TaskList: New task modify_bcd
04-04 23:17 DEBUG  TaskList: ### Running modify_bcd...
04-04 23:17 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 53083.8632813 mb free ntfs)
04-04 23:17 ERROR  TaskList: substring not found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 690, in modify_bcd
ValueError: substring not found
04-04 23:17 DEBUG  TaskList: # Cancelling tasklist
04-04 23:17 DEBUG  TaskList: New task modify_bcd
04-04 23:17 ERROR  root: substring not found
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 690, in modify_bcd
ValueError: substring not found
04-04 23:17 DEBUG  TaskList: ## Finished modify_bootloader
04-04 23:17 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2012-04-05
It does look like a windows issue. Reviewing the code:
```
        command = [bcdedit, '/create', '/d', '%s' % self.info.distro.name, '/application', 'bootsector']
        id = run_command(command)
        id = id[id.index('{'):id.index('}')+1]
```

It fails on that last line, trying to parse the response from the bcdedit command. Please can you go to a command prompt (select Run as Administrator) and then enter:
```
bcdedit
```

See what output it gives. Thanks

---

### Post by Livaud on 2012-04-05
I'll try it and repost as soon as I get home to my computer tonight. Thanks for the quick reply.

---

### Post by Livaud on 2012-04-05
Command prompt bcdedit yields

"Program too big to fit in memory"

so. very. confused. I've got 50gb of free memory on C:, unless it's referring to something else? :confused:

---

### Post by bcbc on 2012-04-05
Yeah... that's not normal. Memory is referring to RAM, not disk space (the 50GB you mentioned is disk space). You could try again without running anything else to see if that makes a difference, but I can't imagine bcdedit needs a lot of RAM.

Usually Wubi is great to try out Ubuntu without having to partition, but in your case - with a bit of a questionable Windows install - you might do better just doing a normal dual boot.

I also recommend backing up all your data if you haven't already. You might consider shrinking your windows partition using Windows' Disk Management first, rather than relying on the Ubuntu installer to do it.

---

### Post by Livaud on 2012-04-06
I've got 2gb of ram. Not a powerhouse by any stretch of the imagination, but I would think it'd be plenty, and I've had everything else closed that can be closed when running bcdedit and wubi. I really do suspect it's just a problem with windows, not the computer. I have to do a reinstall of windows one of these days anyway, so I'll probably just do the back up, reinstalling, partitioning and then dual boot Ubuntu all at the same time. Until I have the time and patience for that though, anyone else have any ideas for current problem?

---

