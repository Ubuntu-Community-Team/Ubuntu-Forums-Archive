---
title: "sos plz"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by Lord_karim on 2011-05-30
i did try  instal ubuntu 11.84  Wubi
but i don t  understand how fix this error message 

unicode encoder error : 'ascii' codec can t encode character u'\x89' in position 1 : ordinal not in range (128)

i have windows sp sp3
and i wana use ubuntu also 

plz if someone can understand this error ,i need help

---

### Post by linuxinstalledfromhdd on 2011-05-30
I would wipe the entire hard drive and start fresh with a disc of Ubuntu 10.10. 

Here is a really nice guide to help you through the process of having a perfect system setup:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by bcbc on 2011-05-31
> **Lord_karim said:**
> i did try  instal ubuntu 11.84  Wubi
but i don t  understand how fix this error message 

unicode encoder error : 'ascii' codec can t encode character u'\x89' in position 1 : ordinal not in range (128[SIZE="1"] [/SIZE])

i have windows sp sp3
and i wana use ubuntu also 

plz if someone can understand this error ,i need help

This error is likely due to non-ascii characters in the drive volume label, userid or path.

Try changing the drive label and see if it works.

PS here is a bug link with a similar sounding problem: [https://bugs.edge.launchpad.net/wubi/+bug/364600](https://bugs.edge.launchpad.net/wubi/+bug/364600)
If you'd like to, you can post your own wubi log file here to see if it's similar. To find it, open Windows Explorer, and enter %temp% in the address bar. Then look for the log file wubi-11.04-rev211.log and post it back here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

---

### Post by Lord_karim on 2011-05-31
```


05-30 01:57 INFO   root: === wubi 11.04 rev211 ===
05-30 01:57 DEBUG  root: Logfile is c:\docume~1\karim\locals~1\temp\wubi-11.04-rev211.log
05-30 01:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
05-30 01:57 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data
05-30 01:57 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
05-30 01:57 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Menu DÃ©marrer\Programmes\DÃ©marrage
05-30 01:57 DEBUG  CommonBackend: Fetching basic info...
05-30 01:57 DEBUG  CommonBackend: original_exe=E:\wubi.exe
05-30 01:57 DEBUG  CommonBackend: platform=win32
05-30 01:57 DEBUG  CommonBackend: osname=nt
05-30 01:57 DEBUG  CommonBackend: language=fr_FR
05-30 01:57 DEBUG  CommonBackend: encoding=cp1252
05-30 01:57 DEBUG  WindowsBackend: arch=i386
05-30 01:57 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
05-30 01:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-30 01:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-30 01:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-30 01:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-30 01:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-30 01:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-30 01:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-30 01:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-30 01:57 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-30 01:57 DEBUG  WindowsBackend: Fetching host info...
05-30 01:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-30 01:57 DEBUG  WindowsBackend: windows version=xp
05-30 01:57 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-30 01:57 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-30 01:57 DEBUG  WindowsBackend: windows_build=2600
05-30 01:57 DEBUG  WindowsBackend: gmt=1
05-30 01:57 DEBUG  WindowsBackend: country=FR
05-30 01:57 DEBUG  WindowsBackend: timezone=Europe/Paris
05-30 01:57 DEBUG  WindowsBackend: windows_username=KARIM
05-30 01:57 DEBUG  WindowsBackend: user_full_name=KARIM
05-30 01:57 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARIM
05-30 01:57 DEBUG  WindowsBackend: windows_language_code=1036
05-30 01:57 DEBUG  WindowsBackend: windows_language=French
05-30 01:57 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
05-30 01:57 DEBUG  WindowsBackend: bootloader=xp
05-30 01:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 113039.761719 mb free ntfs)
05-30 01:57 DEBUG  WindowsBackend: drive=Drive(C: hd 113039.761719 mb free ntfs)
05-30 01:57 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-30 01:57 DEBUG  WindowsBackend: drive=Drive(E: removable 6908.44921875 mb free ntfs)
05-30 01:57 DEBUG  WindowsBackend: uninstaller_path=None
05-30 01:57 DEBUG  WindowsBackend: previous_target_dir=None
05-30 01:57 DEBUG  WindowsBackend: previous_distro_name=None
05-30 01:57 DEBUG  WindowsBackend: keyboard_id=67896332
05-30 01:57 DEBUG  WindowsBackend: keyboard_layout=fr
05-30 01:57 DEBUG  WindowsBackend: keyboard_variant=
05-30 01:57 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1252')
05-30 01:57 DEBUG  CommonBackend: locale=fr_FR.UTF-8
05-30 01:57 DEBUG  WindowsBackend: total_memory_mb=502.046875
05-30 01:57 DEBUG  CommonBackend: Searching ISOs on USB devices
05-30 01:57 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
05-30 01:57 DEBUG  WindowsBackend:   extracting .disk\info from E:\ubuntu-11.04-desktop-i386.iso
05-30 01:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-30 01:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-30 01:57 DEBUG  Distro: wrong arch: i386 != amd64
05-30 01:57 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
05-30 01:57 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
05-30 01:57 DEBUG  CommonBackend: Searching for local CDs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-30 01:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-30 01:57 INFO   root: Running the installer...
05-30 01:57 DEBUG  WindowsFrontend: __init__...
05-30 01:57 DEBUG  WindowsFrontend: on_init...
05-30 01:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['fr_FR', 'fr']
05-30 01:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['fr_FR', 'fr']
05-30 01:58 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=fr_FR, locale=fr_FR.UTF-8, username=karim
05-30 01:58 INFO   root: Received settings
05-30 01:58 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['fr_FR', 'fr']
05-30 01:58 DEBUG  TaskList: # Running tasklist...
05-30 01:58 DEBUG  TaskList: ## Running select_target_dir...
05-30 01:58 INFO   WindowsBackend: Installing into C:\ubuntu
05-30 01:58 DEBUG  TaskList: ## Finished select_target_dir
05-30 01:58 DEBUG  TaskList: ## Running create_dir_structure...
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-30 01:58 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-30 01:58 DEBUG  TaskList: ## Finished create_dir_structure
05-30 01:58 DEBUG  TaskList: ## Running uncompress_target_dir...
05-30 01:58 DEBUG  TaskList: ## Finished uncompress_target_dir
05-30 01:58 DEBUG  TaskList: ## Running create_uninstaller...
05-30 01:58 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-30 01:58 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-30 01:58 DEBUG  TaskList: ## Finished create_uninstaller
05-30 01:58 DEBUG  TaskList: ## Running copy_installation_files...
05-30 01:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-30 01:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\winboot -> C:\ubuntu\winboot
05-30 01:58 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-30 01:58 DEBUG  TaskList: ## Finished copy_installation_files
05-30 01:58 DEBUG  TaskList: ## Running get_iso...
05-30 01:58 DEBUG  CommonBackend: Trying to use pre-specified ISO E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 DEBUG  TaskList: New task is_valid_iso
05-30 01:58 DEBUG  TaskList: ### Running is_valid_iso...
05-30 01:58 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 DEBUG  TaskList: ### Finished is_valid_iso
05-30 01:58 DEBUG  TaskList: New task check_iso
05-30 01:58 DEBUG  TaskList: ### Running check_iso...
05-30 01:58 DEBUG  CommonBackend: Checking E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 DEBUG  Distro:   checking Ubuntu ISO E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 INFO   Distro: Found a valid iso for Ubuntu: E:\ubuntu-11.04-desktop-i386.iso
05-30 01:58 DEBUG  TaskList: New task get_metalink
05-30 01:58 DEBUG  TaskList: #### Running get_metalink...
05-30 01:58 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink > C:\ubuntu\install
05-30 01:58 ERROR  CommonBackend: Cannot download metalink file http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-30 01:58 DEBUG  downloader: downloading http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink > C:\ubuntu\install
05-30 01:58 ERROR  CommonBackend: Cannot download metalink file2 http://cdimage.ubuntu.com/daily-live/current/natty-desktop-i386.metalink err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-30 01:58 DEBUG  TaskList: #### Finished get_metalink
05-30 01:58 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for E:\ubuntu-11.04-desktop-i386.iso, ignoring
05-30 01:58 DEBUG  TaskList: ### Finished check_iso
05-30 01:58 DEBUG  TaskList: New task copy_file
05-30 01:58 DEBUG  CommonBackend: Copying E:\ubuntu-11.04-desktop-i386.iso > C:\ubuntu\install\installation.iso
05-30 01:58 DEBUG  TaskList: ### Running copy_file...
05-30 01:59 DEBUG  TaskList: ### Finished copy_file
05-30 01:59 DEBUG  TaskList: ## Finished get_iso
05-30 01:59 DEBUG  TaskList: ## Running extract_kernel...
05-30 01:59 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\installation.iso
05-30 01:59 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\installation.iso
05-30 01:59 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\installation.iso
05-30 01:59 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\installation.iso
05-30 01:59 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-30 01:59 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-30 01:59 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
05-30 01:59 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-30 01:59 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
05-30 01:59 DEBUG  TaskList: ## Finished extract_kernel
05-30 01:59 DEBUG  TaskList: ## Running choose_disk_sizes...
05-30 01:59 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-30 01:59 DEBUG  TaskList: ## Finished choose_disk_sizes
05-30 01:59 DEBUG  TaskList: ## Running create_preseed...
05-30 01:59 ERROR  TaskList: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 573, in create_preseed
  File "\lib\wubi\backends\common\utils.py", line 89, in md5_password
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
05-30 01:59 DEBUG  TaskList: # Cancelling tasklist
05-30 01:59 ERROR  root: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 573, in create_preseed
  File "\lib\wubi\backends\common\utils.py", line 89, in md5_password
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
05-30 01:59 DEBUG  TaskList: # Finished tasklist
05-30 02:03 INFO   root: === wubi 11.04 rev211 ===
05-30 02:03 DEBUG  root: Logfile is c:\docume~1\karim\locals~1\temp\wubi-11.04-rev211.log
05-30 02:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
05-30 02:03 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\data
05-30 02:03 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\bin\7z.exe
05-30 02:03 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Menu DÃ©marrer\Programmes\DÃ©marrage
05-30 02:03 DEBUG  CommonBackend: Fetching basic info...
05-30 02:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-30 02:03 DEBUG  CommonBackend: platform=win32
05-30 02:03 DEBUG  CommonBackend: osname=nt
05-30 02:03 DEBUG  CommonBackend: language=fr_FR
05-30 02:03 DEBUG  CommonBackend: encoding=cp1252
05-30 02:03 DEBUG  WindowsBackend: arch=i386
05-30 02:03 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\data\isolist.ini
05-30 02:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-30 02:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-30 02:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-30 02:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-30 02:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-30 02:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-30 02:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-30 02:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-30 02:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-30 02:03 DEBUG  WindowsBackend: Fetching host info...
05-30 02:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-30 02:03 DEBUG  WindowsBackend: windows version=xp
05-30 02:03 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-30 02:03 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-30 02:03 DEBUG  WindowsBackend: windows_build=2600
05-30 02:03 DEBUG  WindowsBackend: gmt=1
05-30 02:03 DEBUG  WindowsBackend: country=FR
05-30 02:03 DEBUG  WindowsBackend: timezone=Europe/Paris
05-30 02:03 DEBUG  WindowsBackend: windows_username=KARIM
05-30 02:03 DEBUG  WindowsBackend: user_full_name=KARIM
05-30 02:03 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARIM
05-30 02:03 DEBUG  WindowsBackend: windows_language_code=1036
05-30 02:03 DEBUG  WindowsBackend: windows_language=French
05-30 02:03 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
05-30 02:03 DEBUG  WindowsBackend: bootloader=xp
05-30 02:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 112329.914063 mb free ntfs)
05-30 02:03 DEBUG  WindowsBackend: drive=Drive(C: hd 112329.914063 mb free ntfs)
05-30 02:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
05-30 02:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-30 02:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-30 02:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-30 02:03 DEBUG  WindowsBackend: keyboard_id=67896332
05-30 02:03 DEBUG  WindowsBackend: keyboard_layout=fr
05-30 02:03 DEBUG  WindowsBackend: keyboard_variant=
05-30 02:03 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1252')
05-30 02:03 DEBUG  CommonBackend: locale=fr_FR.UTF-8
05-30 02:03 DEBUG  WindowsBackend: total_memory_mb=502.046875
05-30 02:03 DEBUG  CommonBackend: Searching ISOs on USB devices
05-30 02:03 DEBUG  CommonBackend: Searching for local CDs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Ubuntu Netbook CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Kubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Xubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp is a valid Mythbuntu CD
05-30 02:03 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\casper\filesystem.squashfs
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 02:03 DEBUG  Distro:     does not contain D:\casper\initrd.lz
05-30 02:03 INFO   root: Running the uninstaller...
05-30 02:03 INFO   CommonBackend: This is the uninstaller running
05-30 02:03 DEBUG  WindowsFrontend: __init__...
05-30 02:03 DEBUG  WindowsFrontend: on_init...
05-30 02:03 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\translations, languages=['fr_FR', 'fr']
05-30 02:03 INFO   root: Received settings
05-30 02:03 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\translations, languages=['fr_FR', 'fr']
05-30 02:03 DEBUG  TaskList: # Running tasklist...
05-30 02:03 DEBUG  TaskList: ## Running Sauvegarder l'ISO...
05-30 02:03 DEBUG  TaskList: ## Finished Sauvegarder l'ISO
05-30 02:03 DEBUG  TaskList: ## Running Supprimer l'entrÃ©e pour le programme d'amorÃ§age...
05-30 02:03 ERROR  WindowsBackend: Cannot find bcdedit
05-30 02:03 DEBUG  WindowsBackend: undo_bootini C:
05-30 02:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 112329.914063 mb free ntfs)
05-30 02:03 DEBUG  TaskList: ## Finished Supprimer l'entrÃ©e pour le programme d'amorÃ§age
05-30 02:03 DEBUG  TaskList: ## Running Supprimer le rÃ©pertoire cible...
05-30 02:03 DEBUG  CommonBackend: Deleting C:\ubuntu
05-30 02:03 DEBUG  TaskList: ## Finished Supprimer le rÃ©pertoire cible
05-30 02:03 DEBUG  TaskList: ## Running Supprimer la clÃ© du registre...
05-30 02:03 DEBUG  TaskList: ## Finished Supprimer la clÃ© du registre
05-30 02:03 DEBUG  TaskList: # Finished tasklist
05-30 02:03 INFO   root: Almost finished uninstalling
05-30 02:03 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl5.tmp\translations, languages=['fr_FR', 'fr']
05-30 02:03 INFO   root: Finished uninstallation
05-30 02:03 DEBUG  root: application.quit
05-30 02:03 DEBUG  WindowsFrontend: frontend.quit
05-30 02:03 DEBUG  WindowsFrontend: frontend.on_quit
05-30 02:03 DEBUG  root: application.on_quit
05-30 02:03 INFO   root: sys.exit
05-31 01:19 INFO   root: === wubi 11.04 rev211 ===
05-31 01:19 DEBUG  root: Logfile is c:\docume~1\karim\locals~1\temp\wubi-11.04-rev211.log
05-31 01:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\KARIM\\Mes documents\\T\xe9l\xe9chargements\\wubi.exe"']
05-31 01:19 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\data
05-31 01:19 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\bin\7z.exe
05-31 01:19 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Menu DÃ©marrer\Programmes\DÃ©marrage
05-31 01:19 DEBUG  CommonBackend: Fetching basic info...
05-31 01:19 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\KARIM\Mes documents\Téléchargements\wubi.exe
05-31 01:19 DEBUG  CommonBackend: platform=win32
05-31 01:19 DEBUG  CommonBackend: osname=nt
05-31 01:19 DEBUG  CommonBackend: language=fr_FR
05-31 01:19 DEBUG  CommonBackend: encoding=cp1252
05-31 01:19 DEBUG  WindowsBackend: arch=i386
05-31 01:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\data\isolist.ini
05-31 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-31 01:19 DEBUG  WindowsBackend: Fetching host info...
05-31 01:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-31 01:19 DEBUG  WindowsBackend: windows version=xp
05-31 01:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-31 01:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-31 01:19 DEBUG  WindowsBackend: windows_build=2600
05-31 01:19 DEBUG  WindowsBackend: gmt=1
05-31 01:19 DEBUG  WindowsBackend: country=FR
05-31 01:19 DEBUG  WindowsBackend: timezone=Europe/Paris
05-31 01:19 DEBUG  WindowsBackend: windows_username=KARIM
05-31 01:19 DEBUG  WindowsBackend: user_full_name=KARIM
05-31 01:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARIM
05-31 01:19 DEBUG  WindowsBackend: windows_language_code=1036
05-31 01:19 DEBUG  WindowsBackend: windows_language=French
05-31 01:19 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
05-31 01:19 DEBUG  WindowsBackend: bootloader=xp
05-31 01:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 112648.648438 mb free ntfs)
05-31 01:19 DEBUG  WindowsBackend: drive=Drive(C: hd 112648.648438 mb free ntfs)
05-31 01:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-31 01:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-31 01:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-31 01:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-31 01:19 DEBUG  WindowsBackend: keyboard_id=67896332
05-31 01:19 DEBUG  WindowsBackend: keyboard_layout=fr
05-31 01:19 DEBUG  WindowsBackend: keyboard_variant=
05-31 01:19 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1252')
05-31 01:19 DEBUG  CommonBackend: locale=fr_FR.UTF-8
05-31 01:19 DEBUG  WindowsBackend: total_memory_mb=502.046875
05-31 01:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-31 01:19 DEBUG  CommonBackend: Searching for local CDs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Ubuntu Netbook CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl1.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 INFO   root: Already installed, running the uninstaller...
05-31 01:19 INFO   root: Running the uninstaller...
05-31 01:19 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
05-31 01:19 DEBUG  root: application.quit
05-31 01:19 DEBUG  root: application.on_quit
05-31 01:19 INFO   root: sys.exit
05-31 01:19 INFO   root: Quitting application
05-31 01:19 INFO   root: === wubi 11.04 rev211 ===
05-31 01:19 DEBUG  root: Logfile is c:\docume~1\karim\locals~1\temp\wubi-11.04-rev211.log
05-31 01:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\KARIM\\Mes documents\\T\xe9l\xe9chargements\\wubi.exe"']
05-31 01:19 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data
05-31 01:19 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
05-31 01:19 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Menu DÃ©marrer\Programmes\DÃ©marrage
05-31 01:19 DEBUG  CommonBackend: Fetching basic info...
05-31 01:19 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\KARIM\Mes documents\Téléchargements\wubi.exe
05-31 01:19 DEBUG  CommonBackend: platform=win32
05-31 01:19 DEBUG  CommonBackend: osname=nt
05-31 01:19 DEBUG  CommonBackend: language=fr_FR
05-31 01:19 DEBUG  CommonBackend: encoding=cp1252
05-31 01:19 DEBUG  WindowsBackend: arch=i386
05-31 01:19 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
05-31 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-31 01:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-31 01:19 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-31 01:19 DEBUG  WindowsBackend: Fetching host info...
05-31 01:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-31 01:19 DEBUG  WindowsBackend: windows version=xp
05-31 01:19 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
05-31 01:19 DEBUG  WindowsBackend: windows_sp=Service Pack 2
05-31 01:19 DEBUG  WindowsBackend: windows_build=2600
05-31 01:19 DEBUG  WindowsBackend: gmt=1
05-31 01:19 DEBUG  WindowsBackend: country=FR
05-31 01:19 DEBUG  WindowsBackend: timezone=Europe/Paris
05-31 01:19 DEBUG  WindowsBackend: windows_username=KARIM
05-31 01:19 DEBUG  WindowsBackend: user_full_name=KARIM
05-31 01:19 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\KARIM
05-31 01:19 DEBUG  WindowsBackend: windows_language_code=1036
05-31 01:19 DEBUG  WindowsBackend: windows_language=French
05-31 01:19 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) M CPU        430  @ 1.73GHz
05-31 01:19 DEBUG  WindowsBackend: bootloader=xp
05-31 01:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 112659.648438 mb free ntfs)
05-31 01:19 DEBUG  WindowsBackend: drive=Drive(C: hd 112659.648438 mb free ntfs)
05-31 01:19 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-31 01:19 DEBUG  WindowsBackend: uninstaller_path=None
05-31 01:19 DEBUG  WindowsBackend: previous_target_dir=None
05-31 01:19 DEBUG  WindowsBackend: previous_distro_name=None
05-31 01:19 DEBUG  WindowsBackend: keyboard_id=67896332
05-31 01:19 DEBUG  WindowsBackend: keyboard_layout=fr
05-31 01:19 DEBUG  WindowsBackend: keyboard_variant=
05-31 01:19 DEBUG  CommonBackend: python locale=('fr_FR', 'cp1252')
05-31 01:19 DEBUG  CommonBackend: locale=fr_FR.UTF-8
05-31 01:19 DEBUG  WindowsBackend: total_memory_mb=502.046875
05-31 01:19 DEBUG  CommonBackend: Searching ISOs on USB devices
05-31 01:19 DEBUG  CommonBackend: Searching for local CDs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:19 INFO   root: Running the installer...
05-31 01:19 DEBUG  WindowsFrontend: __init__...
05-31 01:19 DEBUG  WindowsFrontend: on_init...
05-31 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['fr_FR', 'fr']
05-31 01:19 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['fr_FR', 'fr']
05-31 01:20 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=karim
05-31 01:20 INFO   root: Received settings
05-31 01:20 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\translations, languages=['en_US', 'en']
05-31 01:20 DEBUG  TaskList: # Running tasklist...
05-31 01:20 DEBUG  TaskList: ## Running select_target_dir...
05-31 01:20 INFO   WindowsBackend: Installing into C:\ubuntu
05-31 01:20 DEBUG  TaskList: ## Finished select_target_dir
05-31 01:20 DEBUG  TaskList: ## Running create_dir_structure...
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-31 01:20 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-31 01:20 DEBUG  TaskList: ## Finished create_dir_structure
05-31 01:20 DEBUG  TaskList: ## Running uncompress_target_dir...
05-31 01:20 DEBUG  TaskList: ## Finished uncompress_target_dir
05-31 01:20 DEBUG  TaskList: ## Running create_uninstaller...
05-31 01:20 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\KARIM\Mes documents\Téléchargements\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-31 01:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-31 01:20 DEBUG  TaskList: ## Finished create_uninstaller
05-31 01:20 DEBUG  TaskList: ## Running copy_installation_files...
05-31 01:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-31 01:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\winboot -> C:\ubuntu\winboot
05-31 01:20 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-31 01:20 DEBUG  TaskList: ## Finished copy_installation_files
05-31 01:20 DEBUG  TaskList: ## Running get_iso...
05-31 01:20 DEBUG  CommonBackend: Searching for local CD
05-31 01:20 DEBUG  Distro:   checking whether C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
05-31 01:20 DEBUG  Distro:     does not contain C:\DOCUME~1\KARIM\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
05-31 01:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:20 DEBUG  CommonBackend: Searching for local ISO
05-31 01:20 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-31 01:20 DEBUG  TaskList: New task get_metalink
05-31 01:20 DEBUG  TaskList: ### Running get_metalink...
05-31 01:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink > C:\ubuntu\install
05-31 01:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-i386.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.metalink, basename=ubuntu-11.04-desktop-i386.metalink, length=28158, text=None
05-31 01:20 DEBUG  downloader: download finished (read 28158 bytes)
05-31 01:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-31 01:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-31 01:20 DEBUG  downloader: download finished (read 874 bytes)
05-31 01:20 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-31 01:20 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-31 01:20 DEBUG  downloader: download finished (read 198 bytes)
05-31 01:20 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-31 01:20 INFO   saplog: Checking block bindings..
05-31 01:20 INFO   saplog: Key verified successfully.
05-31 01:20 DEBUG  CommonBackend: metalink md5sums:
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

05-31 01:20 DEBUG  TaskList: ### Finished get_metalink
05-31 01:20 DEBUG  TaskList: New task download
05-31 01:20 DEBUG  TaskList: ### Running download...
05-31 01:20 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-i386.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:13 DEBUG  TaskList: ### Finished download
05-31 02:13 DEBUG  TaskList: New task check_iso
05-31 02:13 DEBUG  TaskList: ### Running check_iso...
05-31 02:13 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:13 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:13 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:13 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release i386 (20110427.1)
05-31 02:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'i386'}
05-31 02:13 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:13 DEBUG  TaskList: New task get_file_md5
05-31 02:13 DEBUG  TaskList: #### Running get_file_md5...
05-31 02:15 DEBUG  TaskList: #### Finished get_file_md5
05-31 02:15 DEBUG  TaskList: ### Finished check_iso
05-31 02:15 DEBUG  TaskList: ## Finished get_iso
05-31 02:15 DEBUG  TaskList: ## Running extract_kernel...
05-31 02:15 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:15 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:15 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:15 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-i386.iso
05-31 02:15 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-31 02:15 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-31 02:15 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = db0104e80bc7e667344a14af3515de25 == db0104e80bc7e667344a14af3515de25
05-31 02:15 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-31 02:15 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4b776cdafb272064bb70e09ba212e4aa == 4b776cdafb272064bb70e09ba212e4aa
05-31 02:15 DEBUG  TaskList: ## Finished extract_kernel
05-31 02:15 DEBUG  TaskList: ## Running choose_disk_sizes...
05-31 02:15 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-31 02:15 DEBUG  TaskList: ## Finished choose_disk_sizes
05-31 02:15 DEBUG  TaskList: ## Running create_preseed...
05-31 02:15 ERROR  TaskList: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 573, in create_preseed
  File "\lib\wubi\backends\common\utils.py", line 89, in md5_password
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
05-31 02:15 DEBUG  TaskList: # Cancelling tasklist
05-31 02:15 ERROR  root: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 573, in create_preseed
  File "\lib\wubi\backends\common\utils.py", line 89, in md5_password
UnicodeEncodeError: 'ascii' codec can't encode character u'\xe9' in position 1: ordinal not in range(128)
05-31 02:15 DEBUG  TaskList: # Finished tasklist


```

---

### Post by bcbc on 2011-05-31
It looks like it's failing while encrypting your password. Is there an accent aigu in there? Try removing that and then change it once you have Ubuntu running.

If you can confirm the problem is the é then maybe you should create a new wubi bug for this - or I will for you.

---

### Post by Lord_karim on 2011-06-02
so plz help and try to do for me

---

### Post by bcbc on 2011-06-02
> **Lord_karim said:**
> so plz help and try to do for me
Can you confirm that your password contained the **é** ?
If so, run wubi again, but enter a password without that or other special characters. See if you still get an error. If it works ok, then let it install Ubuntu, login with that same password, and then change it in Ubuntu.

If you can confirm that it is in fact the special character that is causing this, then I'll create a bug report for it. Because it should either be supported or handled more gracefully. But I need that confirmation (or I can test it myself, but I will have to find time to do this - and it won't be for a while).

Thanks

---

### Post by bcbc on 2011-06-03
I've created a bug report for this: [https://bugs.launchpad.net/wubi/+bug/792638](https://bugs.launchpad.net/wubi/+bug/792638)

---

### Post by Lord_karim on 2011-06-04
thank you so much for your support ,I am here to confirm that my Ubuntu works perfect ,but i did use Ubuntu with usb stick.
I am now using ubuntu 11.04.it works perfectly,

---

### Post by bcbc on 2011-06-04
> **Lord_karim said:**
> thank you so much for your support ,I am here to confirm that my Ubuntu works perfect ,but i did use Ubuntu with usb stick.
I am now using ubuntu 11.04.it works perfectly,

Great! Enjoy :)

---

