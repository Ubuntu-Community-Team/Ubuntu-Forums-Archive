---
title: "getting &lt;urlopen error (10061, 'Connection refused')&gt;"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by tozz88 on 2010-08-29
I'm trying to install Ubuntu using the wubi installer but am getting the following error in my log file:

08-28 21:53 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>

all over the place. I've disabled my anit-virus but that doesn't seem to help. Is a server down or something? Do I have to make/install from CD?

Here is the whole log file:

08-28 23:14 INFO   root: === wubi 10.04.1 rev190 ===
08-28 23:14 DEBUG  root: Logfile is c:\docume~1\bob\locals~1\temp\wubi-10.04.1-rev190.log
08-28 23:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Temp\\wubi.exe"']
08-28 23:14 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\data
08-28 23:14 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\bin\7z.exe
08-28 23:14 DEBUG  CommonBackend: Fetching basic info...
08-28 23:14 DEBUG  CommonBackend: original_exe=C:\Temp\wubi.exe
08-28 23:14 DEBUG  CommonBackend: platform=win32
08-28 23:14 DEBUG  CommonBackend: osname=nt
08-28 23:14 DEBUG  CommonBackend: language=en_US
08-28 23:14 DEBUG  CommonBackend: encoding=cp1252
08-28 23:14 DEBUG  WindowsBackend: arch=amd64
08-28 23:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\data\isolist.ini
08-28 23:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-28 23:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-28 23:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-28 23:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-28 23:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-28 23:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-28 23:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-28 23:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-28 23:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
08-28 23:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-28 23:14 DEBUG  WindowsBackend: Fetching host info...
08-28 23:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-28 23:14 DEBUG  WindowsBackend: windows version=xp
08-28 23:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-28 23:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-28 23:14 DEBUG  WindowsBackend: windows_build=2600
08-28 23:14 DEBUG  WindowsBackend: gmt=-8
08-28 23:14 DEBUG  WindowsBackend: country=US
08-28 23:14 DEBUG  WindowsBackend: timezone=America/Los_Angeles
08-28 23:14 DEBUG  WindowsBackend: windows_username=Bob
08-28 23:14 DEBUG  WindowsBackend: user_full_name=Bob
08-28 23:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Bob
08-28 23:14 DEBUG  WindowsBackend: windows_language_code=1033
08-28 23:14 DEBUG  WindowsBackend: windows_language=English
08-28 23:14 DEBUG  WindowsBackend: processor_name=Mobile AMD Athlon(tm) 64 Processor 3000+
08-28 23:14 DEBUG  WindowsBackend: bootloader=xp
08-28 23:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 21872.515625 mb free ntfs)
08-28 23:14 DEBUG  WindowsBackend: drive=Drive(C: hd 21872.515625 mb free ntfs)
08-28 23:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-28 23:14 DEBUG  WindowsBackend: uninstaller_path=None
08-28 23:14 DEBUG  WindowsBackend: previous_target_dir=None
08-28 23:14 DEBUG  WindowsBackend: previous_distro_name=None
08-28 23:14 DEBUG  WindowsBackend: keyboard_id=67699721
08-28 23:14 DEBUG  WindowsBackend: keyboard_layout=us
08-28 23:14 DEBUG  WindowsBackend: keyboard_variant=
08-28 23:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-28 23:14 DEBUG  CommonBackend: locale=en_US.UTF-8
08-28 23:14 DEBUG  WindowsBackend: total_memory_mb=1278.484375
08-28 23:14 DEBUG  CommonBackend: Searching ISOs on USB devices
08-28 23:14 DEBUG  CommonBackend: Searching for local CDs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu Netbook CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Kubuntu Netbook CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Xubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Xubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Mythbuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Mythbuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 INFO   root: Running the installer...
08-28 23:14 DEBUG  WindowsFrontend: __init__...
08-28 23:14 DEBUG  WindowsFrontend: on_init...
08-28 23:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\translations, languages=['en_US', 'en']
08-28 23:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\translations, languages=['en_US', 'en']
08-28 23:14 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=12000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tozz
08-28 23:14 INFO   root: Received settings
08-28 23:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\translations, languages=['en_US', 'en']
08-28 23:14 DEBUG  TaskList: # Running tasklist...
08-28 23:14 DEBUG  TaskList: ## Running select_target_dir...
08-28 23:14 INFO   WindowsBackend: Installing into C:\ubuntu
08-28 23:14 DEBUG  TaskList: ## Finished select_target_dir
08-28 23:14 DEBUG  TaskList: ## Running create_dir_structure...
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
08-28 23:14 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
08-28 23:14 DEBUG  TaskList: ## Finished create_dir_structure
08-28 23:14 DEBUG  TaskList: ## Running uncompress_target_dir...
08-28 23:14 DEBUG  TaskList: ## Finished uncompress_target_dir
08-28 23:14 DEBUG  TaskList: ## Running create_uninstaller...
08-28 23:14 DEBUG  WindowsBackend: Copying uninstaller C:\Temp\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
08-28 23:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
08-28 23:14 DEBUG  TaskList: ## Finished create_uninstaller
08-28 23:14 DEBUG  TaskList: ## Running copy_installation_files...
08-28 23:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
08-28 23:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\winboot -> C:\ubuntu\winboot
08-28 23:14 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
08-28 23:14 DEBUG  TaskList: ## Finished copy_installation_files
08-28 23:14 DEBUG  TaskList: ## Running get_iso...
08-28 23:14 DEBUG  CommonBackend: Searching for local CD
08-28 23:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Bob\LOCALS~1\Temp\pyl42.tmp\casper\filesystem.squashfs
08-28 23:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-28 23:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-28 23:14 DEBUG  CommonBackend: Searching for local ISO
08-28 23:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
08-28 23:14 DEBUG  TaskList: New task get_metalink
08-28 23:14 DEBUG  TaskList: ### Running get_metalink...
08-28 23:14 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > C:\ubuntu\install
08-28 23:14 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
08-28 23:14 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > C:\ubuntu\install
08-28 23:14 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 4] IOError: <urlopen error (10061, 'Connection refused')>
08-28 23:14 DEBUG  TaskList: ### Finished get_metalink
08-28 23:14 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-28 23:14 DEBUG  TaskList: # Cancelling tasklist
08-28 23:14 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
08-28 23:14 DEBUG  TaskList: # Finished tasklist

---

