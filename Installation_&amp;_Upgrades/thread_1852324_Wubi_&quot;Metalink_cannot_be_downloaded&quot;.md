---
title: "Wubi: &quot;Metalink cannot be downloaded&quot;"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by natkill on 2011-09-29
Hi all,

I recently just bought a Toshiba nb505 netbook, and I want to dual boot windows and Ubuntu on it so that I can still keep MS Word and Excel for when I need them for school. However, when I tried to download it, using Wubi, the first time it booted, Ubuntu completely froze and crashed, causing my computer to restart. I uninstalled it and now I cannot download it again. It says "metalink cannot be downloaded, therefore the ISO cannot be downloaded."

09-29 13:15 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) > C:\ubuntu\install
09-29 13:15 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 13:15 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) > C:\ubuntu\install
09-29 13:15 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink](http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 13:15 DEBUG  TaskList: ### Finished get_metalink
09-29 13:15 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 13:15 DEBUG  TaskList: # Cancelling tasklist
09-29 13:15 DEBUG  TaskList: # Finished tasklist
09-29 13:15 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO

I don't know what any of that means, but any help would be greatly appreciated.

---

### Post by bcbc on 2011-09-30
Is that the only error? If it is then the problem is that you're not connected to the internet. But that seems unlikely... Post the whole log if you are connected to the internet i.e. that is not the problem (post it between [CODE][[SIZE="1"] [/SIZE]/CODE] tags - click # above).

If you want to make it easier, first delete/rename/clear the current log and rerun so there is only one installation attempt in it.

---

### Post by natkill on 2011-09-30
Yeah, I was connected to the internet when I was trying to install it. I had an ethernet cord hooked up and it showed 100mbps speed connection with our router. 

```
09-27 18:14 INFO   root: === wubi 11.04 rev211 ===
09-27 18:14 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-27 18:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-27 18:14 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\data
09-27 18:14 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\bin\7z.exe
09-27 18:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-27 18:14 DEBUG  CommonBackend: Fetching basic info...
09-27 18:14 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-27 18:14 DEBUG  CommonBackend: platform=win32
09-27 18:14 DEBUG  CommonBackend: osname=nt
09-27 18:14 DEBUG  CommonBackend: language=en_US
09-27 18:14 DEBUG  CommonBackend: encoding=cp1252
09-27 18:14 DEBUG  WindowsBackend: arch=amd64
09-27 18:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\data\isolist.ini
09-27 18:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-27 18:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-27 18:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-27 18:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-27 18:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-27 18:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-27 18:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-27 18:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-27 18:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-27 18:14 DEBUG  WindowsBackend: Fetching host info...
09-27 18:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-27 18:14 DEBUG  WindowsBackend: windows version=vista
09-27 18:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-27 18:14 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-27 18:14 DEBUG  WindowsBackend: windows_build=7601
09-27 18:14 DEBUG  WindowsBackend: gmt=-6
09-27 18:14 DEBUG  WindowsBackend: country=US
09-27 18:14 DEBUG  WindowsBackend: timezone=America/Chicago
09-27 18:14 DEBUG  WindowsBackend: windows_username=Natalie
09-27 18:14 DEBUG  WindowsBackend: user_full_name=Natalie
09-27 18:14 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-27 18:14 DEBUG  WindowsBackend: windows_language_code=1033
09-27 18:14 DEBUG  WindowsBackend: windows_language=English
09-27 18:14 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-27 18:14 DEBUG  WindowsBackend: bootloader=vista
09-27 18:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 211572.3125 mb free ntfs)
09-27 18:14 DEBUG  WindowsBackend: drive=Drive(C: hd 211572.3125 mb free ntfs)
09-27 18:14 DEBUG  WindowsBackend: uninstaller_path=None
09-27 18:14 DEBUG  WindowsBackend: previous_target_dir=None
09-27 18:14 DEBUG  WindowsBackend: previous_distro_name=None
09-27 18:14 DEBUG  WindowsBackend: keyboard_id=67699721
09-27 18:14 DEBUG  WindowsBackend: keyboard_layout=us
09-27 18:14 DEBUG  WindowsBackend: keyboard_variant=
09-27 18:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-27 18:14 DEBUG  CommonBackend: locale=en_US.UTF-8
09-27 18:14 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-27 18:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-27 18:14 DEBUG  CommonBackend: Searching for local CDs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu Netbook CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Kubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Kubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Xubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Xubuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Mythbuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Mythbuntu CD
09-27 18:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:14 INFO   root: Running the installer...
09-27 18:14 DEBUG  WindowsFrontend: __init__...
09-27 18:14 DEBUG  WindowsFrontend: on_init...
09-27 18:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
09-27 18:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
09-27 18:17 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=natalie
09-27 18:17 INFO   root: Received settings
09-27 18:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
09-27 18:17 DEBUG  TaskList: # Running tasklist...
09-27 18:17 DEBUG  TaskList: ## Running select_target_dir...
09-27 18:17 INFO   WindowsBackend: Installing into C:\ubuntu
09-27 18:17 DEBUG  TaskList: ## Finished select_target_dir
09-27 18:17 DEBUG  TaskList: ## Running create_dir_structure...
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-27 18:17 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-27 18:17 DEBUG  TaskList: ## Finished create_dir_structure
09-27 18:17 DEBUG  TaskList: ## Running uncompress_target_dir...
09-27 18:17 DEBUG  TaskList: ## Finished uncompress_target_dir
09-27 18:17 DEBUG  TaskList: ## Running create_uninstaller...
09-27 18:17 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-27 18:17 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-27 18:17 DEBUG  TaskList: ## Finished create_uninstaller
09-27 18:17 DEBUG  TaskList: ## Running copy_installation_files...
09-27 18:17 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-27 18:17 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\winboot -> C:\ubuntu\winboot
09-27 18:17 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-27 18:17 DEBUG  TaskList: ## Finished copy_installation_files
09-27 18:17 DEBUG  TaskList: ## Running get_iso...
09-27 18:17 DEBUG  CommonBackend: Searching for local CD
09-27 18:17 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp is a valid Ubuntu CD
09-27 18:17 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\casper\filesystem.squashfs
09-27 18:17 DEBUG  CommonBackend: Searching for local ISO
09-27 18:17 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-27 18:17 DEBUG  TaskList: New task get_metalink
09-27 18:17 DEBUG  TaskList: ### Running get_metalink...
09-27 18:17 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
09-27 18:17 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
09-27 18:17 DEBUG  downloader: download finished (read 28363 bytes)
09-27 18:17 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
09-27 18:17 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
09-27 18:17 DEBUG  downloader: download finished (read 874 bytes)
09-27 18:17 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
09-27 18:17 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-27 18:17 DEBUG  downloader: download finished (read 198 bytes)
09-27 18:18 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-27 18:18 INFO   saplog: Checking block bindings..
09-27 18:18 INFO   saplog: Key verified successfully.
09-27 18:18 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

09-27 18:18 DEBUG  TaskList: ### Finished get_metalink
09-27 18:18 DEBUG  TaskList: New task download
09-27 18:18 DEBUG  TaskList: ### Running download...
09-27 18:18 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  TaskList: ### Finished download
09-27 19:11 DEBUG  TaskList: New task check_iso
09-27 19:11 DEBUG  TaskList: ### Running check_iso...
09-27 19:11 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
09-27 19:11 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
09-27 19:11 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  TaskList: New task get_file_md5
09-27 19:11 DEBUG  TaskList: #### Running get_file_md5...
09-27 19:11 DEBUG  TaskList: #### Finished get_file_md5
09-27 19:11 DEBUG  TaskList: ### Finished check_iso
09-27 19:11 DEBUG  TaskList: ## Finished get_iso
09-27 19:11 DEBUG  TaskList: ## Running extract_kernel...
09-27 19:11 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:11 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:12 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:12 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-27 19:12 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-27 19:12 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
09-27 19:12 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
09-27 19:12 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
09-27 19:12 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
09-27 19:12 DEBUG  TaskList: ## Finished extract_kernel
09-27 19:12 DEBUG  TaskList: ## Running choose_disk_sizes...
09-27 19:12 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
09-27 19:12 DEBUG  TaskList: ## Finished choose_disk_sizes
09-27 19:12 DEBUG  TaskList: ## Running create_preseed...
09-27 19:12 DEBUG  TaskList: ## Finished create_preseed
09-27 19:12 DEBUG  TaskList: ## Running modify_bootloader...
09-27 19:12 DEBUG  TaskList: New task modify_bcd
09-27 19:12 DEBUG  TaskList: ### Running modify_bcd...
09-27 19:12 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 211572.3125 mb free ntfs)
09-27 19:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {56cd65f8-9f39-11e0-b02b-f393666bdcab}
09-27 19:12 DEBUG  TaskList: ### Finished modify_bcd
09-27 19:12 DEBUG  TaskList: ## Finished modify_bootloader
09-27 19:12 DEBUG  TaskList: ## Running modify_grub_configuration...
09-27 19:12 DEBUG  TaskList: ## Finished modify_grub_configuration
09-27 19:12 DEBUG  TaskList: ## Running create_virtual_disks...
09-27 19:12 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
09-27 19:12 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
09-27 19:12 DEBUG  TaskList: ## Finished create_virtual_disks
09-27 19:12 DEBUG  TaskList: ## Running uncompress_files...
09-27 19:12 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
09-27 19:12 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
09-27 19:12 DEBUG  TaskList: ## Finished uncompress_files
09-27 19:12 DEBUG  TaskList: ## Running eject_cd...
09-27 19:12 DEBUG  TaskList: ## Finished eject_cd
09-27 19:12 DEBUG  TaskList: # Finished tasklist
09-27 19:12 INFO   root: Almost finished installing
09-27 19:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl1370.tmp\translations, languages=['en_US', 'en']
09-27 19:12 INFO   root: Finished installation
09-27 19:12 INFO   root: Rebooting
09-27 19:12 DEBUG  TaskList: # Running tasklist...
09-27 19:12 DEBUG  TaskList: ## Running reboot...
09-27 19:12 DEBUG  TaskList: ## Finished reboot
09-27 19:12 DEBUG  TaskList: # Finished tasklist
09-27 19:12 DEBUG  root: application.quit
09-27 19:12 DEBUG  WindowsFrontend: frontend.quit
09-27 19:12 DEBUG  WindowsFrontend: frontend.on_quit
09-27 19:12 DEBUG  root: application.on_quit
09-27 19:12 INFO   root: sys.exit
09-27 21:06 INFO   root: === wubi 11.04 rev211 ===
09-27 21:06 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-27 21:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
09-27 21:06 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\data
09-27 21:06 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\bin\7z.exe
09-27 21:06 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-27 21:06 DEBUG  CommonBackend: Fetching basic info...
09-27 21:06 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
09-27 21:06 DEBUG  CommonBackend: platform=win32
09-27 21:06 DEBUG  CommonBackend: osname=nt
09-27 21:06 DEBUG  CommonBackend: language=en_US
09-27 21:06 DEBUG  CommonBackend: encoding=cp1252
09-27 21:06 DEBUG  WindowsBackend: arch=amd64
09-27 21:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\data\isolist.ini
09-27 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-27 21:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-27 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-27 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-27 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-27 21:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-27 21:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-27 21:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-27 21:06 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-27 21:06 DEBUG  WindowsBackend: Fetching host info...
09-27 21:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-27 21:06 DEBUG  WindowsBackend: windows version=vista
09-27 21:06 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-27 21:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-27 21:06 DEBUG  WindowsBackend: windows_build=7601
09-27 21:06 DEBUG  WindowsBackend: gmt=-6
09-27 21:06 DEBUG  WindowsBackend: country=US
09-27 21:06 DEBUG  WindowsBackend: timezone=America/Chicago
09-27 21:06 DEBUG  WindowsBackend: windows_username=Natalie
09-27 21:06 DEBUG  WindowsBackend: user_full_name=Natalie
09-27 21:06 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-27 21:06 DEBUG  WindowsBackend: windows_language_code=1033
09-27 21:06 DEBUG  WindowsBackend: windows_language=English
09-27 21:06 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-27 21:06 DEBUG  WindowsBackend: bootloader=vista
09-27 21:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 193857.824219 mb free ntfs)
09-27 21:06 DEBUG  WindowsBackend: drive=Drive(C: hd 193857.824219 mb free ntfs)
09-27 21:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-27 21:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-27 21:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-27 21:06 DEBUG  WindowsBackend: keyboard_id=67699721
09-27 21:06 DEBUG  WindowsBackend: keyboard_layout=us
09-27 21:06 DEBUG  WindowsBackend: keyboard_variant=
09-27 21:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-27 21:06 DEBUG  CommonBackend: locale=en_US.UTF-8
09-27 21:06 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-27 21:06 DEBUG  CommonBackend: Searching ISOs on USB devices
09-27 21:06 DEBUG  CommonBackend: Searching for local CDs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Ubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Ubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Ubuntu Netbook CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Kubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Kubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Xubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Xubuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Mythbuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp is a valid Mythbuntu CD
09-27 21:06 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\casper\filesystem.squashfs
09-27 21:06 INFO   root: Running the uninstaller...
09-27 21:06 INFO   CommonBackend: This is the uninstaller running
09-27 21:06 DEBUG  WindowsFrontend: __init__...
09-27 21:06 DEBUG  WindowsFrontend: on_init...
09-27 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\translations, languages=['en_US', 'en']
09-27 21:06 INFO   root: Received settings
09-27 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\translations, languages=['en_US', 'en']
09-27 21:06 DEBUG  TaskList: # Running tasklist...
09-27 21:06 DEBUG  TaskList: ## Running Backup ISO...
09-27 21:06 DEBUG  TaskList: ## Finished Backup ISO
09-27 21:06 DEBUG  TaskList: ## Running Remove bootloader entry...
09-27 21:06 DEBUG  WindowsBackend: Removing bcd entry {56cd65f8-9f39-11e0-b02b-f393666bdcab}
09-27 21:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
09-27 21:06 DEBUG  WindowsBackend: undo_bootini C:
09-27 21:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 193857.824219 mb free ntfs)
09-27 21:06 DEBUG  TaskList: ## Finished Remove bootloader entry
09-27 21:06 DEBUG  TaskList: ## Running Remove target dir...
09-27 21:06 DEBUG  CommonBackend: Deleting C:\ubuntu
09-27 21:06 DEBUG  TaskList: ## Finished Remove target dir
09-27 21:06 DEBUG  TaskList: ## Running Remove registry key...
09-27 21:06 DEBUG  TaskList: ## Finished Remove registry key
09-27 21:06 DEBUG  TaskList: # Finished tasklist
09-27 21:06 INFO   root: Almost finished uninstalling
09-27 21:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylDE7B.tmp\translations, languages=['en_US', 'en']
09-27 21:06 INFO   root: Finished uninstallation
09-27 21:06 DEBUG  root: application.quit
09-27 21:06 DEBUG  WindowsFrontend: frontend.quit
09-27 21:06 DEBUG  WindowsFrontend: frontend.on_quit
09-27 21:06 DEBUG  root: application.on_quit
09-27 21:06 INFO   root: sys.exit
09-28 21:31 INFO   root: === wubi 11.04 rev211 ===
09-28 21:31 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-28 21:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-28 21:31 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\data
09-28 21:31 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\bin\7z.exe
09-28 21:31 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-28 21:31 DEBUG  CommonBackend: Fetching basic info...
09-28 21:31 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-28 21:31 DEBUG  CommonBackend: platform=win32
09-28 21:31 DEBUG  CommonBackend: osname=nt
09-28 21:31 DEBUG  CommonBackend: language=en_US
09-28 21:31 DEBUG  CommonBackend: encoding=cp1252
09-28 21:31 DEBUG  WindowsBackend: arch=amd64
09-28 21:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\data\isolist.ini
09-28 21:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-28 21:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-28 21:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-28 21:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-28 21:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-28 21:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-28 21:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-28 21:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-28 21:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-28 21:31 DEBUG  WindowsBackend: Fetching host info...
09-28 21:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-28 21:31 DEBUG  WindowsBackend: windows version=vista
09-28 21:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-28 21:31 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-28 21:31 DEBUG  WindowsBackend: windows_build=7601
09-28 21:31 DEBUG  WindowsBackend: gmt=-6
09-28 21:31 DEBUG  WindowsBackend: country=US
09-28 21:31 DEBUG  WindowsBackend: timezone=America/Chicago
09-28 21:31 DEBUG  WindowsBackend: windows_username=Natalie
09-28 21:31 DEBUG  WindowsBackend: user_full_name=Natalie
09-28 21:31 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-28 21:31 DEBUG  WindowsBackend: windows_language_code=1033
09-28 21:31 DEBUG  WindowsBackend: windows_language=English
09-28 21:31 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-28 21:31 DEBUG  WindowsBackend: bootloader=vista
09-28 21:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 210849.015625 mb free ntfs)
09-28 21:31 DEBUG  WindowsBackend: drive=Drive(C: hd 210849.015625 mb free ntfs)
09-28 21:31 DEBUG  WindowsBackend: uninstaller_path=None
09-28 21:31 DEBUG  WindowsBackend: previous_target_dir=None
09-28 21:31 DEBUG  WindowsBackend: previous_distro_name=None
09-28 21:31 DEBUG  WindowsBackend: keyboard_id=67699721
09-28 21:31 DEBUG  WindowsBackend: keyboard_layout=us
09-28 21:31 DEBUG  WindowsBackend: keyboard_variant=
09-28 21:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-28 21:31 DEBUG  CommonBackend: locale=en_US.UTF-8
09-28 21:31 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-28 21:31 DEBUG  CommonBackend: Searching ISOs on USB devices
09-28 21:31 DEBUG  CommonBackend: Searching for local CDs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Ubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Ubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Ubuntu Netbook CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Kubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Kubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Xubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Xubuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Mythbuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Mythbuntu CD
09-28 21:31 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:31 INFO   root: Running the installer...
09-28 21:31 DEBUG  WindowsFrontend: __init__...
09-28 21:31 DEBUG  WindowsFrontend: on_init...
09-28 21:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\translations, languages=['en_US', 'en']
09-28 21:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\translations, languages=['en_US', 'en']
09-28 21:32 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=natalie
09-28 21:32 INFO   root: Received settings
09-28 21:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\translations, languages=['en_US', 'en']
09-28 21:32 DEBUG  TaskList: # Running tasklist...
09-28 21:32 DEBUG  TaskList: ## Running select_target_dir...
09-28 21:32 INFO   WindowsBackend: Installing into C:\ubuntu
09-28 21:32 DEBUG  TaskList: ## Finished select_target_dir
09-28 21:32 DEBUG  TaskList: ## Running create_dir_structure...
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-28 21:32 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-28 21:32 DEBUG  TaskList: ## Finished create_dir_structure
09-28 21:32 DEBUG  TaskList: ## Running uncompress_target_dir...
09-28 21:32 DEBUG  TaskList: ## Finished uncompress_target_dir
09-28 21:32 DEBUG  TaskList: ## Running create_uninstaller...
09-28 21:32 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-28 21:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-28 21:32 DEBUG  TaskList: ## Finished create_uninstaller
09-28 21:32 DEBUG  TaskList: ## Running copy_installation_files...
09-28 21:32 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-28 21:32 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\winboot -> C:\ubuntu\winboot
09-28 21:32 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
09-28 21:32 DEBUG  TaskList: ## Finished copy_installation_files
09-28 21:32 DEBUG  TaskList: ## Running get_iso...
09-28 21:32 DEBUG  CommonBackend: Searching for local CD
09-28 21:32 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp is a valid Ubuntu CD
09-28 21:32 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl705A.tmp\casper\filesystem.squashfs
09-28 21:32 DEBUG  CommonBackend: Searching for local ISO
09-28 21:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-28 21:32 DEBUG  TaskList: New task get_metalink
09-28 21:32 DEBUG  TaskList: ### Running get_metalink...
09-28 21:32 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
09-28 21:32 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
09-28 21:32 DEBUG  downloader: download finished (read 28363 bytes)
09-28 21:32 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
09-28 21:32 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
09-28 21:32 DEBUG  downloader: download finished (read 874 bytes)
09-28 21:32 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
09-28 21:32 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
09-28 21:32 DEBUG  downloader: download finished (read 198 bytes)
09-28 21:32 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-28 21:32 INFO   saplog: Checking block bindings..
09-28 21:32 INFO   saplog: Key verified successfully.
09-28 21:32 DEBUG  CommonBackend: metalink md5sums:
a941ca07230dd2a812b5abd3aa12f79f  ubuntu-11.04-alternate-amd64.metalink
ec67d129102bbe53715c0a192c6e703b  ubuntu-11.04-alternate-i386.metalink
350c4c0da5823625e5278cc869153e65  ubuntu-11.04-beta2-alternate-amd64.metalink
10eb1df66373fd00cd9be2acfc329bf3  ubuntu-11.04-beta2-alternate-i386.metalink
7b3ef94055a263d7f7f9b1ed6e3c99e2  ubuntu-11.04-beta2-desktop-amd64.metalink
84b89292c5ae40be000a5ee861da257e  ubuntu-11.04-beta2-desktop-i386.metalink
d39c949129feb09da7e349882833f488  ubuntu-11.04-beta2-server-amd64.metalink
b7be563bfb89faaa4c7bd892a1a56aa1  ubuntu-11.04-beta2-server-i386.metalink
42aa52e7eaa441d0b00965d225f4e44f  ubuntu-11.04-desktop-amd64.metalink
8376ce671b922bd1051f16ab2d44d06f  ubuntu-11.04-desktop-i386.metalink
e23ed6d1164876804a7fb9dfb2f8aee1  ubuntu-11.04-server-amd64.metalink
b4b50d20f519fd0d8761e9d998630449  ubuntu-11.04-server-i386.metalink

09-28 21:32 DEBUG  TaskList: ### Finished get_metalink
09-28 21:32 DEBUG  TaskList: New task download
09-28 21:32 DEBUG  TaskList: ### Running download...
09-28 21:32 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
09-28 21:43 INFO   WindowsFrontend: Operation cancelled
09-28 21:43 DEBUG  WindowsFrontend: frontend.quit
09-28 21:43 DEBUG  WindowsFrontend: frontend.on_quit
09-28 21:43 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-28 21:43 DEBUG  TaskList: # Cancelling tasklist
09-28 21:43 DEBUG  TaskList: ### Finished download
09-28 21:43 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-28 21:43 DEBUG  root: application.on_quit
09-28 21:43 DEBUG  root: Forceful exit
09-28 21:43 INFO   root: sys.exit
09-29 13:11 INFO   root: === wubi 11.04 rev211 ===
09-29 13:11 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 13:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 13:11 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\data
09-29 13:11 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\bin\7z.exe
09-29 13:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 13:11 DEBUG  CommonBackend: Fetching basic info...
09-29 13:11 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 13:11 DEBUG  CommonBackend: platform=win32
09-29 13:11 DEBUG  CommonBackend: osname=nt
09-29 13:11 DEBUG  CommonBackend: language=en_US
09-29 13:11 DEBUG  CommonBackend: encoding=cp1252
09-29 13:11 DEBUG  WindowsBackend: arch=amd64
09-29 13:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\data\isolist.ini
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 13:11 DEBUG  WindowsBackend: Fetching host info...
09-29 13:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 13:11 DEBUG  WindowsBackend: windows version=vista
09-29 13:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 13:11 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 13:11 DEBUG  WindowsBackend: windows_build=7601
09-29 13:11 DEBUG  WindowsBackend: gmt=-6
09-29 13:11 DEBUG  WindowsBackend: country=US
09-29 13:11 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 13:11 DEBUG  WindowsBackend: windows_username=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 13:11 DEBUG  WindowsBackend: windows_language_code=1033
09-29 13:11 DEBUG  WindowsBackend: windows_language=English
09-29 13:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 13:11 DEBUG  WindowsBackend: bootloader=vista
09-29 13:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209610.308594 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: drive=Drive(C: hd 209610.308594 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 13:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 13:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-29 13:11 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 13:11 DEBUG  WindowsBackend: keyboard_layout=us
09-29 13:11 DEBUG  WindowsBackend: keyboard_variant=
09-29 13:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 13:11 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 13:11 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 13:11 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 13:11 DEBUG  CommonBackend: Searching for local CDs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Ubuntu Netbook CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\casper\filesystem.squashfs
09-29 13:11 INFO   root: Already installed, running the uninstaller...
09-29 13:11 INFO   root: Running the uninstaller...
09-29 13:11 INFO   CommonBackend: This is the uninstaller running
09-29 13:11 DEBUG  WindowsFrontend: __init__...
09-29 13:11 DEBUG  WindowsFrontend: on_init...
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl182E.tmp\translations, languages=['en_US', 'en']
09-29 13:11 INFO   root: === wubi 11.04 rev211 ===
09-29 13:11 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 13:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 13:11 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\data
09-29 13:11 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\bin\7z.exe
09-29 13:11 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 13:11 DEBUG  CommonBackend: Fetching basic info...
09-29 13:11 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 13:11 DEBUG  CommonBackend: platform=win32
09-29 13:11 DEBUG  CommonBackend: osname=nt
09-29 13:11 DEBUG  CommonBackend: language=en_US
09-29 13:11 DEBUG  CommonBackend: encoding=cp1252
09-29 13:11 DEBUG  WindowsBackend: arch=amd64
09-29 13:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\data\isolist.ini
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 13:11 DEBUG  WindowsBackend: Fetching host info...
09-29 13:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 13:11 DEBUG  WindowsBackend: windows version=vista
09-29 13:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 13:11 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 13:11 DEBUG  WindowsBackend: windows_build=7601
09-29 13:11 DEBUG  WindowsBackend: gmt=-6
09-29 13:11 DEBUG  WindowsBackend: country=US
09-29 13:11 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 13:11 DEBUG  WindowsBackend: windows_username=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 13:11 DEBUG  WindowsBackend: windows_language_code=1033
09-29 13:11 DEBUG  WindowsBackend: windows_language=English
09-29 13:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 13:11 DEBUG  WindowsBackend: bootloader=vista
09-29 13:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209607.125 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: drive=Drive(C: hd 209607.125 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 13:11 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 13:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-29 13:11 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 13:11 DEBUG  WindowsBackend: keyboard_layout=us
09-29 13:11 DEBUG  WindowsBackend: keyboard_variant=
09-29 13:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 13:11 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 13:11 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 13:11 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 13:11 DEBUG  CommonBackend: Searching for local CDs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu Netbook CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 INFO   root: Already installed, running the uninstaller...
09-29 13:11 INFO   root: Running the uninstaller...
09-29 13:11 INFO   CommonBackend: This is the uninstaller running
09-29 13:11 DEBUG  WindowsFrontend: __init__...
09-29 13:11 DEBUG  WindowsFrontend: on_init...
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\translations, languages=['en_US', 'en']
09-29 13:11 INFO   root: Received settings
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\translations, languages=['en_US', 'en']
09-29 13:11 DEBUG  TaskList: # Running tasklist...
09-29 13:11 DEBUG  TaskList: ## Running Backup ISO...
09-29 13:11 DEBUG  TaskList: ## Finished Backup ISO
09-29 13:11 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 13:11 DEBUG  WindowsBackend: Could not find bcd id
09-29 13:11 DEBUG  WindowsBackend: undo_bootini C:
09-29 13:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 209607.125 mb free ntfs)
09-29 13:11 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 13:11 DEBUG  TaskList: ## Running Remove target dir...
09-29 13:11 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 13:11 DEBUG  WindowsFrontend: frontend.on_quit
09-29 13:11 DEBUG  root: application.on_quit
09-29 13:11 INFO   root: sys.exit
09-29 13:11 DEBUG  TaskList: ## Finished Remove target dir
09-29 13:11 DEBUG  TaskList: ## Running Remove registry key...
09-29 13:11 DEBUG  TaskList: ## Finished Remove registry key
09-29 13:11 DEBUG  TaskList: # Finished tasklist
09-29 13:11 INFO   root: Almost finished uninstalling
09-29 13:11 INFO   root: Finished uninstallation
09-29 13:11 DEBUG  CommonBackend: Fetching basic info...
09-29 13:11 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 13:11 DEBUG  CommonBackend: platform=win32
09-29 13:11 DEBUG  CommonBackend: osname=nt
09-29 13:11 DEBUG  WindowsBackend: arch=amd64
09-29 13:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\data\isolist.ini
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 13:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 13:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 13:11 DEBUG  WindowsBackend: Fetching host info...
09-29 13:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 13:11 DEBUG  WindowsBackend: windows version=vista
09-29 13:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 13:11 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 13:11 DEBUG  WindowsBackend: windows_build=7601
09-29 13:11 DEBUG  WindowsBackend: gmt=-6
09-29 13:11 DEBUG  WindowsBackend: country=US
09-29 13:11 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 13:11 DEBUG  WindowsBackend: windows_username=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 13:11 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 13:11 DEBUG  WindowsBackend: windows_language_code=1033
09-29 13:11 DEBUG  WindowsBackend: windows_language=English
09-29 13:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 13:11 DEBUG  WindowsBackend: bootloader=vista
09-29 13:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209760.953125 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: drive=Drive(C: hd 209760.953125 mb free ntfs)
09-29 13:11 DEBUG  WindowsBackend: uninstaller_path=None
09-29 13:11 DEBUG  WindowsBackend: previous_target_dir=None
09-29 13:11 DEBUG  WindowsBackend: previous_distro_name=None
09-29 13:11 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 13:11 DEBUG  WindowsBackend: keyboard_layout=us
09-29 13:11 DEBUG  WindowsBackend: keyboard_variant=
09-29 13:11 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 13:11 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 13:11 DEBUG  CommonBackend: Searching for local CDs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu Netbook CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Kubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Xubuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Mythbuntu CD
09-29 13:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:11 INFO   root: Running the installer...
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\translations, languages=['en_US', 'en']
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\translations, languages=['en_US', 'en']
09-29 13:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 13:11 INFO   root: Received settings
09-29 13:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\translations, languages=['en_US', 'en']
09-29 13:11 DEBUG  TaskList: # Running tasklist...
09-29 13:11 DEBUG  TaskList: ## Running select_target_dir...
09-29 13:11 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 13:11 DEBUG  TaskList: ## Finished select_target_dir
09-29 13:11 DEBUG  TaskList: ## Running create_dir_structure...
09-29 13:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 13:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 13:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 13:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 13:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 13:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 13:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 13:12 DEBUG  TaskList: ## Finished create_dir_structure
09-29 13:12 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 13:12 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 13:12 DEBUG  TaskList: ## Running create_uninstaller...
09-29 13:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 13:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 13:12 DEBUG  TaskList: ## Finished create_uninstaller
09-29 13:12 DEBUG  TaskList: ## Running copy_installation_files...
09-29 13:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 13:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\winboot -> C:\ubuntu\winboot
09-29 13:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 13:12 DEBUG  TaskList: ## Finished copy_installation_files
09-29 13:12 DEBUG  TaskList: ## Running get_iso...
09-29 13:12 DEBUG  CommonBackend: Searching for local CD
09-29 13:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp is a valid Ubuntu Netbook CD
09-29 13:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl27C8.tmp\casper\filesystem.squashfs
09-29 13:12 DEBUG  CommonBackend: Searching for local ISO
09-29 13:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 13:12 DEBUG  TaskList: New task get_metalink
09-29 13:12 DEBUG  TaskList: ### Running get_metalink...
09-29 13:12 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 13:12 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 13:12 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 13:12 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 13:12 DEBUG  TaskList: ### Finished get_metalink
09-29 13:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 13:12 DEBUG  TaskList: # Cancelling tasklist
09-29 13:12 DEBUG  TaskList: # Finished tasklist
09-29 13:12 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 13:14 INFO   root: === wubi 11.04 rev211 ===
09-29 13:14 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 13:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 13:14 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\data
09-29 13:14 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\bin\7z.exe
09-29 13:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 13:14 DEBUG  CommonBackend: Fetching basic info...
09-29 13:14 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 13:14 DEBUG  CommonBackend: platform=win32
09-29 13:14 DEBUG  CommonBackend: osname=nt
09-29 13:14 DEBUG  CommonBackend: language=en_US
09-29 13:14 DEBUG  CommonBackend: encoding=cp1252
09-29 13:14 DEBUG  WindowsBackend: arch=amd64
09-29 13:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\data\isolist.ini
09-29 13:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 13:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 13:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 13:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 13:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 13:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 13:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 13:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 13:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 13:14 DEBUG  WindowsBackend: Fetching host info...
09-29 13:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 13:14 DEBUG  WindowsBackend: windows version=vista
09-29 13:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 13:14 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 13:14 DEBUG  WindowsBackend: windows_build=7601
09-29 13:14 DEBUG  WindowsBackend: gmt=-6
09-29 13:14 DEBUG  WindowsBackend: country=US
09-29 13:14 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 13:14 DEBUG  WindowsBackend: windows_username=Natalie
09-29 13:14 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 13:14 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 13:14 DEBUG  WindowsBackend: windows_language_code=1033
09-29 13:14 DEBUG  WindowsBackend: windows_language=English
09-29 13:14 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 13:14 DEBUG  WindowsBackend: bootloader=vista
09-29 13:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209758.957031 mb free ntfs)
09-29 13:14 DEBUG  WindowsBackend: drive=Drive(C: hd 209758.957031 mb free ntfs)
09-29 13:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 13:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 13:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 13:14 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 13:14 DEBUG  WindowsBackend: keyboard_layout=us
09-29 13:14 DEBUG  WindowsBackend: keyboard_variant=
09-29 13:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 13:14 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 13:14 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 13:14 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 13:14 DEBUG  CommonBackend: Searching for local CDs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu Netbook CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Kubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Kubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Xubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Xubuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Mythbuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Mythbuntu CD
09-29 13:14 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:14 INFO   root: Already installed, running the uninstaller...
09-29 13:14 INFO   root: Running the uninstaller...
09-29 13:14 INFO   CommonBackend: This is the uninstaller running
09-29 13:14 DEBUG  WindowsFrontend: __init__...
09-29 13:14 DEBUG  WindowsFrontend: on_init...
09-29 13:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\translations, languages=['en_US', 'en']
09-29 13:15 INFO   root: Received settings
09-29 13:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\translations, languages=['en_US', 'en']
09-29 13:15 DEBUG  TaskList: # Running tasklist...
09-29 13:15 DEBUG  TaskList: ## Running Backup ISO...
09-29 13:15 DEBUG  TaskList: ## Finished Backup ISO
09-29 13:15 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 13:15 DEBUG  WindowsBackend: Could not find bcd id
09-29 13:15 DEBUG  WindowsBackend: undo_bootini C:
09-29 13:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 209758.957031 mb free ntfs)
09-29 13:15 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 13:15 DEBUG  TaskList: ## Running Remove target dir...
09-29 13:15 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 13:15 DEBUG  TaskList: ## Finished Remove target dir
09-29 13:15 DEBUG  TaskList: ## Running Remove registry key...
09-29 13:15 DEBUG  TaskList: ## Finished Remove registry key
09-29 13:15 DEBUG  TaskList: # Finished tasklist
09-29 13:15 INFO   root: Almost finished uninstalling
09-29 13:15 INFO   root: Finished uninstallation
09-29 13:15 DEBUG  CommonBackend: Fetching basic info...
09-29 13:15 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 13:15 DEBUG  CommonBackend: platform=win32
09-29 13:15 DEBUG  CommonBackend: osname=nt
09-29 13:15 DEBUG  WindowsBackend: arch=amd64
09-29 13:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\data\isolist.ini
09-29 13:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 13:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 13:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 13:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 13:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 13:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 13:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 13:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 13:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 13:15 DEBUG  WindowsBackend: Fetching host info...
09-29 13:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 13:15 DEBUG  WindowsBackend: windows version=vista
09-29 13:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 13:15 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 13:15 DEBUG  WindowsBackend: windows_build=7601
09-29 13:15 DEBUG  WindowsBackend: gmt=-6
09-29 13:15 DEBUG  WindowsBackend: country=US
09-29 13:15 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 13:15 DEBUG  WindowsBackend: windows_username=Natalie
09-29 13:15 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 13:15 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 13:15 DEBUG  WindowsBackend: windows_language_code=1033
09-29 13:15 DEBUG  WindowsBackend: windows_language=English
09-29 13:15 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 13:15 DEBUG  WindowsBackend: bootloader=vista
09-29 13:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 209760.472656 mb free ntfs)
09-29 13:15 DEBUG  WindowsBackend: drive=Drive(C: hd 209760.472656 mb free ntfs)
09-29 13:15 DEBUG  WindowsBackend: uninstaller_path=None
09-29 13:15 DEBUG  WindowsBackend: previous_target_dir=None
09-29 13:15 DEBUG  WindowsBackend: previous_distro_name=None
09-29 13:15 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 13:15 DEBUG  WindowsBackend: keyboard_layout=us
09-29 13:15 DEBUG  WindowsBackend: keyboard_variant=
09-29 13:15 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 13:15 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 13:15 DEBUG  CommonBackend: Searching for local CDs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu Netbook CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Kubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Kubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Xubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Xubuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Mythbuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Mythbuntu CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 INFO   root: Running the installer...
09-29 13:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\translations, languages=['en_US', 'en']
09-29 13:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\translations, languages=['en_US', 'en']
09-29 13:15 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 13:15 INFO   root: Received settings
09-29 13:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\translations, languages=['en_US', 'en']
09-29 13:15 DEBUG  TaskList: # Running tasklist...
09-29 13:15 DEBUG  TaskList: ## Running select_target_dir...
09-29 13:15 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 13:15 DEBUG  TaskList: ## Finished select_target_dir
09-29 13:15 DEBUG  TaskList: ## Running create_dir_structure...
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 13:15 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 13:15 DEBUG  TaskList: ## Finished create_dir_structure
09-29 13:15 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 13:15 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 13:15 DEBUG  TaskList: ## Running create_uninstaller...
09-29 13:15 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 13:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 13:15 DEBUG  TaskList: ## Finished create_uninstaller
09-29 13:15 DEBUG  TaskList: ## Running copy_installation_files...
09-29 13:15 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 13:15 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\winboot -> C:\ubuntu\winboot
09-29 13:15 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 13:15 DEBUG  TaskList: ## Finished copy_installation_files
09-29 13:15 DEBUG  TaskList: ## Running get_iso...
09-29 13:15 DEBUG  CommonBackend: Searching for local CD
09-29 13:15 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp is a valid Ubuntu Netbook CD
09-29 13:15 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl8DAB.tmp\casper\filesystem.squashfs
09-29 13:15 DEBUG  CommonBackend: Searching for local ISO
09-29 13:15 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 13:15 DEBUG  TaskList: New task get_metalink
09-29 13:15 DEBUG  TaskList: ### Running get_metalink...
09-29 13:15 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 13:15 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 13:15 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 13:15 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 13:15 DEBUG  TaskList: ### Finished get_metalink
09-29 13:15 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 13:15 DEBUG  TaskList: # Cancelling tasklist
09-29 13:15 DEBUG  TaskList: # Finished tasklist
09-29 13:15 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 14:10 INFO   root: === wubi 11.04 rev211 ===
09-29 14:10 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 14:10 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 14:10 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\data
09-29 14:10 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\bin\7z.exe
09-29 14:10 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 14:10 DEBUG  CommonBackend: Fetching basic info...
09-29 14:10 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 14:10 DEBUG  CommonBackend: platform=win32
09-29 14:10 DEBUG  CommonBackend: osname=nt
09-29 14:10 DEBUG  CommonBackend: language=en_US
09-29 14:10 DEBUG  CommonBackend: encoding=cp1252
09-29 14:10 DEBUG  WindowsBackend: arch=amd64
09-29 14:10 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\data\isolist.ini
09-29 14:10 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 14:10 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 14:10 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 14:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 14:10 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 14:10 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 14:10 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 14:10 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 14:10 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 14:10 DEBUG  WindowsBackend: Fetching host info...
09-29 14:10 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 14:10 DEBUG  WindowsBackend: windows version=vista
09-29 14:10 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 14:10 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 14:10 DEBUG  WindowsBackend: windows_build=7601
09-29 14:10 DEBUG  WindowsBackend: gmt=-6
09-29 14:10 DEBUG  WindowsBackend: country=US
09-29 14:10 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 14:10 DEBUG  WindowsBackend: windows_username=Natalie
09-29 14:10 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 14:10 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 14:10 DEBUG  WindowsBackend: windows_language_code=1033
09-29 14:10 DEBUG  WindowsBackend: windows_language=English
09-29 14:10 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 14:10 DEBUG  WindowsBackend: bootloader=vista
09-29 14:10 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208725.65625 mb free ntfs)
09-29 14:10 DEBUG  WindowsBackend: drive=Drive(C: hd 208725.65625 mb free ntfs)
09-29 14:10 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 14:10 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 14:10 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 14:10 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 14:10 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 14:10 DEBUG  WindowsBackend: keyboard_layout=us
09-29 14:10 DEBUG  WindowsBackend: keyboard_variant=
09-29 14:10 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 14:10 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 14:10 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 14:10 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 14:10 DEBUG  CommonBackend: Searching for local CDs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu Netbook CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Kubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Kubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Xubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Xubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Mythbuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Mythbuntu CD
09-29 14:10 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:10 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:10 INFO   root: Already installed, running the uninstaller...
09-29 14:10 INFO   root: Running the uninstaller...
09-29 14:10 INFO   CommonBackend: This is the uninstaller running
09-29 14:10 DEBUG  WindowsFrontend: __init__...
09-29 14:11 DEBUG  WindowsFrontend: on_init...
09-29 14:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\translations, languages=['en_US', 'en']
09-29 14:11 INFO   root: Received settings
09-29 14:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\translations, languages=['en_US', 'en']
09-29 14:11 DEBUG  TaskList: # Running tasklist...
09-29 14:11 DEBUG  TaskList: ## Running Backup ISO...
09-29 14:11 DEBUG  TaskList: ## Finished Backup ISO
09-29 14:11 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 14:11 DEBUG  WindowsBackend: Could not find bcd id
09-29 14:11 DEBUG  WindowsBackend: undo_bootini C:
09-29 14:11 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 208725.65625 mb free ntfs)
09-29 14:11 DEBUG  WindowsBackend: undo_bootini Q:
09-29 14:11 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-29 14:11 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 14:11 DEBUG  TaskList: ## Running Remove target dir...
09-29 14:11 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 14:11 DEBUG  TaskList: ## Finished Remove target dir
09-29 14:11 DEBUG  TaskList: ## Running Remove registry key...
09-29 14:11 DEBUG  TaskList: ## Finished Remove registry key
09-29 14:11 DEBUG  TaskList: # Finished tasklist
09-29 14:11 INFO   root: Almost finished uninstalling
09-29 14:11 INFO   root: Finished uninstallation
09-29 14:11 DEBUG  CommonBackend: Fetching basic info...
09-29 14:11 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 14:11 DEBUG  CommonBackend: platform=win32
09-29 14:11 DEBUG  CommonBackend: osname=nt
09-29 14:11 DEBUG  WindowsBackend: arch=amd64
09-29 14:11 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\data\isolist.ini
09-29 14:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 14:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 14:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 14:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 14:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 14:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 14:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 14:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 14:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 14:11 DEBUG  WindowsBackend: Fetching host info...
09-29 14:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 14:11 DEBUG  WindowsBackend: windows version=vista
09-29 14:11 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 14:11 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 14:11 DEBUG  WindowsBackend: windows_build=7601
09-29 14:11 DEBUG  WindowsBackend: gmt=-6
09-29 14:11 DEBUG  WindowsBackend: country=US
09-29 14:11 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 14:11 DEBUG  WindowsBackend: windows_username=Natalie
09-29 14:11 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 14:11 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 14:11 DEBUG  WindowsBackend: windows_language_code=1033
09-29 14:11 DEBUG  WindowsBackend: windows_language=English
09-29 14:11 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 14:11 DEBUG  WindowsBackend: bootloader=vista
09-29 14:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208727.292969 mb free ntfs)
09-29 14:11 DEBUG  WindowsBackend: drive=Drive(C: hd 208727.292969 mb free ntfs)
09-29 14:11 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 14:11 DEBUG  WindowsBackend: uninstaller_path=None
09-29 14:11 DEBUG  WindowsBackend: previous_target_dir=None
09-29 14:11 DEBUG  WindowsBackend: previous_distro_name=None
09-29 14:11 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 14:11 DEBUG  WindowsBackend: keyboard_layout=us
09-29 14:11 DEBUG  WindowsBackend: keyboard_variant=
09-29 14:11 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 14:11 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 14:11 DEBUG  CommonBackend: Searching for local CDs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu Netbook CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Kubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Kubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Xubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Xubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Mythbuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Mythbuntu CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 INFO   root: Running the installer...
09-29 14:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\translations, languages=['en_US', 'en']
09-29 14:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\translations, languages=['en_US', 'en']
09-29 14:11 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 14:11 INFO   root: Received settings
09-29 14:11 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\translations, languages=['en_US', 'en']
09-29 14:11 DEBUG  TaskList: # Running tasklist...
09-29 14:11 DEBUG  TaskList: ## Running select_target_dir...
09-29 14:11 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 14:11 DEBUG  TaskList: ## Finished select_target_dir
09-29 14:11 DEBUG  TaskList: ## Running create_dir_structure...
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 14:11 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 14:11 DEBUG  TaskList: ## Finished create_dir_structure
09-29 14:11 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 14:11 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 14:11 DEBUG  TaskList: ## Running create_uninstaller...
09-29 14:11 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 14:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 14:11 DEBUG  TaskList: ## Finished create_uninstaller
09-29 14:11 DEBUG  TaskList: ## Running copy_installation_files...
09-29 14:11 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 14:11 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\winboot -> C:\ubuntu\winboot
09-29 14:11 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 14:11 DEBUG  TaskList: ## Finished copy_installation_files
09-29 14:11 DEBUG  TaskList: ## Running get_iso...
09-29 14:11 DEBUG  CommonBackend: Searching for local CD
09-29 14:11 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp is a valid Ubuntu Netbook CD
09-29 14:11 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7D96.tmp\casper\filesystem.squashfs
09-29 14:11 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:11 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:11 DEBUG  CommonBackend: Searching for local ISO
09-29 14:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 14:11 DEBUG  TaskList: New task get_metalink
09-29 14:11 DEBUG  TaskList: ### Running get_metalink...
09-29 14:11 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 14:11 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 14:11 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 14:11 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 14:11 DEBUG  TaskList: ### Finished get_metalink
09-29 14:11 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 14:11 DEBUG  TaskList: # Cancelling tasklist
09-29 14:11 DEBUG  TaskList: # Finished tasklist
09-29 14:11 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 14:12 INFO   root: === wubi 11.04 rev211 ===
09-29 14:12 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 14:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 14:12 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\data
09-29 14:12 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\bin\7z.exe
09-29 14:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 14:12 DEBUG  CommonBackend: Fetching basic info...
09-29 14:12 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 14:12 DEBUG  CommonBackend: platform=win32
09-29 14:12 DEBUG  CommonBackend: osname=nt
09-29 14:12 DEBUG  CommonBackend: language=en_US
09-29 14:12 DEBUG  CommonBackend: encoding=cp1252
09-29 14:12 DEBUG  WindowsBackend: arch=amd64
09-29 14:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\data\isolist.ini
09-29 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 14:12 DEBUG  WindowsBackend: Fetching host info...
09-29 14:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 14:12 DEBUG  WindowsBackend: windows version=vista
09-29 14:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 14:12 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 14:12 DEBUG  WindowsBackend: windows_build=7601
09-29 14:12 DEBUG  WindowsBackend: gmt=-6
09-29 14:12 DEBUG  WindowsBackend: country=US
09-29 14:12 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 14:12 DEBUG  WindowsBackend: windows_username=Natalie
09-29 14:12 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 14:12 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 14:12 DEBUG  WindowsBackend: windows_language_code=1033
09-29 14:12 DEBUG  WindowsBackend: windows_language=English
09-29 14:12 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 14:12 DEBUG  WindowsBackend: bootloader=vista
09-29 14:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208725.296875 mb free ntfs)
09-29 14:12 DEBUG  WindowsBackend: drive=Drive(C: hd 208725.296875 mb free ntfs)
09-29 14:12 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 14:12 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 14:12 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 14:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 14:12 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 14:12 DEBUG  WindowsBackend: keyboard_layout=us
09-29 14:12 DEBUG  WindowsBackend: keyboard_variant=
09-29 14:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 14:12 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 14:12 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 14:12 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 14:12 DEBUG  CommonBackend: Searching for local CDs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 INFO   root: Already installed, running the uninstaller...
09-29 14:12 INFO   root: Running the uninstaller...
09-29 14:12 INFO   CommonBackend: This is the uninstaller running
09-29 14:12 DEBUG  WindowsFrontend: __init__...
09-29 14:12 DEBUG  WindowsFrontend: on_init...
09-29 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\translations, languages=['en_US', 'en']
09-29 14:12 INFO   root: Received settings
09-29 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\translations, languages=['en_US', 'en']
09-29 14:12 DEBUG  TaskList: # Running tasklist...
09-29 14:12 DEBUG  TaskList: ## Running Backup ISO...
09-29 14:12 DEBUG  TaskList: ## Finished Backup ISO
09-29 14:12 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 14:12 DEBUG  WindowsBackend: Could not find bcd id
09-29 14:12 DEBUG  WindowsBackend: undo_bootini C:
09-29 14:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 208725.296875 mb free ntfs)
09-29 14:12 DEBUG  WindowsBackend: undo_bootini Q:
09-29 14:12 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-29 14:12 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 14:12 DEBUG  TaskList: ## Running Remove target dir...
09-29 14:12 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 14:12 DEBUG  TaskList: ## Finished Remove target dir
09-29 14:12 DEBUG  TaskList: ## Running Remove registry key...
09-29 14:12 DEBUG  TaskList: ## Finished Remove registry key
09-29 14:12 DEBUG  TaskList: # Finished tasklist
09-29 14:12 INFO   root: Almost finished uninstalling
09-29 14:12 INFO   root: Finished uninstallation
09-29 14:12 DEBUG  CommonBackend: Fetching basic info...
09-29 14:12 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 14:12 DEBUG  CommonBackend: platform=win32
09-29 14:12 DEBUG  CommonBackend: osname=nt
09-29 14:12 DEBUG  WindowsBackend: arch=amd64
09-29 14:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\data\isolist.ini
09-29 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 14:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 14:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 14:12 DEBUG  WindowsBackend: Fetching host info...
09-29 14:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 14:12 DEBUG  WindowsBackend: windows version=vista
09-29 14:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 14:12 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 14:12 DEBUG  WindowsBackend: windows_build=7601
09-29 14:12 DEBUG  WindowsBackend: gmt=-6
09-29 14:12 DEBUG  WindowsBackend: country=US
09-29 14:12 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 14:12 DEBUG  WindowsBackend: windows_username=Natalie
09-29 14:12 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 14:12 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 14:12 DEBUG  WindowsBackend: windows_language_code=1033
09-29 14:12 DEBUG  WindowsBackend: windows_language=English
09-29 14:12 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 14:12 DEBUG  WindowsBackend: bootloader=vista
09-29 14:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208726.96875 mb free ntfs)
09-29 14:12 DEBUG  WindowsBackend: drive=Drive(C: hd 208726.96875 mb free ntfs)
09-29 14:12 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 14:12 DEBUG  WindowsBackend: uninstaller_path=None
09-29 14:12 DEBUG  WindowsBackend: previous_target_dir=None
09-29 14:12 DEBUG  WindowsBackend: previous_distro_name=None
09-29 14:12 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 14:12 DEBUG  WindowsBackend: keyboard_layout=us
09-29 14:12 DEBUG  WindowsBackend: keyboard_variant=
09-29 14:12 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 14:12 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 14:12 DEBUG  CommonBackend: Searching for local CDs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 INFO   root: Running the installer...
09-29 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\translations, languages=['en_US', 'en']
09-29 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\translations, languages=['en_US', 'en']
09-29 14:12 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 14:12 INFO   root: Received settings
09-29 14:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\translations, languages=['en_US', 'en']
09-29 14:12 DEBUG  TaskList: # Running tasklist...
09-29 14:12 DEBUG  TaskList: ## Running select_target_dir...
09-29 14:12 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 14:12 DEBUG  TaskList: ## Finished select_target_dir
09-29 14:12 DEBUG  TaskList: ## Running create_dir_structure...
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 14:12 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 14:12 DEBUG  TaskList: ## Finished create_dir_structure
09-29 14:12 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 14:12 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 14:12 DEBUG  TaskList: ## Running create_uninstaller...
09-29 14:12 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 14:12 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 14:12 DEBUG  TaskList: ## Finished create_uninstaller
09-29 14:12 DEBUG  TaskList: ## Running copy_installation_files...
09-29 14:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 14:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\winboot -> C:\ubuntu\winboot
09-29 14:12 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 14:12 DEBUG  TaskList: ## Finished copy_installation_files
09-29 14:12 DEBUG  TaskList: ## Running get_iso...
09-29 14:12 DEBUG  CommonBackend: Searching for local CD
09-29 14:12 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7CAC.tmp\casper\filesystem.squashfs
09-29 14:12 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 14:12 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 14:12 DEBUG  CommonBackend: Searching for local ISO
09-29 14:12 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 14:12 DEBUG  TaskList: New task get_metalink
09-29 14:12 DEBUG  TaskList: ### Running get_metalink...
09-29 14:12 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 14:12 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 14:12 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 14:12 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 14:12 DEBUG  TaskList: ### Finished get_metalink
09-29 14:12 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 14:12 DEBUG  TaskList: # Cancelling tasklist
09-29 14:12 DEBUG  TaskList: # Finished tasklist
09-29 14:12 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 21:38 INFO   root: === wubi 11.04 rev211 ===
09-29 21:38 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 21:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi(1).exe"']
09-29 21:38 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\data
09-29 21:38 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\bin\7z.exe
09-29 21:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 21:38 DEBUG  CommonBackend: Fetching basic info...
09-29 21:38 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi(1).exe
09-29 21:38 DEBUG  CommonBackend: platform=win32
09-29 21:38 DEBUG  CommonBackend: osname=nt
09-29 21:38 DEBUG  CommonBackend: language=en_US
09-29 21:38 DEBUG  CommonBackend: encoding=cp1252
09-29 21:38 DEBUG  WindowsBackend: arch=amd64
09-29 21:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\data\isolist.ini
09-29 21:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 21:38 DEBUG  WindowsBackend: Fetching host info...
09-29 21:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 21:38 DEBUG  WindowsBackend: windows version=vista
09-29 21:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 21:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 21:38 DEBUG  WindowsBackend: windows_build=7601
09-29 21:38 DEBUG  WindowsBackend: gmt=-6
09-29 21:38 DEBUG  WindowsBackend: country=US
09-29 21:38 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 21:38 DEBUG  WindowsBackend: windows_username=Natalie
09-29 21:38 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 21:38 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 21:38 DEBUG  WindowsBackend: windows_language_code=1033
09-29 21:38 DEBUG  WindowsBackend: windows_language=English
09-29 21:38 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 21:38 DEBUG  WindowsBackend: bootloader=vista
09-29 21:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208863.164063 mb free ntfs)
09-29 21:38 DEBUG  WindowsBackend: drive=Drive(C: hd 208863.164063 mb free ntfs)
09-29 21:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 21:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 21:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 21:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 21:38 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 21:38 DEBUG  WindowsBackend: keyboard_layout=us
09-29 21:38 DEBUG  WindowsBackend: keyboard_variant=
09-29 21:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 21:38 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 21:38 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 21:38 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 21:38 DEBUG  CommonBackend: Searching for local CDs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 INFO   root: Already installed, running the uninstaller...
09-29 21:38 INFO   root: Running the uninstaller...
09-29 21:38 INFO   CommonBackend: This is the uninstaller running
09-29 21:38 DEBUG  WindowsFrontend: __init__...
09-29 21:38 DEBUG  WindowsFrontend: on_init...
09-29 21:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\translations, languages=['en_US', 'en']
09-29 21:38 INFO   root: Received settings
09-29 21:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\translations, languages=['en_US', 'en']
09-29 21:38 DEBUG  TaskList: # Running tasklist...
09-29 21:38 DEBUG  TaskList: ## Running Backup ISO...
09-29 21:38 DEBUG  TaskList: ## Finished Backup ISO
09-29 21:38 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 21:38 DEBUG  WindowsBackend: Could not find bcd id
09-29 21:38 DEBUG  WindowsBackend: undo_bootini C:
09-29 21:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 208863.164063 mb free ntfs)
09-29 21:38 DEBUG  WindowsBackend: undo_bootini Q:
09-29 21:38 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-29 21:38 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 21:38 DEBUG  TaskList: ## Running Remove target dir...
09-29 21:38 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 21:38 DEBUG  TaskList: ## Finished Remove target dir
09-29 21:38 DEBUG  TaskList: ## Running Remove registry key...
09-29 21:38 DEBUG  TaskList: ## Finished Remove registry key
09-29 21:38 DEBUG  TaskList: # Finished tasklist
09-29 21:38 INFO   root: Almost finished uninstalling
09-29 21:38 INFO   root: Finished uninstallation
09-29 21:38 DEBUG  CommonBackend: Fetching basic info...
09-29 21:38 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi(1).exe
09-29 21:38 DEBUG  CommonBackend: platform=win32
09-29 21:38 DEBUG  CommonBackend: osname=nt
09-29 21:38 DEBUG  WindowsBackend: arch=amd64
09-29 21:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\data\isolist.ini
09-29 21:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 21:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 21:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 21:38 DEBUG  WindowsBackend: Fetching host info...
09-29 21:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 21:38 DEBUG  WindowsBackend: windows version=vista
09-29 21:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 21:38 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 21:38 DEBUG  WindowsBackend: windows_build=7601
09-29 21:38 DEBUG  WindowsBackend: gmt=-6
09-29 21:38 DEBUG  WindowsBackend: country=US
09-29 21:38 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 21:38 DEBUG  WindowsBackend: windows_username=Natalie
09-29 21:38 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 21:38 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 21:38 DEBUG  WindowsBackend: windows_language_code=1033
09-29 21:38 DEBUG  WindowsBackend: windows_language=English
09-29 21:38 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 21:38 DEBUG  WindowsBackend: bootloader=vista
09-29 21:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208864.347656 mb free ntfs)
09-29 21:38 DEBUG  WindowsBackend: drive=Drive(C: hd 208864.347656 mb free ntfs)
09-29 21:38 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 21:38 DEBUG  WindowsBackend: uninstaller_path=None
09-29 21:38 DEBUG  WindowsBackend: previous_target_dir=None
09-29 21:38 DEBUG  WindowsBackend: previous_distro_name=None
09-29 21:38 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 21:38 DEBUG  WindowsBackend: keyboard_layout=us
09-29 21:38 DEBUG  WindowsBackend: keyboard_variant=
09-29 21:38 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 21:38 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 21:38 DEBUG  CommonBackend: Searching for local CDs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 INFO   root: Running the installer...
09-29 21:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\translations, languages=['en_US', 'en']
09-29 21:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\translations, languages=['en_US', 'en']
09-29 21:38 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 21:38 INFO   root: Received settings
09-29 21:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\translations, languages=['en_US', 'en']
09-29 21:38 DEBUG  TaskList: # Running tasklist...
09-29 21:38 DEBUG  TaskList: ## Running select_target_dir...
09-29 21:38 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 21:38 DEBUG  TaskList: ## Finished select_target_dir
09-29 21:38 DEBUG  TaskList: ## Running create_dir_structure...
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 21:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 21:38 DEBUG  TaskList: ## Finished create_dir_structure
09-29 21:38 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 21:38 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 21:38 DEBUG  TaskList: ## Running create_uninstaller...
09-29 21:38 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi(1).exe -> C:\ubuntu\uninstall-wubi.exe
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 21:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 21:38 DEBUG  TaskList: ## Finished create_uninstaller
09-29 21:38 DEBUG  TaskList: ## Running copy_installation_files...
09-29 21:38 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 21:38 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\winboot -> C:\ubuntu\winboot
09-29 21:38 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 21:38 DEBUG  TaskList: ## Finished copy_installation_files
09-29 21:38 DEBUG  TaskList: ## Running get_iso...
09-29 21:38 DEBUG  CommonBackend: Searching for local CD
09-29 21:38 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl3571.tmp\casper\filesystem.squashfs
09-29 21:38 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:38 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:38 DEBUG  CommonBackend: Searching for local ISO
09-29 21:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 21:38 DEBUG  TaskList: New task get_metalink
09-29 21:38 DEBUG  TaskList: ### Running get_metalink...
09-29 21:38 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 21:38 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 21:38 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 21:38 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 21:38 DEBUG  TaskList: ### Finished get_metalink
09-29 21:38 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 21:38 DEBUG  TaskList: # Cancelling tasklist
09-29 21:38 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 21:38 DEBUG  TaskList: # Finished tasklist
09-29 21:40 INFO   root: === wubi 11.04 rev211 ===
09-29 21:40 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 21:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi(1).exe"']
09-29 21:40 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\data
09-29 21:40 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\bin\7z.exe
09-29 21:40 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 21:40 DEBUG  CommonBackend: Fetching basic info...
09-29 21:40 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi(1).exe
09-29 21:40 DEBUG  CommonBackend: platform=win32
09-29 21:40 DEBUG  CommonBackend: osname=nt
09-29 21:40 DEBUG  CommonBackend: language=en_US
09-29 21:40 DEBUG  CommonBackend: encoding=cp1252
09-29 21:40 DEBUG  WindowsBackend: arch=amd64
09-29 21:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\data\isolist.ini
09-29 21:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 21:40 DEBUG  WindowsBackend: Fetching host info...
09-29 21:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 21:40 DEBUG  WindowsBackend: windows version=vista
09-29 21:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 21:40 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 21:40 DEBUG  WindowsBackend: windows_build=7601
09-29 21:40 DEBUG  WindowsBackend: gmt=-6
09-29 21:40 DEBUG  WindowsBackend: country=US
09-29 21:40 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 21:40 DEBUG  WindowsBackend: windows_username=Natalie
09-29 21:40 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 21:40 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 21:40 DEBUG  WindowsBackend: windows_language_code=1033
09-29 21:40 DEBUG  WindowsBackend: windows_language=English
09-29 21:40 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 21:40 DEBUG  WindowsBackend: bootloader=vista
09-29 21:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208833.628906 mb free ntfs)
09-29 21:40 DEBUG  WindowsBackend: drive=Drive(C: hd 208833.628906 mb free ntfs)
09-29 21:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 21:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 21:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 21:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 21:40 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 21:40 DEBUG  WindowsBackend: keyboard_layout=us
09-29 21:40 DEBUG  WindowsBackend: keyboard_variant=
09-29 21:40 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 21:40 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 21:40 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 21:40 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 21:40 DEBUG  CommonBackend: Searching for local CDs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 INFO   root: Already installed, running the uninstaller...
09-29 21:40 INFO   root: Running the uninstaller...
09-29 21:40 INFO   CommonBackend: This is the uninstaller running
09-29 21:40 DEBUG  WindowsFrontend: __init__...
09-29 21:40 DEBUG  WindowsFrontend: on_init...
09-29 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\translations, languages=['en_US', 'en']
09-29 21:40 INFO   root: Received settings
09-29 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\translations, languages=['en_US', 'en']
09-29 21:40 DEBUG  TaskList: # Running tasklist...
09-29 21:40 DEBUG  TaskList: ## Running Backup ISO...
09-29 21:40 DEBUG  TaskList: ## Finished Backup ISO
09-29 21:40 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 21:40 DEBUG  WindowsBackend: Could not find bcd id
09-29 21:40 DEBUG  WindowsBackend: undo_bootini C:
09-29 21:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 208833.628906 mb free ntfs)
09-29 21:40 DEBUG  WindowsBackend: undo_bootini Q:
09-29 21:40 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-29 21:40 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 21:40 DEBUG  TaskList: ## Running Remove target dir...
09-29 21:40 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 21:40 DEBUG  TaskList: ## Finished Remove target dir
09-29 21:40 DEBUG  TaskList: ## Running Remove registry key...
09-29 21:40 DEBUG  TaskList: ## Finished Remove registry key
09-29 21:40 DEBUG  TaskList: # Finished tasklist
09-29 21:40 INFO   root: Almost finished uninstalling
09-29 21:40 INFO   root: Finished uninstallation
09-29 21:40 DEBUG  CommonBackend: Fetching basic info...
09-29 21:40 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi(1).exe
09-29 21:40 DEBUG  CommonBackend: platform=win32
09-29 21:40 DEBUG  CommonBackend: osname=nt
09-29 21:40 DEBUG  WindowsBackend: arch=amd64
09-29 21:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\data\isolist.ini
09-29 21:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 21:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 21:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 21:40 DEBUG  WindowsBackend: Fetching host info...
09-29 21:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 21:40 DEBUG  WindowsBackend: windows version=vista
09-29 21:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 21:40 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 21:40 DEBUG  WindowsBackend: windows_build=7601
09-29 21:40 DEBUG  WindowsBackend: gmt=-6
09-29 21:40 DEBUG  WindowsBackend: country=US
09-29 21:40 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 21:40 DEBUG  WindowsBackend: windows_username=Natalie
09-29 21:40 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 21:40 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 21:40 DEBUG  WindowsBackend: windows_language_code=1033
09-29 21:40 DEBUG  WindowsBackend: windows_language=English
09-29 21:40 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 21:40 DEBUG  WindowsBackend: bootloader=vista
09-29 21:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 208835.265625 mb free ntfs)
09-29 21:40 DEBUG  WindowsBackend: drive=Drive(C: hd 208835.265625 mb free ntfs)
09-29 21:40 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 21:40 DEBUG  WindowsBackend: uninstaller_path=None
09-29 21:40 DEBUG  WindowsBackend: previous_target_dir=None
09-29 21:40 DEBUG  WindowsBackend: previous_distro_name=None
09-29 21:40 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 21:40 DEBUG  WindowsBackend: keyboard_layout=us
09-29 21:40 DEBUG  WindowsBackend: keyboard_variant=
09-29 21:40 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 21:40 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 21:40 DEBUG  CommonBackend: Searching for local CDs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 INFO   root: Running the installer...
09-29 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\translations, languages=['en_US', 'en']
09-29 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\translations, languages=['en_US', 'en']
09-29 21:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 21:40 INFO   root: Received settings
09-29 21:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\translations, languages=['en_US', 'en']
09-29 21:40 DEBUG  TaskList: # Running tasklist...
09-29 21:40 DEBUG  TaskList: ## Running select_target_dir...
09-29 21:40 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 21:40 DEBUG  TaskList: ## Finished select_target_dir
09-29 21:40 DEBUG  TaskList: ## Running create_dir_structure...
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 21:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 21:40 DEBUG  TaskList: ## Finished create_dir_structure
09-29 21:40 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 21:40 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 21:40 DEBUG  TaskList: ## Running create_uninstaller...
09-29 21:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi(1).exe -> C:\ubuntu\uninstall-wubi.exe
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 21:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 21:40 DEBUG  TaskList: ## Finished create_uninstaller
09-29 21:40 DEBUG  TaskList: ## Running copy_installation_files...
09-29 21:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 21:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\winboot -> C:\ubuntu\winboot
09-29 21:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 21:40 DEBUG  TaskList: ## Finished copy_installation_files
09-29 21:40 DEBUG  TaskList: ## Running get_iso...
09-29 21:40 DEBUG  CommonBackend: Searching for local CD
09-29 21:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2A3B.tmp\casper\filesystem.squashfs
09-29 21:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 21:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 21:40 DEBUG  CommonBackend: Searching for local ISO
09-29 21:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 21:40 DEBUG  TaskList: New task get_metalink
09-29 21:40 DEBUG  TaskList: ### Running get_metalink...
09-29 21:40 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 21:40 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 21:40 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 21:40 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 21:40 DEBUG  TaskList: ### Finished get_metalink
09-29 21:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 21:40 DEBUG  TaskList: # Cancelling tasklist
09-29 21:40 DEBUG  TaskList: # Finished tasklist
09-29 21:40 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 22:36 INFO   root: === wubi 11.04 rev211 ===
09-29 22:36 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 22:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
09-29 22:36 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\data
09-29 22:36 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\bin\7z.exe
09-29 22:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 22:36 DEBUG  CommonBackend: Fetching basic info...
09-29 22:36 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
09-29 22:36 DEBUG  CommonBackend: platform=win32
09-29 22:36 DEBUG  CommonBackend: osname=nt
09-29 22:36 DEBUG  CommonBackend: language=en_US
09-29 22:36 DEBUG  CommonBackend: encoding=cp1252
09-29 22:36 DEBUG  WindowsBackend: arch=amd64
09-29 22:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\data\isolist.ini
09-29 22:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 22:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 22:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 22:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 22:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 22:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 22:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 22:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 22:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 22:36 DEBUG  WindowsBackend: Fetching host info...
09-29 22:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 22:36 DEBUG  WindowsBackend: windows version=vista
09-29 22:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 22:36 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 22:36 DEBUG  WindowsBackend: windows_build=7601
09-29 22:36 DEBUG  WindowsBackend: gmt=-6
09-29 22:36 DEBUG  WindowsBackend: country=US
09-29 22:36 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 22:36 DEBUG  WindowsBackend: windows_username=Natalie
09-29 22:36 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 22:36 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 22:36 DEBUG  WindowsBackend: windows_language_code=1033
09-29 22:36 DEBUG  WindowsBackend: windows_language=English
09-29 22:36 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 22:36 DEBUG  WindowsBackend: bootloader=vista
09-29 22:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207862.980469 mb free ntfs)
09-29 22:36 DEBUG  WindowsBackend: drive=Drive(C: hd 207862.980469 mb free ntfs)
09-29 22:36 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 22:36 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-29 22:36 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-29 22:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-29 22:36 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 22:36 DEBUG  WindowsBackend: keyboard_layout=us
09-29 22:36 DEBUG  WindowsBackend: keyboard_variant=
09-29 22:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 22:36 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 22:36 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 22:36 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 22:36 DEBUG  CommonBackend: Searching for local CDs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Ubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Ubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Ubuntu Netbook CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Kubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Kubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Xubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Xubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Mythbuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp is a valid Mythbuntu CD
09-29 22:36 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:36 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:36 INFO   root: Running the uninstaller...
09-29 22:36 INFO   CommonBackend: This is the uninstaller running
09-29 22:36 DEBUG  WindowsFrontend: __init__...
09-29 22:36 DEBUG  WindowsFrontend: on_init...
09-29 22:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\translations, languages=['en_US', 'en']
09-29 22:36 INFO   root: Received settings
09-29 22:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7EE0.tmp\translations, languages=['en_US', 'en']
09-29 22:36 DEBUG  TaskList: # Running tasklist...
09-29 22:36 DEBUG  TaskList: ## Running Backup ISO...
09-29 22:36 DEBUG  TaskList: ## Finished Backup ISO
09-29 22:36 DEBUG  TaskList: ## Running Remove bootloader entry...
09-29 22:36 DEBUG  WindowsBackend: Could not find bcd id
09-29 22:36 DEBUG  WindowsBackend: undo_bootini C:
09-29 22:36 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 207862.980469 mb free ntfs)
09-29 22:36 DEBUG  WindowsBackend: undo_bootini Q:
09-29 22:36 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-29 22:36 DEBUG  TaskList: ## Finished Remove bootloader entry
09-29 22:36 DEBUG  TaskList: ## Running Remove target dir...
09-29 22:36 DEBUG  CommonBackend: Deleting C:\ubuntu
09-29 22:36 ERROR  TaskList: [Errno 41] Directory not empty removing C:\ubuntu
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 41] Directory not empty removing C:\ubuntu
09-29 22:36 DEBUG  TaskList: # Cancelling tasklist
09-29 22:36 DEBUG  TaskList: # Finished tasklist
09-29 22:36 ERROR  root: [Errno 41] Directory not empty removing C:\ubuntu
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 41] Directory not empty removing C:\ubuntu
09-29 22:37 INFO   root: === wubi 11.04 rev211 ===
09-29 22:37 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 22:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-29 22:37 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\data
09-29 22:37 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\bin\7z.exe
09-29 22:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 22:37 DEBUG  CommonBackend: Fetching basic info...
09-29 22:37 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-29 22:37 DEBUG  CommonBackend: platform=win32
09-29 22:37 DEBUG  CommonBackend: osname=nt
09-29 22:37 DEBUG  CommonBackend: language=en_US
09-29 22:37 DEBUG  CommonBackend: encoding=cp1252
09-29 22:37 DEBUG  WindowsBackend: arch=amd64
09-29 22:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\data\isolist.ini
09-29 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 22:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 22:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 22:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 22:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 22:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 22:37 DEBUG  WindowsBackend: Fetching host info...
09-29 22:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 22:37 DEBUG  WindowsBackend: windows version=vista
09-29 22:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 22:37 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 22:37 DEBUG  WindowsBackend: windows_build=7601
09-29 22:37 DEBUG  WindowsBackend: gmt=-6
09-29 22:37 DEBUG  WindowsBackend: country=US
09-29 22:37 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 22:37 DEBUG  WindowsBackend: windows_username=Natalie
09-29 22:37 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 22:37 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 22:37 DEBUG  WindowsBackend: windows_language_code=1033
09-29 22:37 DEBUG  WindowsBackend: windows_language=English
09-29 22:37 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 22:37 DEBUG  WindowsBackend: bootloader=vista
09-29 22:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207866.597656 mb free ntfs)
09-29 22:37 DEBUG  WindowsBackend: drive=Drive(C: hd 207866.597656 mb free ntfs)
09-29 22:37 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 22:37 DEBUG  WindowsBackend: uninstaller_path=None
09-29 22:37 DEBUG  WindowsBackend: previous_target_dir=None
09-29 22:37 DEBUG  WindowsBackend: previous_distro_name=None
09-29 22:37 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 22:37 DEBUG  WindowsBackend: keyboard_layout=us
09-29 22:37 DEBUG  WindowsBackend: keyboard_variant=
09-29 22:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 22:37 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 22:37 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 22:37 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 22:37 DEBUG  CommonBackend: Searching for local CDs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Ubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Ubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Ubuntu Netbook CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Kubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Kubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Xubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Xubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Mythbuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp is a valid Mythbuntu CD
09-29 22:37 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:37 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:37 INFO   root: Running the installer...
09-29 22:37 DEBUG  WindowsFrontend: __init__...
09-29 22:37 DEBUG  WindowsFrontend: on_init...
09-29 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\translations, languages=['en_US', 'en']
09-29 22:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl7EA2.tmp\translations, languages=['en_US', 'en']
09-29 22:37 INFO   WindowsFrontend: Operation cancelled
09-29 22:37 DEBUG  WindowsFrontend: frontend.quit
09-29 22:37 DEBUG  WindowsFrontend: frontend.on_quit
09-29 22:37 DEBUG  root: application.on_quit
09-29 22:37 INFO   root: sys.exit
09-29 22:39 INFO   root: === wubi 11.04 rev211 ===
09-29 22:39 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-29 22:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi(1).exe"']
09-29 22:39 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\data
09-29 22:39 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\bin\7z.exe
09-29 22:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 22:39 DEBUG  CommonBackend: Fetching basic info...
09-29 22:39 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi(1).exe
09-29 22:39 DEBUG  CommonBackend: platform=win32
09-29 22:39 DEBUG  CommonBackend: osname=nt
09-29 22:39 DEBUG  CommonBackend: language=en_US
09-29 22:39 DEBUG  CommonBackend: encoding=cp1252
09-29 22:39 DEBUG  WindowsBackend: arch=amd64
09-29 22:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\data\isolist.ini
09-29 22:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 22:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 22:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 22:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 22:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 22:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 22:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 22:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 22:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-29 22:39 DEBUG  WindowsBackend: Fetching host info...
09-29 22:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 22:39 DEBUG  WindowsBackend: windows version=vista
09-29 22:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-29 22:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-29 22:39 DEBUG  WindowsBackend: windows_build=7601
09-29 22:39 DEBUG  WindowsBackend: gmt=-6
09-29 22:39 DEBUG  WindowsBackend: country=US
09-29 22:39 DEBUG  WindowsBackend: timezone=America/Chicago
09-29 22:39 DEBUG  WindowsBackend: windows_username=Natalie
09-29 22:39 DEBUG  WindowsBackend: user_full_name=Natalie
09-29 22:39 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-29 22:39 DEBUG  WindowsBackend: windows_language_code=1033
09-29 22:39 DEBUG  WindowsBackend: windows_language=English
09-29 22:39 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-29 22:39 DEBUG  WindowsBackend: bootloader=vista
09-29 22:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207862.917969 mb free ntfs)
09-29 22:39 DEBUG  WindowsBackend: drive=Drive(C: hd 207862.917969 mb free ntfs)
09-29 22:39 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-29 22:39 DEBUG  WindowsBackend: uninstaller_path=None
09-29 22:39 DEBUG  WindowsBackend: previous_target_dir=None
09-29 22:39 DEBUG  WindowsBackend: previous_distro_name=None
09-29 22:39 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 22:39 DEBUG  WindowsBackend: keyboard_layout=us
09-29 22:39 DEBUG  WindowsBackend: keyboard_variant=
09-29 22:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 22:39 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 22:39 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-29 22:39 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 22:39 DEBUG  CommonBackend: Searching for local CDs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Ubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Ubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Ubuntu Netbook CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Kubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Kubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Xubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Xubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Mythbuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Mythbuntu CD
09-29 22:39 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-29 22:39 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:39 INFO   root: Running the installer...
09-29 22:39 DEBUG  WindowsFrontend: __init__...
09-29 22:39 DEBUG  WindowsFrontend: on_init...
09-29 22:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\translations, languages=['en_US', 'en']
09-29 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\translations, languages=['en_US', 'en']
09-29 22:40 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-29 22:40 INFO   root: Received settings
09-29 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\translations, languages=['en_US', 'en']
09-29 22:40 DEBUG  TaskList: # Running tasklist...
09-29 22:40 DEBUG  TaskList: ## Running select_target_dir...
09-29 22:40 INFO   WindowsBackend: Installing into C:\ubuntu
09-29 22:40 DEBUG  TaskList: ## Finished select_target_dir
09-29 22:40 DEBUG  TaskList: ## Running create_dir_structure...
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-29 22:40 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-29 22:40 DEBUG  TaskList: ## Finished create_dir_structure
09-29 22:40 DEBUG  TaskList: ## Running uncompress_target_dir...
09-29 22:40 DEBUG  TaskList: ## Finished uncompress_target_dir
09-29 22:40 DEBUG  TaskList: ## Running create_uninstaller...
09-29 22:40 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi(1).exe -> C:\ubuntu\uninstall-wubi.exe
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-29 22:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-29 22:40 DEBUG  TaskList: ## Finished create_uninstaller
09-29 22:40 DEBUG  TaskList: ## Running copy_installation_files...
09-29 22:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-29 22:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\winboot -> C:\ubuntu\winboot
09-29 22:40 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-29 22:40 DEBUG  TaskList: ## Finished copy_installation_files
09-29 22:40 DEBUG  TaskList: ## Running get_iso...
09-29 22:40 DEBUG  CommonBackend: Searching for local CD
09-29 22:40 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp is a valid Ubuntu Netbook CD
09-29 22:40 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pylFBCC.tmp\casper\filesystem.squashfs
09-29 22:40 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-29 22:40 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-29 22:40 DEBUG  CommonBackend: Searching for local ISO
09-29 22:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-29 22:40 DEBUG  TaskList: New task get_metalink
09-29 22:40 DEBUG  TaskList: ### Running get_metalink...
09-29 22:40 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-29 22:40 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 22:40 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-29 22:40 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-29 22:40 DEBUG  TaskList: ### Finished get_metalink
09-29 22:40 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-29 22:40 DEBUG  TaskList: # Cancelling tasklist
09-29 22:40 DEBUG  TaskList: # Finished tasklist
09-29 22:40 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-30 08:07 INFO   root: === wubi 11.04 rev211 ===
09-30 08:07 DEBUG  root: Logfile is c:\users\natalie\appdata\local\temp\wubi-11.04-rev211.log
09-30 08:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Natalie\\Downloads\\wubi.exe"']
09-30 08:07 DEBUG  CommonBackend: data_dir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\data
09-30 08:07 DEBUG  WindowsBackend: 7z=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\bin\7z.exe
09-30 08:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-30 08:07 DEBUG  CommonBackend: Fetching basic info...
09-30 08:07 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-30 08:07 DEBUG  CommonBackend: platform=win32
09-30 08:07 DEBUG  CommonBackend: osname=nt
09-30 08:07 DEBUG  CommonBackend: language=en_US
09-30 08:07 DEBUG  CommonBackend: encoding=cp1252
09-30 08:07 DEBUG  WindowsBackend: arch=amd64
09-30 08:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\data\isolist.ini
09-30 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-30 08:07 DEBUG  WindowsBackend: Fetching host info...
09-30 08:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 08:07 DEBUG  WindowsBackend: windows version=vista
09-30 08:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-30 08:07 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-30 08:07 DEBUG  WindowsBackend: windows_build=7601
09-30 08:07 DEBUG  WindowsBackend: gmt=-6
09-30 08:07 DEBUG  WindowsBackend: country=US
09-30 08:07 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 08:07 DEBUG  WindowsBackend: windows_username=Natalie
09-30 08:07 DEBUG  WindowsBackend: user_full_name=Natalie
09-30 08:07 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-30 08:07 DEBUG  WindowsBackend: windows_language_code=1033
09-30 08:07 DEBUG  WindowsBackend: windows_language=English
09-30 08:07 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-30 08:07 DEBUG  WindowsBackend: bootloader=vista
09-30 08:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207838.898438 mb free ntfs)
09-30 08:07 DEBUG  WindowsBackend: drive=Drive(C: hd 207838.898438 mb free ntfs)
09-30 08:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-30 08:07 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
09-30 08:07 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
09-30 08:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook
09-30 08:07 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 08:07 DEBUG  WindowsBackend: keyboard_layout=us
09-30 08:07 DEBUG  WindowsBackend: keyboard_variant=
09-30 08:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-30 08:07 DEBUG  CommonBackend: locale=en_US.UTF-8
09-30 08:07 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-30 08:07 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 08:07 DEBUG  CommonBackend: Searching for local CDs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 INFO   root: Already installed, running the uninstaller...
09-30 08:07 INFO   root: Running the uninstaller...
09-30 08:07 INFO   CommonBackend: This is the uninstaller running
09-30 08:07 DEBUG  WindowsFrontend: __init__...
09-30 08:07 DEBUG  WindowsFrontend: on_init...
09-30 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\translations, languages=['en_US', 'en']
09-30 08:07 INFO   root: Received settings
09-30 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\translations, languages=['en_US', 'en']
09-30 08:07 DEBUG  TaskList: # Running tasklist...
09-30 08:07 DEBUG  TaskList: ## Running Backup ISO...
09-30 08:07 DEBUG  TaskList: ## Finished Backup ISO
09-30 08:07 DEBUG  TaskList: ## Running Remove bootloader entry...
09-30 08:07 DEBUG  WindowsBackend: Could not find bcd id
09-30 08:07 DEBUG  WindowsBackend: undo_bootini C:
09-30 08:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 207838.898438 mb free ntfs)
09-30 08:07 DEBUG  WindowsBackend: undo_bootini Q:
09-30 08:07 DEBUG  WindowsBackend: undo_configsys Drive(Q: hd 0.0 mb free )
09-30 08:07 DEBUG  TaskList: ## Finished Remove bootloader entry
09-30 08:07 DEBUG  TaskList: ## Running Remove target dir...
09-30 08:07 DEBUG  CommonBackend: Deleting C:\ubuntu
09-30 08:07 DEBUG  TaskList: ## Finished Remove target dir
09-30 08:07 DEBUG  TaskList: ## Running Remove registry key...
09-30 08:07 DEBUG  TaskList: ## Finished Remove registry key
09-30 08:07 DEBUG  TaskList: # Finished tasklist
09-30 08:07 INFO   root: Almost finished uninstalling
09-30 08:07 INFO   root: Finished uninstallation
09-30 08:07 DEBUG  CommonBackend: Fetching basic info...
09-30 08:07 DEBUG  CommonBackend: original_exe=C:\Users\Natalie\Downloads\wubi.exe
09-30 08:07 DEBUG  CommonBackend: platform=win32
09-30 08:07 DEBUG  CommonBackend: osname=nt
09-30 08:07 DEBUG  WindowsBackend: arch=amd64
09-30 08:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\data\isolist.ini
09-30 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-30 08:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-30 08:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-30 08:07 DEBUG  WindowsBackend: Fetching host info...
09-30 08:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-30 08:07 DEBUG  WindowsBackend: windows version=vista
09-30 08:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Starter
09-30 08:07 DEBUG  WindowsBackend: windows_sp=Service Pack 1
09-30 08:07 DEBUG  WindowsBackend: windows_build=7601
09-30 08:07 DEBUG  WindowsBackend: gmt=-6
09-30 08:07 DEBUG  WindowsBackend: country=US
09-30 08:07 DEBUG  WindowsBackend: timezone=America/Chicago
09-30 08:07 DEBUG  WindowsBackend: windows_username=Natalie
09-30 08:07 DEBUG  WindowsBackend: user_full_name=Natalie
09-30 08:07 DEBUG  WindowsBackend: user_directory=C:\Users\Natalie
09-30 08:07 DEBUG  WindowsBackend: windows_language_code=1033
09-30 08:07 DEBUG  WindowsBackend: windows_language=English
09-30 08:07 DEBUG  WindowsBackend: processor_name=Intel(R) Atom(TM) CPU N455   @ 1.66GHz
09-30 08:07 DEBUG  WindowsBackend: bootloader=vista
09-30 08:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 207840.535156 mb free ntfs)
09-30 08:07 DEBUG  WindowsBackend: drive=Drive(C: hd 207840.535156 mb free ntfs)
09-30 08:07 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
09-30 08:07 DEBUG  WindowsBackend: uninstaller_path=None
09-30 08:07 DEBUG  WindowsBackend: previous_target_dir=None
09-30 08:07 DEBUG  WindowsBackend: previous_distro_name=None
09-30 08:07 DEBUG  WindowsBackend: keyboard_id=67699721
09-30 08:07 DEBUG  WindowsBackend: keyboard_layout=us
09-30 08:07 DEBUG  WindowsBackend: keyboard_variant=
09-30 08:07 DEBUG  WindowsBackend: total_memory_mb=1013.421875
09-30 08:07 DEBUG  CommonBackend: Searching ISOs on USB devices
09-30 08:07 DEBUG  CommonBackend: Searching for local CDs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Kubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Xubuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Mythbuntu CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 INFO   root: Running the installer...
09-30 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\translations, languages=['en_US', 'en']
09-30 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\translations, languages=['en_US', 'en']
09-30 08:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu Netbook, language=en_US, locale=en_US.UTF-8, username=natalie
09-30 08:07 INFO   root: Received settings
09-30 08:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\translations, languages=['en_US', 'en']
09-30 08:07 DEBUG  TaskList: # Running tasklist...
09-30 08:07 DEBUG  TaskList: ## Running select_target_dir...
09-30 08:07 INFO   WindowsBackend: Installing into C:\ubuntu
09-30 08:07 DEBUG  TaskList: ## Finished select_target_dir
09-30 08:07 DEBUG  TaskList: ## Running create_dir_structure...
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
09-30 08:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
09-30 08:07 DEBUG  TaskList: ## Finished create_dir_structure
09-30 08:07 DEBUG  TaskList: ## Running uncompress_target_dir...
09-30 08:07 DEBUG  TaskList: ## Finished uncompress_target_dir
09-30 08:07 DEBUG  TaskList: ## Running create_uninstaller...
09-30 08:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Natalie\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook.ico
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
09-30 08:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
09-30 08:07 DEBUG  TaskList: ## Finished create_uninstaller
09-30 08:07 DEBUG  TaskList: ## Running copy_installation_files...
09-30 08:07 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
09-30 08:07 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\winboot -> C:\ubuntu\winboot
09-30 08:07 DEBUG  WindowsBackend: Copying C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\data\images\Ubuntu Netbook.ico -> C:\ubuntu\Ubuntu Netbook.ico
09-30 08:07 DEBUG  TaskList: ## Finished copy_installation_files
09-30 08:07 DEBUG  TaskList: ## Running get_iso...
09-30 08:07 DEBUG  CommonBackend: Searching for local CD
09-30 08:07 DEBUG  Distro:   checking whether C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain C:\Users\Natalie\AppData\Local\Temp\pyl2BDC.tmp\casper\filesystem.squashfs
09-30 08:07 DEBUG  Distro:   checking whether Q:\ is a valid Ubuntu Netbook CD
09-30 08:07 DEBUG  Distro:     does not contain Q:\casper\filesystem.squashfs
09-30 08:07 DEBUG  CommonBackend: Searching for local ISO
09-30 08:07 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-30 08:07 DEBUG  TaskList: New task get_metalink
09-30 08:07 DEBUG  TaskList: ### Running get_metalink...
09-30 08:07 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink > C:\ubuntu\install
09-30 08:07 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-30 08:07 DEBUG  downloader: downloading http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink > C:\ubuntu\install
09-30 08:07 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/ubuntu-netbook/daily-live/current/natty-netbook-i386.metalink err=[Errno 14] HTTP Error 404: Not Found
09-30 08:07 DEBUG  TaskList: ### Finished get_metalink
09-30 08:07 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
09-30 08:07 DEBUG  TaskList: # Cancelling tasklist
09-30 08:07 DEBUG  TaskList: # Finished tasklist
09-30 08:07 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO

```

---

### Post by bcbc on 2011-09-30
Natty doesn't have a netbook edition. It was left in wubi by accident. It's not needed because the netbook interface (from 10.10) is now the standard desktop interface. 

So just select Ubuntu.

---

### Post by natkill on 2011-10-01
I got the regular Ubuntu installed, but now I get the startup window welcoming me to Ubuntu, and I have a perpetual loading cursor until it finally just quits and I get a black screen full of text and it freezes, forcing me to reboot. The top menu bar only has the sound, internet, and timestamp or whatever it is in the top right corner, but no menu or app buttons. Is there a way to copy the code from when it freezes so I can show what happened?

---

### Post by bcbc on 2011-10-01
What is the brand/model of your computer? It's probably easier just to see if there already a documented workaround required for the computer than debug exactly where it is hanging.

edit: nevermind - I see you already mentioned it. Hold on I'll do some searches.

---

### Post by bcbc on 2011-10-01
I can't see anything specific for this model. There was a reported kernel panic [here]("http://ubuntuforums.org/showthread.php?p=11219797") on Natty.

This one states that it works great on Maverick 10.10 and has some info for the wireless card: [http://ubuntuforums.org/showthread.php?t=1687636](http://ubuntuforums.org/showthread.php?t=1687636)

Maybe try maverick - or you could try posting on that last thread and see if the original poster got it working in Natty and if there was anything special required to do this.

---

### Post by natkill on 2011-10-01
Yeah the kernal panic is what I'm getting. Thanks for all your help and finding the other thread, I posted in it asking about this computer and issues with natty.

---

