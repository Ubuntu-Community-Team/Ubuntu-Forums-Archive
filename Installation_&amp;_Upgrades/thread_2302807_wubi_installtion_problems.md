---
title: "wubi installtion problems"
date: 2015-11-13
forum: Installation &amp; Upgrades
---

### Post by KOUTRONAS_Mixalis on 2015-11-13
Hi to everyone i'm new to the forum and i don;t knot if the is the right place for my problem and if it is the right place to be posted but because it is an installation related issue i think i am in the right place i want to install lubuntu version lubuntu-14.04-desktop-i386 with wubi but it give me the error NameError: global name 'sig' is not defined im istalling from windows xpsp3
 so i post the log

```
11-13 19:19 INFO   root: === wubi 14.04 rev286 ===
11-13 19:19 DEBUG  root: Logfile is c:\docume~1\admin\locals~1\temp\wubi-14.04-rev286.log
11-13 19:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
11-13 19:19 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\data
11-13 19:19 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
11-13 19:19 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-13 19:19 DEBUG  CommonBackend: Fetching basic info...
11-13 19:19 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-13 19:19 DEBUG  CommonBackend: platform=win32
11-13 19:19 DEBUG  CommonBackend: osname=nt
11-13 19:19 DEBUG  CommonBackend: language=el_GR
11-13 19:19 DEBUG  CommonBackend: encoding=cp1253
11-13 19:19 DEBUG  WindowsBackend: arch=amd64
11-13 19:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
11-13 19:19 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-13 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
11-13 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 19:19 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 19:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
11-13 19:19 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-13 19:19 DEBUG  WindowsBackend: Fetching host info...
11-13 19:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 19:19 DEBUG  WindowsBackend: windows version=xp
11-13 19:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 19:19 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 19:19 DEBUG  WindowsBackend: windows_build=2600
11-13 19:19 DEBUG  WindowsBackend: gmt=2
11-13 19:19 DEBUG  WindowsBackend: country=GR
11-13 19:19 DEBUG  WindowsBackend: timezone=Europe/Athens
11-13 19:19 DEBUG  WindowsBackend: windows_username=Admin
11-13 19:19 DEBUG  WindowsBackend: user_full_name=Admin
11-13 19:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Admin
11-13 19:19 DEBUG  WindowsBackend: windows_language_code=1032
11-13 19:19 DEBUG  WindowsBackend: windows_language=Greek
11-13 19:19 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
11-13 19:19 DEBUG  WindowsBackend: bootloader=xp
11-13 19:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 31662.5546875 mb free ntfs)
11-13 19:19 DEBUG  WindowsBackend: drive=Drive(C: hd 31662.5546875 mb free ntfs)
11-13 19:19 DEBUG  WindowsBackend: drive=Drive(E: hd 322188.941406 mb free ntfs)
11-13 19:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-13 19:19 DEBUG  WindowsBackend: uninstaller_path=None
11-13 19:19 DEBUG  WindowsBackend: previous_target_dir=None
11-13 19:19 DEBUG  WindowsBackend: previous_distro_name=None
11-13 19:19 DEBUG  WindowsBackend: keyboard_id=-268368887
11-13 19:19 DEBUG  WindowsBackend: keyboard_layout=us
11-13 19:19 DEBUG  WindowsBackend: keyboard_variant=
11-13 19:19 DEBUG  CommonBackend: python locale=('el_GR', 'cp1253')
11-13 19:19 DEBUG  CommonBackend: locale=el_GR.UTF-8
11-13 19:19 DEBUG  WindowsBackend: total_memory_mb=2046.734375
11-13 19:19 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 19:19 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:19 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  WindowsBackend:   extracting .disk\info from C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro:   parsing info from str=Lubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20140416.2)
11-13 19:19 DEBUG  Distro:   parsed info={'name': 'Lubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140416.2', 'codename': 'Trusty Tahr', 'arch': 'i386'}
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Ubuntu
11-13 19:19 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:19 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:19 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:19 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:19 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro: wrong name: Lubuntu != Edubuntu
11-13 19:19 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:19 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  CommonBackend: Searching for local CDs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 INFO   root: Running the installer...
11-13 19:19 DEBUG  WindowsFrontend: __init__...
11-13 19:19 DEBUG  WindowsFrontend: on_init...
11-13 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\translations, languages=['el_GR', 'el']
11-13 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\translations, languages=['el_GR', 'el']
11-13 19:19 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Lubuntu, language=en_US, locale=en_US.UTF-8, username=mxalis
11-13 19:19 INFO   root: Received settings
11-13 19:19 DEBUG  CommonBackend: Searching for local CD
11-13 19:19 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:19 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:19 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:19 DEBUG  CommonBackend: Searching for local ISO
11-13 19:19 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\translations, languages=['en_US', 'en']
11-13 19:19 DEBUG  TaskList: # Running tasklist...
11-13 19:19 DEBUG  TaskList: ## Running select_target_dir...
11-13 19:19 INFO   WindowsBackend: Installing into C:\ubuntu
11-13 19:19 DEBUG  TaskList: ## Finished select_target_dir
11-13 19:19 DEBUG  TaskList: ## Running create_dir_structure...
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-13 19:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-13 19:19 DEBUG  TaskList: ## Finished create_dir_structure
11-13 19:19 DEBUG  TaskList: ## Running uncompress_target_dir...
11-13 19:19 DEBUG  TaskList: ## Finished uncompress_target_dir
11-13 19:19 DEBUG  TaskList: ## Running create_uninstaller...
11-13 19:19 DEBUG  WindowsBackend: Copying uninstaller C:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Lubuntu
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Lubuntu.ico
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 14.04-rev286
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Lubuntu
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://lubuntu.net](http://lubuntu.net)
11-13 19:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-13 19:19 DEBUG  TaskList: ## Finished create_uninstaller
11-13 19:19 DEBUG  TaskList: ## Running copy_installation_files...
11-13 19:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-13 19:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\winboot -> C:\ubuntu\winboot
11-13 19:19 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl1.tmp\data\images\Lubuntu.ico -> C:\ubuntu\Lubuntu.ico
11-13 19:19 DEBUG  TaskList: ## Finished copy_installation_files
11-13 19:19 DEBUG  TaskList: ## Running get_iso...
11-13 19:19 DEBUG  CommonBackend: Trying to use pre-specified ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  TaskList: New task is_valid_iso
11-13 19:19 DEBUG  TaskList: ### Running is_valid_iso...
11-13 19:19 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  TaskList: ### Finished is_valid_iso
11-13 19:19 DEBUG  TaskList: New task check_iso
11-13 19:19 DEBUG  TaskList: ### Running check_iso...
11-13 19:19 DEBUG  CommonBackend: Checking C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:19 DEBUG  CommonBackend: Using distro Lubuntu i386 instead of Lubuntu amd64
11-13 19:19 DEBUG  TaskList: New task get_metalink
11-13 19:19 DEBUG  TaskList: #### Running get_metalink...
11-13 19:19 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04-desktop-i386.metalink](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04-desktop-i386.metalink) > C:\ubuntu\install
11-13 19:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\lubuntu-14.04-desktop-i386.metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04-desktop-i386.metalink, basename=lubuntu-14.04-desktop-i386.metalink, length=1043, text=None
11-13 19:19 DEBUG  downloader: download finished (read 1043 bytes)
11-13 19:19 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink) > C:\ubuntu\install
11-13 19:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=1553, text=None
11-13 19:19 DEBUG  downloader: download finished (read 1553 bytes)
11-13 19:19 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink.gpg) > C:\ubuntu\install
11-13 19:19 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=933, text=None
11-13 19:19 DEBUG  downloader: download finished (read 933 bytes)
11-13 19:19 ERROR  TaskList: global name 'sig' is not defined
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 458, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 270, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 41, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1202, in verify_str
  File "\lib\openpgp\sap\api.py", line 1100, in verify_msg
  File "\lib\openpgp\sap\crypto.py", line 445, in verify
  File "\lib\openpgp\sap\crypto.py", line 174, in hash_context
NameError: global name 'sig' is not defined
11-13 19:19 DEBUG  TaskList: # Cancelling tasklist
11-13 19:19 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for C:\lubuntu-14.04-desktop-i386.iso, ignoring
11-13 19:19 DEBUG  TaskList: ### Finished check_iso
11-13 19:19 ERROR  root: global name 'sig' is not defined
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 458, in get_metalink
  File "\lib\wubi\backends\common\backend.py", line 270, in check_metalink
  File "\lib\wubi\backends\common\signature.py", line 41, in verify_gpg_signature
  File "\lib\openpgp\sap\api.py", line 1202, in verify_str
  File "\lib\openpgp\sap\api.py", line 1100, in verify_msg
  File "\lib\openpgp\sap\crypto.py", line 445, in verify
  File "\lib\openpgp\sap\crypto.py", line 174, in hash_context
NameError: global name 'sig' is not defined
11-13 19:19 DEBUG  TaskList: New task copy_file
11-13 19:19 DEBUG  CommonBackend: Copying C:\lubuntu-14.04-desktop-i386.iso > C:\ubuntu\install\installation.iso
11-13 19:19 DEBUG  TaskList: ## Finished get_iso
11-13 19:19 DEBUG  TaskList: # Finished tasklist
11-13 19:20 INFO   root: === wubi 14.04 rev286 ===
11-13 19:20 DEBUG  root: Logfile is c:\docume~1\admin\locals~1\temp\wubi-14.04-rev286.log
11-13 19:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\wubi.exe"']
11-13 19:20 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\data
11-13 19:20 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\bin\7z.exe
11-13 19:20 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
11-13 19:20 DEBUG  CommonBackend: Fetching basic info...
11-13 19:20 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-13 19:20 DEBUG  CommonBackend: platform=win32
11-13 19:20 DEBUG  CommonBackend: osname=nt
11-13 19:20 DEBUG  CommonBackend: language=el_GR
11-13 19:20 DEBUG  CommonBackend: encoding=cp1253
11-13 19:20 DEBUG  WindowsBackend: arch=amd64
11-13 19:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-13 19:20 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-13 19:20 DEBUG  WindowsBackend: Fetching host info...
11-13 19:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 19:20 DEBUG  WindowsBackend: windows version=xp
11-13 19:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 19:20 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 19:20 DEBUG  WindowsBackend: windows_build=2600
11-13 19:20 DEBUG  WindowsBackend: gmt=2
11-13 19:20 DEBUG  WindowsBackend: country=GR
11-13 19:20 DEBUG  WindowsBackend: timezone=Europe/Athens
11-13 19:20 DEBUG  WindowsBackend: windows_username=Admin
11-13 19:20 DEBUG  WindowsBackend: user_full_name=Admin
11-13 19:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Admin
11-13 19:20 DEBUG  WindowsBackend: windows_language_code=1032
11-13 19:20 DEBUG  WindowsBackend: windows_language=Greek
11-13 19:20 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
11-13 19:20 DEBUG  WindowsBackend: bootloader=xp
11-13 19:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 31659.5898438 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(C: hd 31659.5898438 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(E: hd 322188.941406 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-13 19:20 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-13 19:20 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-13 19:20 DEBUG  WindowsBackend: previous_distro_name=Lubuntu
11-13 19:20 DEBUG  WindowsBackend: keyboard_id=-268368887
11-13 19:20 DEBUG  WindowsBackend: keyboard_layout=us
11-13 19:20 DEBUG  WindowsBackend: keyboard_variant=
11-13 19:20 DEBUG  CommonBackend: python locale=('el_GR', 'cp1253')
11-13 19:20 DEBUG  CommonBackend: locale=el_GR.UTF-8
11-13 19:20 DEBUG  WindowsBackend: total_memory_mb=2046.734375
11-13 19:20 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  WindowsBackend:   extracting .disk\info from C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:   parsing info from str=Lubuntu 14.04 LTS "Trusty Tahr" - Release i386 (20140416.2)
11-13 19:20 DEBUG  Distro:   parsed info={'name': 'Lubuntu', 'subversion': 'Release', 'version': '14.04', 'build': '20140416.2', 'codename': 'Trusty Tahr', 'arch': 'i386'}
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Ubuntu
11-13 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:20 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Edubuntu
11-13 19:20 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:20 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  CommonBackend: Searching for local CDs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 INFO   root: Already installed, running the uninstaller...
11-13 19:20 INFO   root: Running the uninstaller...
11-13 19:20 INFO   CommonBackend: This is the uninstaller running
11-13 19:20 DEBUG  WindowsFrontend: __init__...
11-13 19:20 DEBUG  WindowsFrontend: on_init...
11-13 19:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\translations, languages=['el_GR', 'el']
11-13 19:20 INFO   root: Received settings
11-13 19:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\translations, languages=['el_GR', 'el']
11-13 19:20 DEBUG  TaskList: # Running tasklist...
11-13 19:20 DEBUG  TaskList: ## Running &#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951; &#954;&#945;&#964;&#945;&#967;&#974;&#961;&#953;&#963;&#951;&#962; &#949;&#954;&#954;&#953;&#957;&#951;&#964;&#942; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#953;&#954;&#959;&#973;...
11-13 19:20 ERROR  WindowsBackend: Cannot find bcdedit
11-13 19:20 DEBUG  WindowsBackend: undo_bootini C:
11-13 19:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 31659.5898438 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: undo_bootini E:
11-13 19:20 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 322188.941406 mb free ntfs)
11-13 19:20 DEBUG  TaskList: ## Finished &#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951; &#954;&#945;&#964;&#945;&#967;&#974;&#961;&#953;&#963;&#951;&#962; &#949;&#954;&#954;&#953;&#957;&#951;&#964;&#942; &#955;&#949;&#953;&#964;&#959;&#965;&#961;&#947;&#953;&#954;&#959;&#973;
11-13 19:20 DEBUG  TaskList: ## Running &#916;&#953;&#945;&#947;&#961;&#945;&#966;&#942; &#964;&#959;&#965; &#954;&#945;&#964;&#945;&#955;&#972;&#947;&#959;&#965; &#960;&#961;&#959;&#959;&#961;&#953;&#963;&#956;&#959;&#973;...
11-13 19:20 DEBUG  CommonBackend: Deleting C:\ubuntu
11-13 19:20 DEBUG  TaskList: ## Finished &#916;&#953;&#945;&#947;&#961;&#945;&#966;&#942; &#964;&#959;&#965; &#954;&#945;&#964;&#945;&#955;&#972;&#947;&#959;&#965; &#960;&#961;&#959;&#959;&#961;&#953;&#963;&#956;&#959;&#973;
11-13 19:20 DEBUG  TaskList: ## Running &#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951; &#954;&#955;&#949;&#953;&#948;&#953;&#959;&#973; &#956;&#951;&#964;&#961;&#974;&#959;&#965;...
11-13 19:20 DEBUG  TaskList: ## Finished &#913;&#966;&#945;&#943;&#961;&#949;&#963;&#951; &#954;&#955;&#949;&#953;&#948;&#953;&#959;&#973; &#956;&#951;&#964;&#961;&#974;&#959;&#965;
11-13 19:20 DEBUG  TaskList: # Finished tasklist
11-13 19:20 INFO   root: Almost finished uninstalling
11-13 19:20 INFO   root: Finished uninstallation
11-13 19:20 DEBUG  CommonBackend: Fetching basic info...
11-13 19:20 DEBUG  CommonBackend: original_exe=C:\wubi.exe
11-13 19:20 DEBUG  CommonBackend: platform=win32
11-13 19:20 DEBUG  CommonBackend: osname=nt
11-13 19:20 DEBUG  WindowsBackend: arch=amd64
11-13 19:20 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\data\isolist.ini
11-13 19:20 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 19:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
11-13 19:20 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-13 19:20 DEBUG  WindowsBackend: Fetching host info...
11-13 19:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 19:20 DEBUG  WindowsBackend: windows version=xp
11-13 19:20 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 19:20 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 19:20 DEBUG  WindowsBackend: windows_build=2600
11-13 19:20 DEBUG  WindowsBackend: gmt=2
11-13 19:20 DEBUG  WindowsBackend: country=GR
11-13 19:20 DEBUG  WindowsBackend: timezone=Europe/Athens
11-13 19:20 DEBUG  WindowsBackend: windows_username=Admin
11-13 19:20 DEBUG  WindowsBackend: user_full_name=Admin
11-13 19:20 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Admin
11-13 19:20 DEBUG  WindowsBackend: windows_language_code=1032
11-13 19:20 DEBUG  WindowsBackend: windows_language=Greek
11-13 19:20 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 Processor 3400+
11-13 19:20 DEBUG  WindowsBackend: bootloader=xp
11-13 19:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 31662.2226563 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(C: hd 31662.2226563 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(E: hd 322188.941406 mb free ntfs)
11-13 19:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
11-13 19:20 DEBUG  WindowsBackend: uninstaller_path=None
11-13 19:20 DEBUG  WindowsBackend: previous_target_dir=None
11-13 19:20 DEBUG  WindowsBackend: previous_distro_name=None
11-13 19:20 DEBUG  WindowsBackend: keyboard_id=-268368887
11-13 19:20 DEBUG  WindowsBackend: keyboard_layout=us
11-13 19:20 DEBUG  WindowsBackend: keyboard_variant=
11-13 19:20 DEBUG  WindowsBackend: total_memory_mb=2046.734375
11-13 19:20 DEBUG  CommonBackend: Checking pre-specified ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:20 DEBUG  Distro:   checking Ubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Ubuntu
11-13 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:20 DEBUG  Distro:   checking Kubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Kubuntu
11-13 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:20 DEBUG  Distro:   checking Mythbuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Mythbuntu
11-13 19:20 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro: wrong name: Lubuntu != Edubuntu
11-13 19:20 DEBUG  Distro:   checking Edubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  Distro:     does not contain casper\vmlinuz.efi
11-13 19:20 DEBUG  Distro:   checking Lubuntu ISO C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 INFO   Distro: Found a valid iso for Lubuntu: C:\lubuntu-14.04-desktop-i386.iso
11-13 19:20 DEBUG  CommonBackend: Searching for local CDs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
11-13 19:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
11-13 19:20 INFO   root: Running the installer...
11-13 19:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\translations, languages=['el_GR', 'el']
11-13 19:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Admin\LOCALS~1\Temp\pyl2.tmp\translations, languages=['el_GR', 'el']
11-13 19:20 INFO   WindowsFrontend: Operation cancelled
11-13 19:20 DEBUG  WindowsFrontend: frontend.quit
11-13 19:20 DEBUG  WindowsFrontend: frontend.on_quit
11-13 19:20 DEBUG  root: application.on_quit
11-13 19:20 INFO   root: sys.exit
```

i hope you to help me thanks

---

### Post by yancek on 2015-11-13
Wubi hasn't been developed or supported for over two years and people are discouraged from using it.  It will not be available on newer releases.  You should be able to get it to work on your outdated xp though.  I've never used WUBI do can't offer any suggestions.

---

### Post by KOUTRONAS_Mixalis on 2015-11-13
me neater but sometimes i want to do a quick compile on linux without having to format drives and without using a virtual machine  and you can remove it wenever you want it used to work before but for some reason its now give me this error

---

### Post by QIII on 2015-11-13
Again:  Wubi has been dropped by its developers and is not recommended for use.  It is not likely that anyone will be willing or able to help you with it any longer.

Also, please use code tags to enclose commands and results from the terminal.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by hakuna_matata on 2015-11-13
> ```
11-13 19:19 ERROR  TaskList: global name 'sig' is not defined
```
IMHO the real error message is "Unsupported signature hash algorithm" and refers to the downloaded file [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/MD5SUMS-metalink.gpg) . This file was changed yesterday. 

If you downloaded the right iso file, it is not necessary to enable internet connection during Windows part of installation....

---

