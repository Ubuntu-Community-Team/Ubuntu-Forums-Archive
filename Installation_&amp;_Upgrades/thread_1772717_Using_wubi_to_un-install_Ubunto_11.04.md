---
title: "Using wubi to un-install Ubunto 11.04"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by Coaxsist on 2011-06-01
Hey all, looking forward to learning about Ubuntu.

I installed 11.04, uninstalled it, then installed it again, all with wubi. I'd like to install it again, but I get an error from wubi: [IMG]http://img204.imageshack.us/img204/7637/exampleip.jpg[/IMG]

I've tried to follow this procedure:
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
but I can't delete the partition I believe Ubuntu was using in either my Administrator account, or my regular account.

Can anyone offer any help?

Thanks,
- K

EDIT:

I've done some Google searches and realized I haven't provided enough information.
I'm running a Dell Studio 15 with Win 7 Home Premium 64x. The log file wubi refers to in the above screenshot is below:
```

05-19 01:30 INFO   root: === wubi 11.04 rev211 ===
05-19 01:30 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-19 01:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
05-19 01:30 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\data
05-19 01:30 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\bin\7z.exe
05-19 01:30 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-19 01:30 DEBUG  CommonBackend: Fetching basic info...
05-19 01:30 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-19 01:30 DEBUG  CommonBackend: platform=win32
05-19 01:30 DEBUG  CommonBackend: osname=nt
05-19 01:30 DEBUG  CommonBackend: language=en_US
05-19 01:30 DEBUG  CommonBackend: encoding=cp1252
05-19 01:30 DEBUG  WindowsBackend: arch=amd64
05-19 01:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\data\isolist.ini
05-19 01:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-19 01:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-19 01:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-19 01:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-19 01:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-19 01:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-19 01:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-19 01:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-19 01:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-19 01:30 DEBUG  WindowsBackend: Fetching host info...
05-19 01:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-19 01:30 DEBUG  WindowsBackend: windows version=vista
05-19 01:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-19 01:30 DEBUG  WindowsBackend: windows_sp=None
05-19 01:30 DEBUG  WindowsBackend: windows_build=7601
05-19 01:30 DEBUG  WindowsBackend: gmt=-5
05-19 01:30 DEBUG  WindowsBackend: country=US
05-19 01:30 DEBUG  WindowsBackend: timezone=America/New_York
05-19 01:30 DEBUG  WindowsBackend: windows_username=Kyle
05-19 01:30 DEBUG  WindowsBackend: user_full_name=Kyle
05-19 01:30 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-19 01:30 DEBUG  WindowsBackend: windows_language_code=1033
05-19 01:30 DEBUG  WindowsBackend: windows_language=English
05-19 01:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-19 01:30 DEBUG  WindowsBackend: bootloader=vista
05-19 01:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 374851.808594 mb free ntfs)
05-19 01:30 DEBUG  WindowsBackend: drive=Drive(C: hd 374851.808594 mb free ntfs)
05-19 01:30 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-19 01:30 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-19 01:30 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-19 01:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-19 01:30 DEBUG  WindowsBackend: keyboard_id=67699721
05-19 01:30 DEBUG  WindowsBackend: keyboard_layout=us
05-19 01:30 DEBUG  WindowsBackend: keyboard_variant=
05-19 01:30 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-19 01:30 DEBUG  CommonBackend: locale=en_US.UTF-8
05-19 01:30 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-19 01:30 DEBUG  CommonBackend: Searching ISOs on USB devices
05-19 01:30 DEBUG  CommonBackend: Searching for local CDs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Ubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Ubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Ubuntu Netbook CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Kubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Kubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Xubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Xubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Mythbuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp is a valid Mythbuntu CD
05-19 01:30 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylB2F9.tmp\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-19 01:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:30 INFO   root: Already installed, running the uninstaller...
05-19 01:30 INFO   root: Running the uninstaller...
05-19 01:30 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
05-19 01:30 DEBUG  root: application.quit
05-19 01:30 DEBUG  root: application.on_quit
05-19 01:30 INFO   root: sys.exit
05-19 01:30 INFO   root: Quitting application
05-19 01:33 INFO   root: === wubi 11.04 rev211 ===
05-19 01:33 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-19 01:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
05-19 01:33 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\data
05-19 01:33 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\bin\7z.exe
05-19 01:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-19 01:33 DEBUG  CommonBackend: Fetching basic info...
05-19 01:33 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-19 01:33 DEBUG  CommonBackend: platform=win32
05-19 01:33 DEBUG  CommonBackend: osname=nt
05-19 01:33 DEBUG  CommonBackend: language=en_US
05-19 01:33 DEBUG  CommonBackend: encoding=cp1252
05-19 01:33 DEBUG  WindowsBackend: arch=amd64
05-19 01:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\data\isolist.ini
05-19 01:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-19 01:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-19 01:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-19 01:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-19 01:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-19 01:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-19 01:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-19 01:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-19 01:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-19 01:33 DEBUG  WindowsBackend: Fetching host info...
05-19 01:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-19 01:33 DEBUG  WindowsBackend: windows version=vista
05-19 01:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-19 01:33 DEBUG  WindowsBackend: windows_sp=None
05-19 01:33 DEBUG  WindowsBackend: windows_build=7601
05-19 01:33 DEBUG  WindowsBackend: gmt=-5
05-19 01:33 DEBUG  WindowsBackend: country=US
05-19 01:33 DEBUG  WindowsBackend: timezone=America/New_York
05-19 01:33 DEBUG  WindowsBackend: windows_username=Kyle
05-19 01:33 DEBUG  WindowsBackend: user_full_name=Kyle
05-19 01:33 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-19 01:33 DEBUG  WindowsBackend: windows_language_code=1033
05-19 01:33 DEBUG  WindowsBackend: windows_language=English
05-19 01:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-19 01:33 DEBUG  WindowsBackend: bootloader=vista
05-19 01:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392544.777344 mb free ntfs)
05-19 01:33 DEBUG  WindowsBackend: drive=Drive(C: hd 392544.777344 mb free ntfs)
05-19 01:33 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-19 01:33 DEBUG  WindowsBackend: uninstaller_path=None
05-19 01:33 DEBUG  WindowsBackend: previous_target_dir=None
05-19 01:33 DEBUG  WindowsBackend: previous_distro_name=None
05-19 01:33 DEBUG  WindowsBackend: keyboard_id=67699721
05-19 01:33 DEBUG  WindowsBackend: keyboard_layout=us
05-19 01:33 DEBUG  WindowsBackend: keyboard_variant=
05-19 01:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-19 01:33 DEBUG  CommonBackend: locale=en_US.UTF-8
05-19 01:33 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-19 01:33 DEBUG  CommonBackend: Searching ISOs on USB devices
05-19 01:33 DEBUG  CommonBackend: Searching for local CDs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Ubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Ubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Ubuntu Netbook CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Kubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Kubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Xubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Xubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Mythbuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Mythbuntu CD
05-19 01:33 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-19 01:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:33 INFO   root: Running the installer...
05-19 01:33 DEBUG  WindowsFrontend: __init__...
05-19 01:33 DEBUG  WindowsFrontend: on_init...
05-19 01:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\translations, languages=['en_US', 'en']
05-19 01:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\translations, languages=['en_US', 'en']
05-19 01:34 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kyle
05-19 01:34 INFO   root: Received settings
05-19 01:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\translations, languages=['en_US', 'en']
05-19 01:34 DEBUG  TaskList: # Running tasklist...
05-19 01:34 DEBUG  TaskList: ## Running select_target_dir...
05-19 01:34 INFO   WindowsBackend: Installing into C:\ubuntu
05-19 01:34 DEBUG  TaskList: ## Finished select_target_dir
05-19 01:34 DEBUG  TaskList: ## Running create_dir_structure...
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-19 01:34 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-19 01:34 DEBUG  TaskList: ## Finished create_dir_structure
05-19 01:34 DEBUG  TaskList: ## Running uncompress_target_dir...
05-19 01:34 DEBUG  TaskList: ## Finished uncompress_target_dir
05-19 01:34 DEBUG  TaskList: ## Running create_uninstaller...
05-19 01:34 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe -> C:\ubuntu\uninstall-wubi.exe
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-19 01:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-19 01:34 DEBUG  TaskList: ## Finished create_uninstaller
05-19 01:34 DEBUG  TaskList: ## Running copy_installation_files...
05-19 01:34 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-19 01:34 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\winboot -> C:\ubuntu\winboot
05-19 01:34 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-19 01:34 DEBUG  TaskList: ## Finished copy_installation_files
05-19 01:34 DEBUG  TaskList: ## Running get_iso...
05-19 01:34 DEBUG  CommonBackend: Searching for local CD
05-19 01:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp is a valid Ubuntu CD
05-19 01:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\casper\filesystem.squashfs
05-19 01:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 01:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 01:34 DEBUG  CommonBackend: Searching for local ISO
05-19 01:34 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-19 01:34 DEBUG  TaskList: New task get_metalink
05-19 01:34 DEBUG  TaskList: ### Running get_metalink...
05-19 01:34 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-19 01:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-19 01:34 DEBUG  downloader: download finished (read 28363 bytes)
05-19 01:34 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-19 01:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-19 01:34 DEBUG  downloader: download finished (read 874 bytes)
05-19 01:34 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-19 01:34 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-19 01:34 DEBUG  downloader: download finished (read 198 bytes)
05-19 01:34 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-19 01:34 INFO   saplog: Checking block bindings..
05-19 01:34 INFO   saplog: Key verified successfully.
05-19 01:34 DEBUG  CommonBackend: metalink md5sums:
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

05-19 01:34 DEBUG  TaskList: ### Finished get_metalink
05-19 01:34 DEBUG  TaskList: New task download
05-19 01:34 DEBUG  TaskList: ### Running download...
05-19 01:34 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  TaskList: ### Finished download
05-19 01:43 DEBUG  TaskList: New task check_iso
05-19 01:43 DEBUG  TaskList: ### Running check_iso...
05-19 01:43 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
05-19 01:43 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
05-19 01:43 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  TaskList: New task get_file_md5
05-19 01:43 DEBUG  TaskList: #### Running get_file_md5...
05-19 01:43 DEBUG  TaskList: #### Finished get_file_md5
05-19 01:43 DEBUG  TaskList: ### Finished check_iso
05-19 01:43 DEBUG  TaskList: ## Finished get_iso
05-19 01:43 DEBUG  TaskList: ## Running extract_kernel...
05-19 01:43 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 01:43 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-19 01:43 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-19 01:43 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
05-19 01:43 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-19 01:43 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
05-19 01:43 DEBUG  TaskList: ## Finished extract_kernel
05-19 01:43 DEBUG  TaskList: ## Running choose_disk_sizes...
05-19 01:43 DEBUG  WindowsBackend: total size=17000
  root=16744
  swap=256
  home=0
  usr=0
05-19 01:43 DEBUG  TaskList: ## Finished choose_disk_sizes
05-19 01:43 DEBUG  TaskList: ## Running create_preseed...
05-19 01:43 DEBUG  TaskList: ## Finished create_preseed
05-19 01:43 DEBUG  TaskList: ## Running modify_bootloader...
05-19 01:43 DEBUG  TaskList: New task modify_bcd
05-19 01:43 DEBUG  TaskList: ### Running modify_bcd...
05-19 01:43 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 392544.777344 mb free ntfs)
05-19 01:43 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {599f1815-6055-11e0-b332-b8ac6f70cae5}
05-19 01:43 DEBUG  TaskList: ### Finished modify_bcd
05-19 01:43 DEBUG  TaskList: ## Finished modify_bootloader
05-19 01:43 DEBUG  TaskList: ## Running modify_grub_configuration...
05-19 01:43 DEBUG  TaskList: ## Finished modify_grub_configuration
05-19 01:43 DEBUG  TaskList: ## Running create_virtual_disks...
05-19 01:43 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 16744MB
05-19 01:43 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-19 01:43 DEBUG  TaskList: ## Finished create_virtual_disks
05-19 01:43 DEBUG  TaskList: ## Running uncompress_files...
05-19 01:43 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-19 01:43 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-19 01:43 DEBUG  TaskList: ## Finished uncompress_files
05-19 01:43 DEBUG  TaskList: ## Running eject_cd...
05-19 01:43 DEBUG  TaskList: ## Finished eject_cd
05-19 01:43 DEBUG  TaskList: # Finished tasklist
05-19 01:43 INFO   root: Almost finished installing
05-19 01:43 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl9C6D.tmp\translations, languages=['en_US', 'en']
05-19 01:43 INFO   root: Finished installation
05-19 01:43 INFO   root: Rebooting
05-19 01:43 DEBUG  TaskList: # Running tasklist...
05-19 01:43 DEBUG  TaskList: ## Running reboot...
05-19 01:43 DEBUG  TaskList: ## Finished reboot
05-19 01:43 DEBUG  TaskList: # Finished tasklist
05-19 01:43 DEBUG  root: application.quit
05-19 01:43 DEBUG  WindowsFrontend: frontend.quit
05-19 01:43 DEBUG  WindowsFrontend: frontend.on_quit
05-19 01:43 DEBUG  root: application.on_quit
05-19 01:43 INFO   root: sys.exit
05-18 21:59 INFO   root: === wubi 11.04 rev211 ===
05-18 21:59 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-18 21:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
05-18 21:59 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\data
05-18 21:59 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\bin\7z.exe
05-18 21:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-18 21:59 DEBUG  CommonBackend: Fetching basic info...
05-18 21:59 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-18 21:59 DEBUG  CommonBackend: platform=win32
05-18 21:59 DEBUG  CommonBackend: osname=nt
05-18 21:59 DEBUG  CommonBackend: language=en_US
05-18 21:59 DEBUG  CommonBackend: encoding=cp1252
05-18 21:59 DEBUG  WindowsBackend: arch=amd64
05-18 21:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\data\isolist.ini
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 21:59 DEBUG  WindowsBackend: Fetching host info...
05-18 21:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 21:59 DEBUG  WindowsBackend: windows version=vista
05-18 21:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 21:59 DEBUG  WindowsBackend: windows_sp=None
05-18 21:59 DEBUG  WindowsBackend: windows_build=7601
05-18 21:59 DEBUG  WindowsBackend: gmt=-5
05-18 21:59 DEBUG  WindowsBackend: country=US
05-18 21:59 DEBUG  WindowsBackend: timezone=America/New_York
05-18 21:59 DEBUG  WindowsBackend: windows_username=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_full_name=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-18 21:59 DEBUG  WindowsBackend: windows_language_code=1033
05-18 21:59 DEBUG  WindowsBackend: windows_language=English
05-18 21:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-18 21:59 DEBUG  WindowsBackend: bootloader=vista
05-18 21:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 374828.273438 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(C: hd 374828.273438 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-18 21:59 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-18 21:59 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-18 21:59 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-18 21:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 21:59 DEBUG  WindowsBackend: keyboard_layout=us
05-18 21:59 DEBUG  WindowsBackend: keyboard_variant=
05-18 21:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 21:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 21:59 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-18 21:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 21:59 DEBUG  CommonBackend: Searching for local CDs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 INFO   root: Already installed, running the uninstaller...
05-18 21:59 INFO   root: Running the uninstaller...
05-18 21:59 INFO   CommonBackend: This is the uninstaller running
05-18 21:59 DEBUG  WindowsFrontend: __init__...
05-18 21:59 DEBUG  WindowsFrontend: on_init...
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-18 21:59 INFO   root: Received settings
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-18 21:59 DEBUG  TaskList: # Running tasklist...
05-18 21:59 DEBUG  TaskList: ## Running Backup ISO...
05-18 21:59 DEBUG  TaskList: ## Finished Backup ISO
05-18 21:59 DEBUG  TaskList: ## Running Remove bootloader entry...
05-18 21:59 DEBUG  WindowsBackend: Removing bcd entry {599f1815-6055-11e0-b332-b8ac6f70cae5}
05-18 21:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-18 21:59 DEBUG  WindowsBackend: undo_bootini C:
05-18 21:59 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 374828.273438 mb free ntfs)
05-18 21:59 DEBUG  TaskList: ## Finished Remove bootloader entry
05-18 21:59 DEBUG  TaskList: ## Running Remove target dir...
05-18 21:59 DEBUG  CommonBackend: Deleting C:\ubuntu
05-18 21:59 DEBUG  TaskList: ## Finished Remove target dir
05-18 21:59 DEBUG  TaskList: ## Running Remove registry key...
05-18 21:59 DEBUG  TaskList: ## Finished Remove registry key
05-18 21:59 DEBUG  TaskList: # Finished tasklist
05-18 21:59 INFO   root: Almost finished uninstalling
05-18 21:59 INFO   root: Finished uninstallation
05-18 21:59 DEBUG  CommonBackend: Fetching basic info...
05-18 21:59 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-18 21:59 DEBUG  CommonBackend: platform=win32
05-18 21:59 DEBUG  CommonBackend: osname=nt
05-18 21:59 DEBUG  WindowsBackend: arch=amd64
05-18 21:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\data\isolist.ini
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 21:59 DEBUG  WindowsBackend: Fetching host info...
05-18 21:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 21:59 DEBUG  WindowsBackend: windows version=vista
05-18 21:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 21:59 DEBUG  WindowsBackend: windows_sp=None
05-18 21:59 DEBUG  WindowsBackend: windows_build=7601
05-18 21:59 DEBUG  WindowsBackend: gmt=-5
05-18 21:59 DEBUG  WindowsBackend: country=US
05-18 21:59 DEBUG  WindowsBackend: timezone=America/New_York
05-18 21:59 DEBUG  WindowsBackend: windows_username=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_full_name=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-18 21:59 DEBUG  WindowsBackend: windows_language_code=1033
05-18 21:59 DEBUG  WindowsBackend: windows_language=English
05-18 21:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-18 21:59 DEBUG  WindowsBackend: bootloader=vista
05-18 21:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392545.886719 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(C: hd 392545.886719 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-18 21:59 DEBUG  WindowsBackend: uninstaller_path=None
05-18 21:59 DEBUG  WindowsBackend: previous_target_dir=None
05-18 21:59 DEBUG  WindowsBackend: previous_distro_name=None
05-18 21:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 21:59 DEBUG  WindowsBackend: keyboard_layout=us
05-18 21:59 DEBUG  WindowsBackend: keyboard_variant=
05-18 21:59 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-18 21:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 21:59 DEBUG  CommonBackend: Searching for local CDs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 INFO   root: Running the installer...
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-18 21:59 INFO   root: === wubi 11.04 rev211 ===
05-18 21:59 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-18 21:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
05-18 21:59 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\data
05-18 21:59 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\bin\7z.exe
05-18 21:59 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-18 21:59 DEBUG  CommonBackend: Fetching basic info...
05-18 21:59 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-18 21:59 DEBUG  CommonBackend: platform=win32
05-18 21:59 DEBUG  CommonBackend: osname=nt
05-18 21:59 DEBUG  CommonBackend: language=en_US
05-18 21:59 DEBUG  CommonBackend: encoding=cp1252
05-18 21:59 DEBUG  WindowsBackend: arch=amd64
05-18 21:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\data\isolist.ini
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-18 21:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-18 21:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-18 21:59 DEBUG  WindowsBackend: Fetching host info...
05-18 21:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-18 21:59 DEBUG  WindowsBackend: windows version=vista
05-18 21:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-18 21:59 DEBUG  WindowsBackend: windows_sp=None
05-18 21:59 DEBUG  WindowsBackend: windows_build=7601
05-18 21:59 DEBUG  WindowsBackend: gmt=-5
05-18 21:59 DEBUG  WindowsBackend: country=US
05-18 21:59 DEBUG  WindowsBackend: timezone=America/New_York
05-18 21:59 DEBUG  WindowsBackend: windows_username=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_full_name=Kyle
05-18 21:59 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-18 21:59 DEBUG  WindowsBackend: windows_language_code=1033
05-18 21:59 DEBUG  WindowsBackend: windows_language=English
05-18 21:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-18 21:59 DEBUG  WindowsBackend: bootloader=vista
05-18 21:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392539.453125 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(C: hd 392539.453125 mb free ntfs)
05-18 21:59 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-18 21:59 DEBUG  WindowsBackend: uninstaller_path=None
05-18 21:59 DEBUG  WindowsBackend: previous_target_dir=None
05-18 21:59 DEBUG  WindowsBackend: previous_distro_name=None
05-18 21:59 DEBUG  WindowsBackend: keyboard_id=67699721
05-18 21:59 DEBUG  WindowsBackend: keyboard_layout=us
05-18 21:59 DEBUG  WindowsBackend: keyboard_variant=
05-18 21:59 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-18 21:59 DEBUG  CommonBackend: locale=en_US.UTF-8
05-18 21:59 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-18 21:59 DEBUG  CommonBackend: Searching ISOs on USB devices
05-18 21:59 DEBUG  CommonBackend: Searching for local CDs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-18 21:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-18 21:59 INFO   root: Running the installer...
05-18 21:59 DEBUG  WindowsFrontend: __init__...
05-18 21:59 DEBUG  WindowsFrontend: on_init...
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\translations, languages=['en_US', 'en']
05-18 21:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylD1EE.tmp\translations, languages=['en_US', 'en']
05-18 21:59 INFO   WindowsFrontend: Operation cancelled
05-18 21:59 DEBUG  WindowsFrontend: frontend.quit
05-18 21:59 DEBUG  WindowsFrontend: frontend.on_quit
05-18 21:59 DEBUG  root: application.on_quit
05-18 21:59 INFO   root: sys.exit
05-19 06:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=kyle
05-19 06:06 INFO   root: Received settings
05-19 06:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-19 06:06 DEBUG  TaskList: # Running tasklist...
05-19 06:06 DEBUG  TaskList: ## Running select_target_dir...
05-19 06:06 INFO   WindowsBackend: Installing into C:\ubuntu
05-19 06:06 DEBUG  TaskList: ## Finished select_target_dir
05-19 06:06 DEBUG  TaskList: ## Running create_dir_structure...
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-19 06:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-19 06:06 DEBUG  TaskList: ## Finished create_dir_structure
05-19 06:06 DEBUG  TaskList: ## Running uncompress_target_dir...
05-19 06:06 DEBUG  TaskList: ## Finished uncompress_target_dir
05-19 06:06 DEBUG  TaskList: ## Running create_uninstaller...
05-19 06:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe -> C:\ubuntu\uninstall-wubi.exe
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
05-19 06:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
05-19 06:06 DEBUG  TaskList: ## Finished create_uninstaller
05-19 06:06 DEBUG  TaskList: ## Running copy_installation_files...
05-19 06:06 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-19 06:06 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\winboot -> C:\ubuntu\winboot
05-19 06:06 DEBUG  WindowsBackend: Copying C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-19 06:06 DEBUG  TaskList: ## Finished copy_installation_files
05-19 06:06 DEBUG  TaskList: ## Running get_iso...
05-19 06:06 DEBUG  CommonBackend: Searching for local CD
05-19 06:06 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp is a valid Ubuntu CD
05-19 06:06 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\casper\filesystem.squashfs
05-19 06:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-19 06:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-19 06:06 DEBUG  CommonBackend: Searching for local ISO
05-19 06:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-19 06:06 DEBUG  TaskList: New task get_metalink
05-19 06:06 DEBUG  TaskList: ### Running get_metalink...
05-19 06:06 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink > C:\ubuntu\install
05-19 06:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-19 06:06 DEBUG  downloader: download finished (read 28363 bytes)
05-19 06:06 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink > C:\ubuntu\install
05-19 06:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-19 06:06 DEBUG  downloader: download finished (read 874 bytes)
05-19 06:06 DEBUG  downloader: downloading http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg > C:\ubuntu\install
05-19 06:06 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-19 06:06 DEBUG  downloader: download finished (read 198 bytes)
05-19 06:06 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-19 06:06 INFO   saplog: Checking block bindings..
05-19 06:06 INFO   saplog: Key verified successfully.
05-19 06:06 DEBUG  CommonBackend: metalink md5sums:
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

05-19 06:06 DEBUG  TaskList: ### Finished get_metalink
05-19 06:06 DEBUG  TaskList: New task download
05-19 06:06 DEBUG  TaskList: ### Running download...
05-19 06:06 DEBUG  btdownloader: downloading http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:13 DEBUG  TaskList: ### Finished download
05-19 10:13 DEBUG  TaskList: New task check_iso
05-19 10:13 DEBUG  TaskList: ### Running check_iso...
05-19 10:13 DEBUG  CommonBackend: Checking C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:13 DEBUG  Distro:   checking Ubuntu ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:13 DEBUG  WindowsBackend:   extracting .disk\info from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:13 DEBUG  Distro:   parsing info from str=Ubuntu 11.04 "Natty Narwhal" - Release amd64 (20110427.1)
05-19 10:13 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427.1', 'codename': 'Natty Narwhal', 'arch': 'amd64'}
05-19 10:13 INFO   Distro: Found a valid iso for Ubuntu: C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:13 DEBUG  TaskList: New task get_file_md5
05-19 10:13 DEBUG  TaskList: #### Running get_file_md5...
05-19 10:14 DEBUG  TaskList: #### Finished get_file_md5
05-19 10:14 DEBUG  TaskList: ### Finished check_iso
05-19 10:14 DEBUG  TaskList: ## Finished get_iso
05-19 10:14 DEBUG  TaskList: ## Running extract_kernel...
05-19 10:14 DEBUG  CommonBackend: Extracting files from ISO C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:14 DEBUG  WindowsBackend:   extracting md5sum.txt from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:14 DEBUG  WindowsBackend:   extracting casper\vmlinuz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:14 DEBUG  WindowsBackend:   extracting casper\initrd.lz from C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-19 10:14 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
05-19 10:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\vmlinuz
05-19 10:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\vmlinuz md5 = 45a7bee6779b8cd75634a70fd7a566dd == 45a7bee6779b8cd75634a70fd7a566dd
05-19 10:14 DEBUG  CommonBackend:   checking C:\ubuntu\install\boot\initrd.lz
05-19 10:14 DEBUG  CommonBackend:   C:\ubuntu\install\boot\initrd.lz md5 = 4aa66b9da42e1a3f667ab0c8009cc801 == 4aa66b9da42e1a3f667ab0c8009cc801
05-19 10:14 DEBUG  TaskList: ## Finished extract_kernel
05-19 10:14 DEBUG  TaskList: ## Running choose_disk_sizes...
05-19 10:14 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
05-19 10:14 DEBUG  TaskList: ## Finished choose_disk_sizes
05-19 10:14 DEBUG  TaskList: ## Running create_preseed...
05-19 10:14 DEBUG  TaskList: ## Finished create_preseed
05-19 10:14 DEBUG  TaskList: ## Running modify_bootloader...
05-19 10:14 DEBUG  TaskList: New task modify_bcd
05-19 10:14 DEBUG  TaskList: ### Running modify_bcd...
05-19 10:14 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 392545.886719 mb free ntfs)
05-19 10:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-19 10:14 DEBUG  TaskList: ### Finished modify_bcd
05-19 10:14 DEBUG  TaskList: ## Finished modify_bootloader
05-19 10:14 DEBUG  TaskList: ## Running modify_grub_configuration...
05-19 10:14 DEBUG  TaskList: ## Finished modify_grub_configuration
05-19 10:14 DEBUG  TaskList: ## Running create_virtual_disks...
05-19 10:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\root.disk of 29744MB
05-19 10:14 DEBUG  Virtualdisk:  Creating virtual disk C:\ubuntu\disks\swap.disk of 256MB
05-19 10:14 DEBUG  TaskList: ## Finished create_virtual_disks
05-19 10:14 DEBUG  TaskList: ## Running uncompress_files...
05-19 10:14 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot /U /A /F
05-19 10:14 DEBUG  WindowsBackend: compact C:\ubuntu\install\boot\*.* /U /A /F
05-19 10:14 DEBUG  TaskList: ## Finished uncompress_files
05-19 10:14 DEBUG  TaskList: ## Running eject_cd...
05-19 10:14 DEBUG  TaskList: ## Finished eject_cd
05-19 10:14 DEBUG  TaskList: # Finished tasklist
05-19 10:14 INFO   root: Almost finished installing
05-19 10:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl96F1.tmp\translations, languages=['en_US', 'en']
05-19 10:17 INFO   root: Finished installation
05-19 10:17 INFO   root: Rebooting
05-19 10:17 DEBUG  TaskList: # Running tasklist...
05-19 10:17 DEBUG  TaskList: ## Running reboot...
05-19 10:17 DEBUG  TaskList: ## Finished reboot
05-19 10:17 DEBUG  TaskList: # Finished tasklist
05-19 10:17 DEBUG  root: application.quit
05-19 10:17 DEBUG  WindowsFrontend: frontend.quit
05-19 10:17 DEBUG  WindowsFrontend: frontend.on_quit
05-19 10:17 DEBUG  root: application.on_quit
05-19 10:17 INFO   root: sys.exit
05-21 00:56 INFO   root: === wubi 11.04 rev211 ===
05-21 00:56 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-21 00:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
05-21 00:56 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\data
05-21 00:56 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\bin\7z.exe
05-21 00:56 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-21 00:56 DEBUG  CommonBackend: Fetching basic info...
05-21 00:56 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-21 00:56 DEBUG  CommonBackend: platform=win32
05-21 00:56 DEBUG  CommonBackend: osname=nt
05-21 00:56 DEBUG  CommonBackend: language=en_US
05-21 00:56 DEBUG  CommonBackend: encoding=cp1252
05-21 00:56 DEBUG  WindowsBackend: arch=amd64
05-21 00:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\data\isolist.ini
05-21 00:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-21 00:56 DEBUG  WindowsBackend: Fetching host info...
05-21 00:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-21 00:56 DEBUG  WindowsBackend: windows version=vista
05-21 00:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-21 00:56 DEBUG  WindowsBackend: windows_sp=None
05-21 00:56 DEBUG  WindowsBackend: windows_build=7601
05-21 00:56 DEBUG  WindowsBackend: gmt=-5
05-21 00:56 DEBUG  WindowsBackend: country=US
05-21 00:56 DEBUG  WindowsBackend: timezone=America/New_York
05-21 00:56 DEBUG  WindowsBackend: windows_username=Kyle
05-21 00:56 DEBUG  WindowsBackend: user_full_name=Kyle
05-21 00:56 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-21 00:56 DEBUG  WindowsBackend: windows_language_code=1033
05-21 00:56 DEBUG  WindowsBackend: windows_language=English
05-21 00:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-21 00:56 DEBUG  WindowsBackend: bootloader=vista
05-21 00:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 363344.648438 mb free ntfs)
05-21 00:56 DEBUG  WindowsBackend: drive=Drive(C: hd 363344.648438 mb free ntfs)
05-21 00:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-21 00:56 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-21 00:56 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-21 00:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-21 00:56 DEBUG  WindowsBackend: keyboard_id=67699721
05-21 00:56 DEBUG  WindowsBackend: keyboard_layout=us
05-21 00:56 DEBUG  WindowsBackend: keyboard_variant=
05-21 00:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-21 00:56 DEBUG  CommonBackend: locale=en_US.UTF-8
05-21 00:56 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-21 00:56 DEBUG  CommonBackend: Searching ISOs on USB devices
05-21 00:56 DEBUG  CommonBackend: Searching for local CDs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu Netbook CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 INFO   root: Already installed, running the uninstaller...
05-21 00:56 INFO   root: Running the uninstaller...
05-21 00:56 INFO   CommonBackend: This is the uninstaller running
05-21 00:56 DEBUG  WindowsFrontend: __init__...
05-21 00:56 DEBUG  WindowsFrontend: on_init...
05-21 00:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\translations, languages=['en_US', 'en']
05-21 00:56 INFO   root: Received settings
05-21 00:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\translations, languages=['en_US', 'en']
05-21 00:56 DEBUG  TaskList: # Running tasklist...
05-21 00:56 DEBUG  TaskList: ## Running Backup ISO...
05-21 00:56 DEBUG  TaskList: ## Finished Backup ISO
05-21 00:56 DEBUG  TaskList: ## Running Remove bootloader entry...
05-21 00:56 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-21 00:56 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-21 00:56 DEBUG  WindowsBackend: undo_bootini C:
05-21 00:56 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 363344.648438 mb free ntfs)
05-21 00:56 DEBUG  TaskList: ## Finished Remove bootloader entry
05-21 00:56 DEBUG  TaskList: ## Running Remove target dir...
05-21 00:56 DEBUG  CommonBackend: Deleting C:\ubuntu
05-21 00:56 DEBUG  TaskList: ## Finished Remove target dir
05-21 00:56 DEBUG  TaskList: ## Running Remove registry key...
05-21 00:56 DEBUG  TaskList: ## Finished Remove registry key
05-21 00:56 DEBUG  TaskList: # Finished tasklist
05-21 00:56 INFO   root: Almost finished uninstalling
05-21 00:56 INFO   root: Finished uninstallation
05-21 00:56 DEBUG  CommonBackend: Fetching basic info...
05-21 00:56 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
05-21 00:56 DEBUG  CommonBackend: platform=win32
05-21 00:56 DEBUG  CommonBackend: osname=nt
05-21 00:56 DEBUG  WindowsBackend: arch=amd64
05-21 00:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\data\isolist.ini
05-21 00:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-21 00:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-21 00:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-21 00:56 DEBUG  WindowsBackend: Fetching host info...
05-21 00:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-21 00:56 DEBUG  WindowsBackend: windows version=vista
05-21 00:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-21 00:56 DEBUG  WindowsBackend: windows_sp=None
05-21 00:56 DEBUG  WindowsBackend: windows_build=7601
05-21 00:56 DEBUG  WindowsBackend: gmt=-5
05-21 00:56 DEBUG  WindowsBackend: country=US
05-21 00:56 DEBUG  WindowsBackend: timezone=America/New_York
05-21 00:56 DEBUG  WindowsBackend: windows_username=Kyle
05-21 00:56 DEBUG  WindowsBackend: user_full_name=Kyle
05-21 00:56 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-21 00:56 DEBUG  WindowsBackend: windows_language_code=1033
05-21 00:56 DEBUG  WindowsBackend: windows_language=English
05-21 00:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-21 00:56 DEBUG  WindowsBackend: bootloader=vista
05-21 00:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 394044.625 mb free ntfs)
05-21 00:56 DEBUG  WindowsBackend: drive=Drive(C: hd 394044.625 mb free ntfs)
05-21 00:56 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-21 00:56 DEBUG  WindowsBackend: uninstaller_path=None
05-21 00:56 DEBUG  WindowsBackend: previous_target_dir=None
05-21 00:56 DEBUG  WindowsBackend: previous_distro_name=None
05-21 00:56 DEBUG  WindowsBackend: keyboard_id=67699721
05-21 00:56 DEBUG  WindowsBackend: keyboard_layout=us
05-21 00:56 DEBUG  WindowsBackend: keyboard_variant=
05-21 00:56 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-21 00:56 DEBUG  CommonBackend: Searching ISOs on USB devices
05-21 00:56 DEBUG  CommonBackend: Searching for local CDs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Ubuntu Netbook CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-21 00:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-21 00:56 INFO   root: Running the installer...
05-21 00:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\translations, languages=['en_US', 'en']
05-21 00:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA9A7.tmp\translations, languages=['en_US', 'en']
05-21 00:56 INFO   WindowsFrontend: Operation cancelled
05-21 00:56 DEBUG  WindowsFrontend: frontend.quit
05-21 00:56 DEBUG  WindowsFrontend: frontend.on_quit
05-21 00:56 DEBUG  root: application.on_quit
05-21 00:56 INFO   root: sys.exit
05-30 21:34 INFO   root: === wubi 11.04 rev211 ===
05-30 21:34 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-30 21:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\wubi.exe"']
05-30 21:34 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\data
05-30 21:34 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\bin\7z.exe
05-30 21:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-30 21:34 DEBUG  CommonBackend: Fetching basic info...
05-30 21:34 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\wubi.exe
05-30 21:34 DEBUG  CommonBackend: platform=win32
05-30 21:34 DEBUG  CommonBackend: osname=nt
05-30 21:34 DEBUG  CommonBackend: language=en_US
05-30 21:34 DEBUG  CommonBackend: encoding=cp1252
05-30 21:34 DEBUG  WindowsBackend: arch=amd64
05-30 21:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\data\isolist.ini
05-30 21:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-30 21:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-30 21:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-30 21:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-30 21:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-30 21:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-30 21:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-30 21:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-30 21:34 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-30 21:34 DEBUG  WindowsBackend: Fetching host info...
05-30 21:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-30 21:34 DEBUG  WindowsBackend: windows version=vista
05-30 21:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-30 21:34 DEBUG  WindowsBackend: windows_sp=None
05-30 21:34 DEBUG  WindowsBackend: windows_build=7601
05-30 21:34 DEBUG  WindowsBackend: gmt=-5
05-30 21:34 DEBUG  WindowsBackend: country=US
05-30 21:34 DEBUG  WindowsBackend: timezone=America/New_York
05-30 21:34 DEBUG  WindowsBackend: windows_username=Kyle
05-30 21:34 DEBUG  WindowsBackend: user_full_name=Kyle
05-30 21:34 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-30 21:34 DEBUG  WindowsBackend: windows_language_code=1033
05-30 21:34 DEBUG  WindowsBackend: windows_language=English
05-30 21:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-30 21:34 DEBUG  WindowsBackend: bootloader=vista
05-30 21:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392421.992188 mb free ntfs)
05-30 21:34 DEBUG  WindowsBackend: drive=Drive(C: hd 392421.992188 mb free ntfs)
05-30 21:34 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-30 21:34 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-30 21:34 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-30 21:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-30 21:34 DEBUG  WindowsBackend: keyboard_id=67699721
05-30 21:34 DEBUG  WindowsBackend: keyboard_layout=us
05-30 21:34 DEBUG  WindowsBackend: keyboard_variant=
05-30 21:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-30 21:34 DEBUG  CommonBackend: locale=en_US.UTF-8
05-30 21:34 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-30 21:34 DEBUG  CommonBackend: Searching ISOs on USB devices
05-30 21:34 DEBUG  CommonBackend: Searching for local CDs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Ubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Ubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Ubuntu Netbook CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Kubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Kubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Xubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Xubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Mythbuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp is a valid Mythbuntu CD
05-30 21:34 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 21:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:34 INFO   root: Already installed, running the uninstaller...
05-30 21:34 INFO   root: Running the uninstaller...
05-30 21:34 INFO   CommonBackend: This is the uninstaller running
05-30 21:34 DEBUG  WindowsFrontend: __init__...
05-30 21:34 DEBUG  WindowsFrontend: on_init...
05-30 21:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\translations, languages=['en_US', 'en']
05-30 21:34 INFO   root: Received settings
05-30 21:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylE96B.tmp\translations, languages=['en_US', 'en']
05-30 21:34 DEBUG  TaskList: # Running tasklist...
05-30 21:34 DEBUG  TaskList: ## Running Backup ISO...
05-30 21:34 DEBUG  TaskList: ## Finished Backup ISO
05-30 21:34 DEBUG  TaskList: ## Running Remove bootloader entry...
05-30 21:34 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-30 21:34 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-30 21:34 DEBUG  TaskList: # Cancelling tasklist
05-30 21:34 DEBUG  TaskList: # Finished tasklist
05-30 21:34 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-30 21:35 INFO   root: === wubi 11.04 rev211 ===
05-30 21:35 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-30 21:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\wubi.exe"']
05-30 21:35 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\data
05-30 21:35 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\bin\7z.exe
05-30 21:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-30 21:35 DEBUG  CommonBackend: Fetching basic info...
05-30 21:35 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\wubi.exe
05-30 21:35 DEBUG  CommonBackend: platform=win32
05-30 21:35 DEBUG  CommonBackend: osname=nt
05-30 21:35 DEBUG  CommonBackend: language=en_US
05-30 21:35 DEBUG  CommonBackend: encoding=cp1252
05-30 21:35 DEBUG  WindowsBackend: arch=amd64
05-30 21:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\data\isolist.ini
05-30 21:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-30 21:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-30 21:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-30 21:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-30 21:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-30 21:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-30 21:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-30 21:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-30 21:35 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-30 21:35 DEBUG  WindowsBackend: Fetching host info...
05-30 21:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-30 21:35 DEBUG  WindowsBackend: windows version=vista
05-30 21:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-30 21:35 DEBUG  WindowsBackend: windows_sp=None
05-30 21:35 DEBUG  WindowsBackend: windows_build=7601
05-30 21:35 DEBUG  WindowsBackend: gmt=-5
05-30 21:35 DEBUG  WindowsBackend: country=US
05-30 21:35 DEBUG  WindowsBackend: timezone=America/New_York
05-30 21:35 DEBUG  WindowsBackend: windows_username=Kyle
05-30 21:35 DEBUG  WindowsBackend: user_full_name=Kyle
05-30 21:35 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-30 21:35 DEBUG  WindowsBackend: windows_language_code=1033
05-30 21:35 DEBUG  WindowsBackend: windows_language=English
05-30 21:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-30 21:35 DEBUG  WindowsBackend: bootloader=vista
05-30 21:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392421.484375 mb free ntfs)
05-30 21:35 DEBUG  WindowsBackend: drive=Drive(C: hd 392421.484375 mb free ntfs)
05-30 21:35 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-30 21:35 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-30 21:35 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-30 21:35 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-30 21:35 DEBUG  WindowsBackend: keyboard_id=67699721
05-30 21:35 DEBUG  WindowsBackend: keyboard_layout=us
05-30 21:35 DEBUG  WindowsBackend: keyboard_variant=
05-30 21:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-30 21:35 DEBUG  CommonBackend: locale=en_US.UTF-8
05-30 21:35 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-30 21:35 DEBUG  CommonBackend: Searching ISOs on USB devices
05-30 21:35 DEBUG  CommonBackend: Searching for local CDs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Ubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Ubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Ubuntu Netbook CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Kubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Kubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Xubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Xubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Mythbuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp is a valid Mythbuntu CD
05-30 21:35 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-30 21:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-30 21:35 INFO   root: Already installed, running the uninstaller...
05-30 21:35 INFO   root: Running the uninstaller...
05-30 21:35 INFO   CommonBackend: This is the uninstaller running
05-30 21:35 DEBUG  WindowsFrontend: __init__...
05-30 21:35 DEBUG  WindowsFrontend: on_init...
05-30 21:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\translations, languages=['en_US', 'en']
05-30 21:35 INFO   root: Received settings
05-30 21:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl1E02.tmp\translations, languages=['en_US', 'en']
05-30 21:35 DEBUG  TaskList: # Running tasklist...
05-30 21:35 DEBUG  TaskList: ## Running Backup ISO...
05-30 21:35 DEBUG  TaskList: ## Finished Backup ISO
05-30 21:35 DEBUG  TaskList: ## Running Remove bootloader entry...
05-30 21:35 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-30 21:35 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-30 21:35 DEBUG  TaskList: # Cancelling tasklist
05-30 21:35 DEBUG  TaskList: # Finished tasklist
05-30 21:35 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:14 INFO   root: === wubi 11.04 rev211 ===
05-31 01:14 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-31 01:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\wubi.exe"']
05-31 01:14 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\data
05-31 01:14 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\bin\7z.exe
05-31 01:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-31 01:14 DEBUG  CommonBackend: Fetching basic info...
05-31 01:14 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\wubi.exe
05-31 01:14 DEBUG  CommonBackend: platform=win32
05-31 01:14 DEBUG  CommonBackend: osname=nt
05-31 01:14 DEBUG  CommonBackend: language=en_US
05-31 01:14 DEBUG  CommonBackend: encoding=cp1252
05-31 01:14 DEBUG  WindowsBackend: arch=amd64
05-31 01:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\data\isolist.ini
05-31 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-31 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-31 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-31 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-31 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-31 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-31 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-31 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-31 01:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-31 01:14 DEBUG  WindowsBackend: Fetching host info...
05-31 01:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-31 01:14 DEBUG  WindowsBackend: windows version=vista
05-31 01:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-31 01:14 DEBUG  WindowsBackend: windows_sp=None
05-31 01:14 DEBUG  WindowsBackend: windows_build=7601
05-31 01:14 DEBUG  WindowsBackend: gmt=-5
05-31 01:14 DEBUG  WindowsBackend: country=US
05-31 01:14 DEBUG  WindowsBackend: timezone=America/New_York
05-31 01:14 DEBUG  WindowsBackend: windows_username=Kyle
05-31 01:14 DEBUG  WindowsBackend: user_full_name=Kyle
05-31 01:14 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-31 01:14 DEBUG  WindowsBackend: windows_language_code=1033
05-31 01:14 DEBUG  WindowsBackend: windows_language=English
05-31 01:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-31 01:14 DEBUG  WindowsBackend: bootloader=vista
05-31 01:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392206.765625 mb free ntfs)
05-31 01:14 DEBUG  WindowsBackend: drive=Drive(C: hd 392206.765625 mb free ntfs)
05-31 01:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-31 01:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-31 01:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-31 01:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-31 01:14 DEBUG  WindowsBackend: keyboard_id=67699721
05-31 01:14 DEBUG  WindowsBackend: keyboard_layout=us
05-31 01:14 DEBUG  WindowsBackend: keyboard_variant=
05-31 01:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-31 01:14 DEBUG  CommonBackend: locale=en_US.UTF-8
05-31 01:14 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-31 01:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-31 01:14 DEBUG  CommonBackend: Searching for local CDs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Ubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Ubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Ubuntu Netbook CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Kubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Kubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Xubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Xubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Mythbuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp is a valid Mythbuntu CD
05-31 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:14 INFO   root: Already installed, running the uninstaller...
05-31 01:14 INFO   root: Running the uninstaller...
05-31 01:14 INFO   CommonBackend: This is the uninstaller running
05-31 01:14 DEBUG  WindowsFrontend: __init__...
05-31 01:14 DEBUG  WindowsFrontend: on_init...
05-31 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\translations, languages=['en_US', 'en']
05-31 01:14 INFO   root: Received settings
05-31 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl674A.tmp\translations, languages=['en_US', 'en']
05-31 01:14 DEBUG  TaskList: # Running tasklist...
05-31 01:14 DEBUG  TaskList: ## Running Backup ISO...
05-31 01:14 DEBUG  TaskList: ## Finished Backup ISO
05-31 01:14 DEBUG  TaskList: ## Running Remove bootloader entry...
05-31 01:14 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-31 01:14 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:14 DEBUG  TaskList: # Cancelling tasklist
05-31 01:14 DEBUG  TaskList: # Finished tasklist
05-31 01:14 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:28 INFO   root: === wubi 11.04 rev211 ===
05-31 01:28 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-31 01:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\wubi.exe"']
05-31 01:28 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\data
05-31 01:28 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\bin\7z.exe
05-31 01:28 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-31 01:28 DEBUG  CommonBackend: Fetching basic info...
05-31 01:28 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\wubi.exe
05-31 01:28 DEBUG  CommonBackend: platform=win32
05-31 01:28 DEBUG  CommonBackend: osname=nt
05-31 01:28 DEBUG  CommonBackend: language=en_US
05-31 01:28 DEBUG  CommonBackend: encoding=cp1252
05-31 01:28 DEBUG  WindowsBackend: arch=amd64
05-31 01:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\data\isolist.ini
05-31 01:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-31 01:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-31 01:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-31 01:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-31 01:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-31 01:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-31 01:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-31 01:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-31 01:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-31 01:28 DEBUG  WindowsBackend: Fetching host info...
05-31 01:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-31 01:28 DEBUG  WindowsBackend: windows version=vista
05-31 01:28 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-31 01:28 DEBUG  WindowsBackend: windows_sp=None
05-31 01:28 DEBUG  WindowsBackend: windows_build=7601
05-31 01:28 DEBUG  WindowsBackend: gmt=-5
05-31 01:28 DEBUG  WindowsBackend: country=US
05-31 01:28 DEBUG  WindowsBackend: timezone=America/New_York
05-31 01:28 DEBUG  WindowsBackend: windows_username=Kyle
05-31 01:28 DEBUG  WindowsBackend: user_full_name=Kyle
05-31 01:28 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-31 01:28 DEBUG  WindowsBackend: windows_language_code=1033
05-31 01:28 DEBUG  WindowsBackend: windows_language=English
05-31 01:28 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-31 01:28 DEBUG  WindowsBackend: bootloader=vista
05-31 01:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392206.863281 mb free ntfs)
05-31 01:28 DEBUG  WindowsBackend: drive=Drive(C: hd 392206.863281 mb free ntfs)
05-31 01:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-31 01:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-31 01:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-31 01:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-31 01:28 DEBUG  WindowsBackend: keyboard_id=67699721
05-31 01:28 DEBUG  WindowsBackend: keyboard_layout=us
05-31 01:28 DEBUG  WindowsBackend: keyboard_variant=
05-31 01:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-31 01:28 DEBUG  CommonBackend: locale=en_US.UTF-8
05-31 01:28 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-31 01:28 DEBUG  CommonBackend: Searching ISOs on USB devices
05-31 01:28 DEBUG  CommonBackend: Searching for local CDs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Ubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Ubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Ubuntu Netbook CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Kubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Kubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Xubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Xubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Mythbuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp is a valid Mythbuntu CD
05-31 01:28 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:28 INFO   root: Already installed, running the uninstaller...
05-31 01:28 INFO   root: Running the uninstaller...
05-31 01:28 INFO   CommonBackend: This is the uninstaller running
05-31 01:28 DEBUG  WindowsFrontend: __init__...
05-31 01:28 DEBUG  WindowsFrontend: on_init...
05-31 01:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\translations, languages=['en_US', 'en']
05-31 01:28 INFO   root: Received settings
05-31 01:28 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl1776.tmp\translations, languages=['en_US', 'en']
05-31 01:28 DEBUG  TaskList: # Running tasklist...
05-31 01:28 DEBUG  TaskList: ## Running Backup ISO...
05-31 01:28 DEBUG  TaskList: ## Finished Backup ISO
05-31 01:28 DEBUG  TaskList: ## Running Remove bootloader entry...
05-31 01:28 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-31 01:28 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:28 DEBUG  TaskList: # Cancelling tasklist
05-31 01:28 DEBUG  TaskList: # Finished tasklist
05-31 01:28 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:29 INFO   root: === wubi 11.04 rev211 ===
05-31 01:29 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
05-31 01:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\wubi.exe"']
05-31 01:29 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\data
05-31 01:29 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\bin\7z.exe
05-31 01:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-31 01:29 DEBUG  CommonBackend: Fetching basic info...
05-31 01:29 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\wubi.exe
05-31 01:29 DEBUG  CommonBackend: platform=win32
05-31 01:29 DEBUG  CommonBackend: osname=nt
05-31 01:29 DEBUG  CommonBackend: language=en_US
05-31 01:29 DEBUG  CommonBackend: encoding=cp1252
05-31 01:29 DEBUG  WindowsBackend: arch=amd64
05-31 01:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\data\isolist.ini
05-31 01:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-31 01:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-31 01:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-31 01:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-31 01:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-31 01:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-31 01:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-31 01:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-31 01:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-31 01:29 DEBUG  WindowsBackend: Fetching host info...
05-31 01:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-31 01:29 DEBUG  WindowsBackend: windows version=vista
05-31 01:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
05-31 01:29 DEBUG  WindowsBackend: windows_sp=None
05-31 01:29 DEBUG  WindowsBackend: windows_build=7601
05-31 01:29 DEBUG  WindowsBackend: gmt=-5
05-31 01:29 DEBUG  WindowsBackend: country=US
05-31 01:29 DEBUG  WindowsBackend: timezone=America/New_York
05-31 01:29 DEBUG  WindowsBackend: windows_username=Kyle
05-31 01:29 DEBUG  WindowsBackend: user_full_name=Kyle
05-31 01:29 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
05-31 01:29 DEBUG  WindowsBackend: windows_language_code=1033
05-31 01:29 DEBUG  WindowsBackend: windows_language=English
05-31 01:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
05-31 01:29 DEBUG  WindowsBackend: bootloader=vista
05-31 01:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392205.722656 mb free ntfs)
05-31 01:29 DEBUG  WindowsBackend: drive=Drive(C: hd 392205.722656 mb free ntfs)
05-31 01:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-31 01:29 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-31 01:29 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-31 01:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-31 01:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-31 01:29 DEBUG  WindowsBackend: keyboard_layout=us
05-31 01:29 DEBUG  WindowsBackend: keyboard_variant=
05-31 01:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-31 01:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-31 01:29 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
05-31 01:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-31 01:29 DEBUG  CommonBackend: Searching for local CDs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Ubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Ubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Ubuntu Netbook CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Kubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Kubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Xubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Xubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Mythbuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp is a valid Mythbuntu CD
05-31 01:29 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-31 01:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-31 01:29 INFO   root: Already installed, running the uninstaller...
05-31 01:29 INFO   root: Running the uninstaller...
05-31 01:29 INFO   CommonBackend: This is the uninstaller running
05-31 01:29 DEBUG  WindowsFrontend: __init__...
05-31 01:29 DEBUG  WindowsFrontend: on_init...
05-31 01:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\translations, languages=['en_US', 'en']
05-31 01:29 INFO   root: Received settings
05-31 01:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylA2C4.tmp\translations, languages=['en_US', 'en']
05-31 01:29 DEBUG  TaskList: # Running tasklist...
05-31 01:29 DEBUG  TaskList: ## Running Backup ISO...
05-31 01:29 DEBUG  TaskList: ## Finished Backup ISO
05-31 01:29 DEBUG  TaskList: ## Running Remove bootloader entry...
05-31 01:29 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
05-31 01:29 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-31 01:29 DEBUG  TaskList: # Cancelling tasklist
05-31 01:29 DEBUG  TaskList: # Finished tasklist
05-31 01:29 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 00:38 INFO   root: === wubi 11.04 rev211 ===
06-01 00:38 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 00:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
06-01 00:38 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\data
06-01 00:38 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\bin\7z.exe
06-01 00:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 00:38 DEBUG  CommonBackend: Fetching basic info...
06-01 00:38 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
06-01 00:38 DEBUG  CommonBackend: platform=win32
06-01 00:38 DEBUG  CommonBackend: osname=nt
06-01 00:38 DEBUG  CommonBackend: language=en_US
06-01 00:38 DEBUG  CommonBackend: encoding=cp1252
06-01 00:38 DEBUG  WindowsBackend: arch=amd64
06-01 00:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\data\isolist.ini
06-01 00:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 00:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 00:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 00:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 00:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 00:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 00:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 00:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 00:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 00:38 DEBUG  WindowsBackend: Fetching host info...
06-01 00:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 00:38 DEBUG  WindowsBackend: windows version=vista
06-01 00:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 00:38 DEBUG  WindowsBackend: windows_sp=None
06-01 00:38 DEBUG  WindowsBackend: windows_build=7601
06-01 00:38 DEBUG  WindowsBackend: gmt=-5
06-01 00:38 DEBUG  WindowsBackend: country=US
06-01 00:38 DEBUG  WindowsBackend: timezone=America/New_York
06-01 00:38 DEBUG  WindowsBackend: windows_username=Kyle
06-01 00:38 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 00:38 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 00:38 DEBUG  WindowsBackend: windows_language_code=1033
06-01 00:38 DEBUG  WindowsBackend: windows_language=English
06-01 00:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 00:38 DEBUG  WindowsBackend: bootloader=vista
06-01 00:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392110.835938 mb free ntfs)
06-01 00:38 DEBUG  WindowsBackend: drive=Drive(C: hd 392110.835938 mb free ntfs)
06-01 00:38 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 00:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 00:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 00:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 00:38 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 00:38 DEBUG  WindowsBackend: keyboard_layout=us
06-01 00:38 DEBUG  WindowsBackend: keyboard_variant=
06-01 00:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 00:38 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 00:38 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 00:38 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 00:38 DEBUG  CommonBackend: Searching for local CDs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Ubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Ubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Ubuntu Netbook CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Kubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Kubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Xubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Xubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Mythbuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp is a valid Mythbuntu CD
06-01 00:38 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 00:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 00:38 INFO   root: Already installed, running the uninstaller...
06-01 00:38 INFO   root: Running the uninstaller...
06-01 00:38 INFO   CommonBackend: This is the uninstaller running
06-01 00:38 DEBUG  WindowsFrontend: __init__...
06-01 00:38 DEBUG  WindowsFrontend: on_init...
06-01 00:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\translations, languages=['en_US', 'en']
06-01 00:38 INFO   root: Received settings
06-01 00:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylFCBF.tmp\translations, languages=['en_US', 'en']
06-01 00:38 DEBUG  TaskList: # Running tasklist...
06-01 00:38 DEBUG  TaskList: ## Running Backup ISO...
06-01 00:38 DEBUG  TaskList: ## Finished Backup ISO
06-01 00:38 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 00:38 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 00:38 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 00:38 DEBUG  TaskList: # Cancelling tasklist
06-01 00:38 DEBUG  TaskList: # Finished tasklist
06-01 00:38 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:05 INFO   root: === wubi 11.04 rev211 ===
06-01 01:05 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
06-01 01:05 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\data
06-01 01:05 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\bin\7z.exe
06-01 01:05 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:05 DEBUG  CommonBackend: Fetching basic info...
06-01 01:05 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
06-01 01:05 DEBUG  CommonBackend: platform=win32
06-01 01:05 DEBUG  CommonBackend: osname=nt
06-01 01:05 DEBUG  CommonBackend: language=en_US
06-01 01:05 DEBUG  CommonBackend: encoding=cp1252
06-01 01:05 DEBUG  WindowsBackend: arch=amd64
06-01 01:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\data\isolist.ini
06-01 01:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:05 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:05 DEBUG  WindowsBackend: Fetching host info...
06-01 01:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:05 DEBUG  WindowsBackend: windows version=vista
06-01 01:05 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 01:05 DEBUG  WindowsBackend: windows_sp=None
06-01 01:05 DEBUG  WindowsBackend: windows_build=7601
06-01 01:05 DEBUG  WindowsBackend: gmt=-5
06-01 01:05 DEBUG  WindowsBackend: country=US
06-01 01:05 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:05 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:05 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:05 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:05 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:05 DEBUG  WindowsBackend: windows_language=English
06-01 01:05 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:05 DEBUG  WindowsBackend: bootloader=vista
06-01 01:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392115.359375 mb free ntfs)
06-01 01:05 DEBUG  WindowsBackend: drive=Drive(C: hd 392115.359375 mb free ntfs)
06-01 01:05 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:05 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:05 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:05 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:05 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:05 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:05 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 01:05 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:05 DEBUG  CommonBackend: Searching for local CDs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Ubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Ubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Ubuntu Netbook CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Kubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Kubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Xubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Xubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Mythbuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp is a valid Mythbuntu CD
06-01 01:05 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:05 INFO   root: Already installed, running the uninstaller...
06-01 01:05 INFO   root: Running the uninstaller...
06-01 01:05 INFO   CommonBackend: This is the uninstaller running
06-01 01:05 DEBUG  WindowsFrontend: __init__...
06-01 01:05 DEBUG  WindowsFrontend: on_init...
06-01 01:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\translations, languages=['en_US', 'en']
06-01 01:05 INFO   root: Received settings
06-01 01:05 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylAA3D.tmp\translations, languages=['en_US', 'en']
06-01 01:05 DEBUG  TaskList: # Running tasklist...
06-01 01:05 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:05 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:05 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:05 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:05 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:05 DEBUG  TaskList: # Cancelling tasklist
06-01 01:05 DEBUG  TaskList: # Finished tasklist
06-01 01:05 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:12 INFO   root: === wubi 11.04 rev211 ===
06-01 01:12 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:12 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Documents\\Ubuntu\\wubi_11.04.exe"']
06-01 01:12 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\data
06-01 01:12 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\bin\7z.exe
06-01 01:12 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:12 DEBUG  CommonBackend: Fetching basic info...
06-01 01:12 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Documents\Ubuntu\wubi_11.04.exe
06-01 01:12 DEBUG  CommonBackend: platform=win32
06-01 01:12 DEBUG  CommonBackend: osname=nt
06-01 01:12 DEBUG  CommonBackend: language=en_US
06-01 01:12 DEBUG  CommonBackend: encoding=cp1252
06-01 01:12 DEBUG  WindowsBackend: arch=amd64
06-01 01:12 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\data\isolist.ini
06-01 01:12 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:12 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:12 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:12 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:12 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:12 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:12 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:12 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:12 DEBUG  WindowsBackend: Fetching host info...
06-01 01:12 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:12 DEBUG  WindowsBackend: windows version=vista
06-01 01:12 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 01:12 DEBUG  WindowsBackend: windows_sp=None
06-01 01:12 DEBUG  WindowsBackend: windows_build=7601
06-01 01:12 DEBUG  WindowsBackend: gmt=-5
06-01 01:12 DEBUG  WindowsBackend: country=US
06-01 01:12 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:12 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:12 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:12 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:12 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:12 DEBUG  WindowsBackend: windows_language=English
06-01 01:12 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:12 DEBUG  WindowsBackend: bootloader=vista
06-01 01:12 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392113.027344 mb free ntfs)
06-01 01:12 DEBUG  WindowsBackend: drive=Drive(C: hd 392113.027344 mb free ntfs)
06-01 01:12 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:12 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:12 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:12 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:12 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:12 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:12 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:12 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:12 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:12 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 01:12 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:12 DEBUG  CommonBackend: Searching for local CDs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Ubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Ubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Ubuntu Netbook CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Kubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Kubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Xubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Xubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Mythbuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp is a valid Mythbuntu CD
06-01 01:12 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:12 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:12 INFO   root: Already installed, running the uninstaller...
06-01 01:12 INFO   root: Running the uninstaller...
06-01 01:12 INFO   CommonBackend: This is the uninstaller running
06-01 01:12 DEBUG  WindowsFrontend: __init__...
06-01 01:12 DEBUG  WindowsFrontend: on_init...
06-01 01:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\translations, languages=['en_US', 'en']
06-01 01:12 INFO   root: Received settings
06-01 01:12 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylAE14.tmp\translations, languages=['en_US', 'en']
06-01 01:12 DEBUG  TaskList: # Running tasklist...
06-01 01:12 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:12 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:12 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:12 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:12 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:12 DEBUG  TaskList: # Cancelling tasklist
06-01 01:12 DEBUG  TaskList: # Finished tasklist
06-01 01:12 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:14 INFO   root: === wubi 11.04 rev211 ===
06-01 01:14 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Desktop\\wubi_11.04.exe"']
06-01 01:14 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\data
06-01 01:14 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\bin\7z.exe
06-01 01:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:14 DEBUG  CommonBackend: Fetching basic info...
06-01 01:14 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Desktop\wubi_11.04.exe
06-01 01:14 DEBUG  CommonBackend: platform=win32
06-01 01:14 DEBUG  CommonBackend: osname=nt
06-01 01:14 DEBUG  CommonBackend: language=en_US
06-01 01:14 DEBUG  CommonBackend: encoding=cp1252
06-01 01:14 DEBUG  WindowsBackend: arch=amd64
06-01 01:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\data\isolist.ini
06-01 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:14 DEBUG  WindowsBackend: Fetching host info...
06-01 01:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:14 DEBUG  WindowsBackend: windows version=vista
06-01 01:14 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 01:14 DEBUG  WindowsBackend: windows_sp=None
06-01 01:14 DEBUG  WindowsBackend: windows_build=7601
06-01 01:14 DEBUG  WindowsBackend: gmt=-5
06-01 01:14 DEBUG  WindowsBackend: country=US
06-01 01:14 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:14 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:14 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:14 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:14 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:14 DEBUG  WindowsBackend: windows_language=English
06-01 01:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:14 DEBUG  WindowsBackend: bootloader=vista
06-01 01:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392115.417969 mb free ntfs)
06-01 01:14 DEBUG  WindowsBackend: drive=Drive(C: hd 392115.417969 mb free ntfs)
06-01 01:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:14 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:14 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:14 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:14 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:14 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:14 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 01:14 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:14 DEBUG  CommonBackend: Searching for local CDs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Ubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Ubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Ubuntu Netbook CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Kubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Kubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Xubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Xubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Mythbuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp is a valid Mythbuntu CD
06-01 01:14 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:14 INFO   root: Already installed, running the uninstaller...
06-01 01:14 INFO   root: Running the uninstaller...
06-01 01:14 INFO   CommonBackend: This is the uninstaller running
06-01 01:14 DEBUG  WindowsFrontend: __init__...
06-01 01:14 DEBUG  WindowsFrontend: on_init...
06-01 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\translations, languages=['en_US', 'en']
06-01 01:14 INFO   root: Received settings
06-01 01:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylEEAC.tmp\translations, languages=['en_US', 'en']
06-01 01:14 DEBUG  TaskList: # Running tasklist...
06-01 01:14 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:14 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:14 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:14 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:14 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:14 DEBUG  TaskList: # Cancelling tasklist
06-01 01:14 DEBUG  TaskList: # Finished tasklist
06-01 01:14 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:17 INFO   root: === wubi 11.04 rev211 ===
06-01 01:17 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Desktop\\wubi_11.04.exe"']
06-01 01:17 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\data
06-01 01:17 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\bin\7z.exe
06-01 01:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:17 DEBUG  CommonBackend: Fetching basic info...
06-01 01:17 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Desktop\wubi_11.04.exe
06-01 01:17 DEBUG  CommonBackend: platform=win32
06-01 01:17 DEBUG  CommonBackend: osname=nt
06-01 01:17 DEBUG  CommonBackend: language=en_US
06-01 01:17 DEBUG  CommonBackend: encoding=cp1252
06-01 01:17 DEBUG  WindowsBackend: arch=amd64
06-01 01:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\data\isolist.ini
06-01 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:17 DEBUG  WindowsBackend: Fetching host info...
06-01 01:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:17 DEBUG  WindowsBackend: windows version=vista
06-01 01:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 01:17 DEBUG  WindowsBackend: windows_sp=None
06-01 01:17 DEBUG  WindowsBackend: windows_build=7601
06-01 01:17 DEBUG  WindowsBackend: gmt=-5
06-01 01:17 DEBUG  WindowsBackend: country=US
06-01 01:17 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:17 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:17 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:17 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:17 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:17 DEBUG  WindowsBackend: windows_language=English
06-01 01:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:17 DEBUG  WindowsBackend: bootloader=vista
06-01 01:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392114.226563 mb free ntfs)
06-01 01:17 DEBUG  WindowsBackend: drive=Drive(C: hd 392114.226563 mb free ntfs)
06-01 01:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:17 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:17 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:17 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:17 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:17 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 01:17 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:17 DEBUG  CommonBackend: Searching for local CDs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Ubuntu Netbook CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 INFO   root: Already installed, running the uninstaller...
06-01 01:17 INFO   root: Running the uninstaller...
06-01 01:17 INFO   CommonBackend: This is the uninstaller running
06-01 01:17 DEBUG  WindowsFrontend: __init__...
06-01 01:17 DEBUG  WindowsFrontend: on_init...
06-01 01:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\translations, languages=['en_US', 'en']
06-01 01:17 INFO   root: Received settings
06-01 01:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl5F97.tmp\translations, languages=['en_US', 'en']
06-01 01:17 DEBUG  TaskList: # Running tasklist...
06-01 01:17 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:17 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:17 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:17 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:17 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:17 DEBUG  TaskList: # Cancelling tasklist
06-01 01:17 DEBUG  TaskList: # Finished tasklist
06-01 01:17 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:17 INFO   root: === wubi 11.04 rev211 ===
06-01 01:17 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:17 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Kyle\\Desktop\\wubi_11.04.exe"']
06-01 01:17 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\data
06-01 01:17 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\bin\7z.exe
06-01 01:17 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:17 DEBUG  CommonBackend: Fetching basic info...
06-01 01:17 DEBUG  CommonBackend: original_exe=C:\Users\Kyle\Desktop\wubi_11.04.exe
06-01 01:17 DEBUG  CommonBackend: platform=win32
06-01 01:17 DEBUG  CommonBackend: osname=nt
06-01 01:17 DEBUG  CommonBackend: language=en_US
06-01 01:17 DEBUG  CommonBackend: encoding=cp1252
06-01 01:17 DEBUG  WindowsBackend: arch=amd64
06-01 01:17 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\data\isolist.ini
06-01 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:17 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:17 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:17 DEBUG  WindowsBackend: Fetching host info...
06-01 01:17 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:17 DEBUG  WindowsBackend: windows version=vista
06-01 01:17 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
06-01 01:17 DEBUG  WindowsBackend: windows_sp=None
06-01 01:17 DEBUG  WindowsBackend: windows_build=7601
06-01 01:17 DEBUG  WindowsBackend: gmt=-5
06-01 01:17 DEBUG  WindowsBackend: country=US
06-01 01:17 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:17 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:17 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:17 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:17 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:17 DEBUG  WindowsBackend: windows_language=English
06-01 01:17 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:17 DEBUG  WindowsBackend: bootloader=vista
06-01 01:17 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392114.195313 mb free ntfs)
06-01 01:17 DEBUG  WindowsBackend: drive=Drive(C: hd 392114.195313 mb free ntfs)
06-01 01:17 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:17 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:17 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:17 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:17 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:17 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:17 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:17 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:17 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:17 DEBUG  WindowsBackend: total_memory_mb=2996.5234375
06-01 01:17 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:17 DEBUG  CommonBackend: Searching for local CDs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Ubuntu Netbook CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:17 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:17 INFO   root: Already installed, running the uninstaller...
06-01 01:17 INFO   root: Running the uninstaller...
06-01 01:17 INFO   CommonBackend: This is the uninstaller running
06-01 01:17 DEBUG  WindowsFrontend: __init__...
06-01 01:17 DEBUG  WindowsFrontend: on_init...
06-01 01:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\translations, languages=['en_US', 'en']
06-01 01:17 INFO   root: Received settings
06-01 01:17 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pylD285.tmp\translations, languages=['en_US', 'en']
06-01 01:17 DEBUG  TaskList: # Running tasklist...
06-01 01:17 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:17 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:17 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:17 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:17 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:17 DEBUG  TaskList: # Cancelling tasklist
06-01 01:17 DEBUG  TaskList: # Finished tasklist
06-01 01:17 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 144, in run_installer
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:24 INFO   root: === wubi 11.04 rev211 ===
06-01 01:24 DEBUG  root: Logfile is c:\users\kyle\appdata\local\temp\wubi-11.04-rev211.log
06-01 01:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
06-01 01:24 DEBUG  CommonBackend: data_dir=C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\data
06-01 01:24 DEBUG  WindowsBackend: 7z=C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\bin\7z.exe
06-01 01:24 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
06-01 01:24 DEBUG  CommonBackend: Fetching basic info...
06-01 01:24 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
06-01 01:24 DEBUG  CommonBackend: platform=win32
06-01 01:24 DEBUG  CommonBackend: osname=nt
06-01 01:24 DEBUG  CommonBackend: language=en_US
06-01 01:24 DEBUG  CommonBackend: encoding=cp1252
06-01 01:24 DEBUG  WindowsBackend: arch=amd64
06-01 01:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\data\isolist.ini
06-01 01:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-01 01:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-01 01:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-01 01:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-01 01:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-01 01:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-01 01:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-01 01:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-01 01:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-01 01:24 DEBUG  WindowsBackend: Fetching host info...
06-01 01:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-01 01:24 DEBUG  WindowsBackend: windows version=vista
06-01 01:24 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
06-01 01:24 DEBUG  WindowsBackend: windows_sp=None
06-01 01:24 DEBUG  WindowsBackend: windows_build=6000
06-01 01:24 DEBUG  WindowsBackend: gmt=-5
06-01 01:24 DEBUG  WindowsBackend: country=US
06-01 01:24 DEBUG  WindowsBackend: timezone=America/New_York
06-01 01:24 DEBUG  WindowsBackend: windows_username=Kyle
06-01 01:24 DEBUG  WindowsBackend: user_full_name=Kyle
06-01 01:24 DEBUG  WindowsBackend: user_directory=C:\Users\Kyle
06-01 01:24 DEBUG  WindowsBackend: windows_language_code=1033
06-01 01:24 DEBUG  WindowsBackend: windows_language=English
06-01 01:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i3 CPU       M 330  @ 2.13GHz
06-01 01:24 DEBUG  WindowsBackend: bootloader=vista
06-01 01:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 392113.695313 mb free ntfs)
06-01 01:24 DEBUG  WindowsBackend: drive=Drive(C: hd 392113.695313 mb free ntfs)
06-01 01:24 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
06-01 01:24 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-01 01:24 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-01 01:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-01 01:24 DEBUG  WindowsBackend: keyboard_id=67699721
06-01 01:24 DEBUG  WindowsBackend: keyboard_layout=us
06-01 01:24 DEBUG  WindowsBackend: keyboard_variant=
06-01 01:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
06-01 01:24 DEBUG  CommonBackend: locale=en_US.UTF-8
06-01 01:24 DEBUG  WindowsBackend: total_memory_mb=1023.99999905
06-01 01:24 DEBUG  CommonBackend: Searching ISOs on USB devices
06-01 01:24 DEBUG  CommonBackend: Searching for local CDs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Ubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Ubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Ubuntu Netbook CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Kubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Kubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Xubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Xubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Mythbuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp is a valid Mythbuntu CD
06-01 01:24 DEBUG  Distro:     does not contain C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-01 01:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-01 01:24 INFO   root: Running the uninstaller...
06-01 01:24 INFO   CommonBackend: This is the uninstaller running
06-01 01:24 DEBUG  WindowsFrontend: __init__...
06-01 01:24 DEBUG  WindowsFrontend: on_init...
06-01 01:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\translations, languages=['en_US', 'en']
06-01 01:24 INFO   root: Received settings
06-01 01:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Kyle\AppData\Local\Temp\pyl921C.tmp\translations, languages=['en_US', 'en']
06-01 01:24 DEBUG  TaskList: # Running tasklist...
06-01 01:24 DEBUG  TaskList: ## Running Backup ISO...
06-01 01:24 DEBUG  TaskList: ## Finished Backup ISO
06-01 01:24 DEBUG  TaskList: ## Running Remove bootloader entry...
06-01 01:24 DEBUG  WindowsBackend: Removing bcd entry {599f1816-6055-11e0-b332-b8ac6f70cae5}
06-01 01:24 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
06-01 01:24 DEBUG  TaskList: # Cancelling tasklist
06-01 01:24 DEBUG  TaskList: # Finished tasklist
06-01 01:24 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 123, in select_task
  File "\lib\wubi\application.py", line 178, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 518, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 701, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 62, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /delete {599f1816-6055-11e0-b332-b8ac6f70cae5} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=



```

---

### Post by bcbc on 2011-06-01
The good news is there is no partition to remove. The instructions you linked to is to remove a normal partition installed dual boot, not with Wubi (which uses a virtual partition - the file \ubuntu\disks\root.disk).

You should be able to to manually uninstall as described in the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?").

---

### Post by Coaxsist on 2011-06-01
> **bcbc said:**
> The good news is there is no partition to remove. The instructions you linked to is to remove a normal partition installed dual boot, not with Wubi (which uses a virtual partition - the file \ubuntu\disks\root.disk).

You should be able to to manually uninstall as described in the [Wubi guide]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?").

Wow, thanks! A virtual partition? Admittedly, I've never heard of such a thing... It seems though that Ubuntu would run better on an actual physical partition instead of a virtual one. Is that true? I'm about to download the .iso and try to install from a flash drive. Will that put it on a physical partition? Also, why is a 32x version of Ubuntu recommended for use, especially on a 64x OS?

Thanks again.

---

### Post by Coaxsist on 2011-06-01
I got it.

I went here: [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe)

and downloaded "Uninstall-Ubuntu.exe" and it worked flawlessly.

Thanks.

---

### Post by bcbc on 2011-06-01
> **Coaxsist said:**
> Wow, thanks! A virtual partition? Admittedly, I've never heard of such a thing... It seems though that Ubuntu would run better on an actual physical partition instead of a virtual one. Is that true? I'm about to download the .iso and try to install from a flash drive. Will that put it on a physical partition? Also, why is a 32x version of Ubuntu recommended for use, especially on a 64x OS?

Thanks again.

The virtual partition is only used with Wubi (windows ubuntu installer) and it's mainly to try out Ubuntu as a dual boot, but without partitioning.
If you boot from the flash drive or a CD and install, it will always be to a physical partition.
Yes it runs better on an actual partition - although Wubi is a pretty close experience. I run both and it's a little slower (mainly for booting) and there's a possibility of corruption with a hard power off, but other than that it's pretty much the same.

I don't know why they still recommend 32 bit.

---

### Post by Coaxsist on 2011-06-01
Cool, thanks.

---

