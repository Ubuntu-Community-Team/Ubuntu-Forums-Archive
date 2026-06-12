---
title: "problem with wubi!!!"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by amit.neo2000 on 2011-05-15
I'm having problem installing Ubuntu 11.04 inside windows using wubi.
the download aromatically stops after some time...
I'm copying the log file text with this... please help.
it always stops after downloading 70-80 Mb.
I have pppoe type internet connection...



here's the log:


05-15 19:37 INFO   root: === wubi 11.04 rev211 ===
05-15 19:37 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-15 19:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Operating Systems\\wubi.exe"']
05-15 19:37 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\data
05-15 19:37 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\bin\7z.exe
05-15 19:37 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-15 19:37 DEBUG  CommonBackend: Fetching basic info...
05-15 19:37 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-15 19:37 DEBUG  CommonBackend: platform=win32
05-15 19:37 DEBUG  CommonBackend: osname=nt
05-15 19:37 DEBUG  CommonBackend: language=en_US
05-15 19:37 DEBUG  CommonBackend: encoding=cp1252
05-15 19:37 DEBUG  WindowsBackend: arch=amd64
05-15 19:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\data\isolist.ini
05-15 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 19:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 19:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 19:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 19:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 19:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-15 19:37 DEBUG  WindowsBackend: Fetching host info...
05-15 19:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 19:37 DEBUG  WindowsBackend: windows version=vista
05-15 19:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-15 19:37 DEBUG  WindowsBackend: windows_sp=None
05-15 19:37 DEBUG  WindowsBackend: windows_build=7600
05-15 19:37 DEBUG  WindowsBackend: gmt=5
05-15 19:37 DEBUG  WindowsBackend: country=US
05-15 19:37 DEBUG  WindowsBackend: timezone=America/New_York
05-15 19:37 DEBUG  WindowsBackend: windows_username=Amit
05-15 19:37 DEBUG  WindowsBackend: user_full_name=Amit
05-15 19:37 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-15 19:37 DEBUG  WindowsBackend: windows_language_code=1033
05-15 19:37 DEBUG  WindowsBackend: windows_language=English
05-15 19:37 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-15 19:37 DEBUG  WindowsBackend: bootloader=vista
05-15 19:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26592.1601563 mb free ntfs)
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(C: hd 26592.1601563 mb free ntfs)
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(D: hd 27085.25 mb free ntfs)
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-15 19:37 DEBUG  WindowsBackend: uninstaller_path=None
05-15 19:37 DEBUG  WindowsBackend: previous_target_dir=None
05-15 19:37 DEBUG  WindowsBackend: previous_distro_name=None
05-15 19:37 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 19:37 DEBUG  WindowsBackend: keyboard_layout=us
05-15 19:37 DEBUG  WindowsBackend: keyboard_variant=
05-15 19:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-15 19:37 DEBUG  CommonBackend: locale=en_US.UTF-8
05-15 19:37 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-15 19:37 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 19:37 DEBUG  CommonBackend: Searching for local CDs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 19:37 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:37 INFO   root: Running the installer...
05-15 19:37 DEBUG  WindowsFrontend: __init__...
05-15 19:37 DEBUG  WindowsFrontend: on_init...
05-15 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\translations, languages=['en_US', 'en']
05-15 19:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\translations, languages=['en_US', 'en']
05-15 19:38 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=amit
05-15 19:38 INFO   root: Received settings
05-15 19:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\translations, languages=['en_US', 'en']
05-15 19:38 DEBUG  TaskList: # Running tasklist...
05-15 19:38 DEBUG  TaskList: ## Running select_target_dir...
05-15 19:38 INFO   WindowsBackend: Installing into C:\ubuntu
05-15 19:38 DEBUG  TaskList: ## Finished select_target_dir
05-15 19:38 DEBUG  TaskList: ## Running create_dir_structure...
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-15 19:38 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-15 19:38 DEBUG  TaskList: ## Finished create_dir_structure
05-15 19:38 DEBUG  TaskList: ## Running uncompress_target_dir...
05-15 19:38 DEBUG  TaskList: ## Finished uncompress_target_dir
05-15 19:38 DEBUG  TaskList: ## Running create_uninstaller...
05-15 19:38 DEBUG  WindowsBackend: Copying uninstaller D:\Operating Systems\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-15 19:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-15 19:38 DEBUG  TaskList: ## Finished create_uninstaller
05-15 19:38 DEBUG  TaskList: ## Running copy_installation_files...
05-15 19:38 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-15 19:38 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\winboot -> C:\ubuntu\winboot
05-15 19:38 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-15 19:38 DEBUG  TaskList: ## Finished copy_installation_files
05-15 19:38 DEBUG  TaskList: ## Running get_iso...
05-15 19:38 DEBUG  CommonBackend: Searching for local CD
05-15 19:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl5E47.tmp\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 19:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 19:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 19:38 DEBUG  CommonBackend: Searching for local ISO
05-15 19:38 DEBUG  Distro:   checking Ubuntu ISO D:\Operating Systems\ubuntu-10.10-desktop-i386.iso
05-15 19:38 DEBUG  Distro:     does not contain casper\filesystem.squashfs
05-15 19:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-15 19:38 DEBUG  TaskList: New task get_metalink
05-15 19:38 DEBUG  TaskList: ### Running get_metalink...
05-15 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-15 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-15 19:38 DEBUG  downloader: download finished (read 28363 bytes)
05-15 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-15 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-15 19:38 DEBUG  downloader: download finished (read 874 bytes)
05-15 19:38 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-15 19:38 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-15 19:38 DEBUG  downloader: download finished (read 198 bytes)
05-15 19:38 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-15 19:38 INFO   saplog: Checking block bindings..
05-15 19:38 INFO   saplog: Key verified successfully.
05-15 19:38 DEBUG  CommonBackend: metalink md5sums:
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

05-15 19:38 DEBUG  TaskList: ### Finished get_metalink
05-15 19:38 DEBUG  TaskList: New task download
05-15 19:38 DEBUG  TaskList: ### Running download...
05-15 19:38 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-15 20:08 ERROR  TaskList: (10053, 'Software caused connection abort')
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 120, in download
  File "\lib\urllib2.py", line 129, in urlopen
  File "\lib\urllib2.py", line 326, in open
  File "\lib\urllib2.py", line 306, in _call_chain
  File "\lib\bittorrent\zurllib.py", line 33, in http_open
  File "\lib\urllib2.py", line 901, in http_open
  File "\lib\urllib2.py", line 890, in do_open
  File "\lib\httplib.py", line 1052, in getreply
  File "\lib\httplib.py", line 781, in getresponse
  File "\lib\httplib.py", line 273, in begin
  File "\lib\httplib.py", line 231, in _read_status
  File "\lib\socket.py", line 323, in readline
error: (10053, 'Software caused connection abort')
05-15 20:08 ERROR  TaskList: Non fatal error (10053, 'Software caused connection abort') in task download
05-15 20:08 DEBUG  TaskList: ### Finished download
05-15 20:08 DEBUG  TaskList: New task download
05-15 20:08 DEBUG  TaskList: ### Running download...
05-15 20:08 DEBUG  downloader: downloading [http://ftp.heanet.ie/pub/ubuntu-releases/11.04/ubuntu-11.04-desktop-amd64.iso](http://ftp.heanet.ie/pub/ubuntu-releases/11.04/ubuntu-11.04-desktop-amd64.iso) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-15 20:08 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-15 20:08 DEBUG  TaskList: # Cancelling tasklist
05-15 20:08 ERROR  root: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 78, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
05-15 20:08 DEBUG  TaskList: New task download
05-15 20:08 DEBUG  TaskList: New task download
05-15 20:08 DEBUG  TaskList: New task download
05-15 20:08 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 497, in get_iso
Exception: Could not retrieve the required installation files
05-15 20:08 DEBUG  TaskList: # Cancelling tasklist
05-15 20:08 DEBUG  TaskList: # Finished tasklist
05-15 20:32 INFO   root: === wubi 11.04 rev211 ===
05-15 20:32 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-15 20:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Operating Systems\\wubi.exe"']
05-15 20:32 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\data
05-15 20:32 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\bin\7z.exe
05-15 20:32 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-15 20:32 DEBUG  CommonBackend: Fetching basic info...
05-15 20:32 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-15 20:32 DEBUG  CommonBackend: platform=win32
05-15 20:32 DEBUG  CommonBackend: osname=nt
05-15 20:32 DEBUG  CommonBackend: language=en_US
05-15 20:32 DEBUG  CommonBackend: encoding=cp1252
05-15 20:32 DEBUG  WindowsBackend: arch=amd64
05-15 20:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\data\isolist.ini
05-15 20:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-15 20:32 DEBUG  WindowsBackend: Fetching host info...
05-15 20:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 20:32 DEBUG  WindowsBackend: windows version=vista
05-15 20:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-15 20:32 DEBUG  WindowsBackend: windows_sp=None
05-15 20:32 DEBUG  WindowsBackend: windows_build=7600
05-15 20:32 DEBUG  WindowsBackend: gmt=5
05-15 20:32 DEBUG  WindowsBackend: country=US
05-15 20:32 DEBUG  WindowsBackend: timezone=America/New_York
05-15 20:32 DEBUG  WindowsBackend: windows_username=Amit
05-15 20:32 DEBUG  WindowsBackend: user_full_name=Amit
05-15 20:32 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-15 20:32 DEBUG  WindowsBackend: windows_language_code=1033
05-15 20:32 DEBUG  WindowsBackend: windows_language=English
05-15 20:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-15 20:32 DEBUG  WindowsBackend: bootloader=vista
05-15 20:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26594.8203125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(C: hd 26594.8203125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-15 20:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-15 20:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-15 20:32 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 20:32 DEBUG  WindowsBackend: keyboard_layout=us
05-15 20:32 DEBUG  WindowsBackend: keyboard_variant=
05-15 20:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-15 20:32 DEBUG  CommonBackend: locale=en_US.UTF-8
05-15 20:32 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-15 20:32 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 20:32 DEBUG  CommonBackend: Searching for local CDs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 INFO   root: Already installed, running the uninstaller...
05-15 20:32 INFO   root: Running the uninstaller...
05-15 20:32 INFO   CommonBackend: This is the uninstaller running
05-15 20:32 DEBUG  WindowsFrontend: __init__...
05-15 20:32 DEBUG  WindowsFrontend: on_init...
05-15 20:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\translations, languages=['en_US', 'en']
05-15 20:32 INFO   root: Received settings
05-15 20:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\translations, languages=['en_US', 'en']
05-15 20:32 DEBUG  TaskList: # Running tasklist...
05-15 20:32 DEBUG  TaskList: ## Running Backup ISO...
05-15 20:32 DEBUG  TaskList: ## Finished Backup ISO
05-15 20:32 DEBUG  TaskList: ## Running Remove bootloader entry...
05-15 20:32 DEBUG  WindowsBackend: Could not find bcd id
05-15 20:32 DEBUG  WindowsBackend: undo_bootini C:
05-15 20:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 26594.8203125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: undo_bootini D:
05-15 20:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 27195.2578125 mb free ntfs)
05-15 20:32 DEBUG  TaskList: ## Finished Remove bootloader entry
05-15 20:32 DEBUG  TaskList: ## Running Remove target dir...
05-15 20:32 DEBUG  CommonBackend: Deleting C:\ubuntu
05-15 20:32 DEBUG  TaskList: ## Finished Remove target dir
05-15 20:32 DEBUG  TaskList: ## Running Remove registry key...
05-15 20:32 DEBUG  TaskList: ## Finished Remove registry key
05-15 20:32 DEBUG  TaskList: # Finished tasklist
05-15 20:32 INFO   root: Almost finished uninstalling
05-15 20:32 INFO   root: Finished uninstallation
05-15 20:32 DEBUG  CommonBackend: Fetching basic info...
05-15 20:32 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-15 20:32 DEBUG  CommonBackend: platform=win32
05-15 20:32 DEBUG  CommonBackend: osname=nt
05-15 20:32 DEBUG  WindowsBackend: arch=amd64
05-15 20:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\data\isolist.ini
05-15 20:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-15 20:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-15 20:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-15 20:32 DEBUG  WindowsBackend: Fetching host info...
05-15 20:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-15 20:32 DEBUG  WindowsBackend: windows version=vista
05-15 20:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-15 20:32 DEBUG  WindowsBackend: windows_sp=None
05-15 20:32 DEBUG  WindowsBackend: windows_build=7600
05-15 20:32 DEBUG  WindowsBackend: gmt=5
05-15 20:32 DEBUG  WindowsBackend: country=US
05-15 20:32 DEBUG  WindowsBackend: timezone=America/New_York
05-15 20:32 DEBUG  WindowsBackend: windows_username=Amit
05-15 20:32 DEBUG  WindowsBackend: user_full_name=Amit
05-15 20:32 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-15 20:32 DEBUG  WindowsBackend: windows_language_code=1033
05-15 20:32 DEBUG  WindowsBackend: windows_language=English
05-15 20:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-15 20:32 DEBUG  WindowsBackend: bootloader=vista
05-15 20:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26596.3125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(C: hd 26596.3125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-15 20:32 DEBUG  WindowsBackend: uninstaller_path=None
05-15 20:32 DEBUG  WindowsBackend: previous_target_dir=None
05-15 20:32 DEBUG  WindowsBackend: previous_distro_name=None
05-15 20:32 DEBUG  WindowsBackend: keyboard_id=67699721
05-15 20:32 DEBUG  WindowsBackend: keyboard_layout=us
05-15 20:32 DEBUG  WindowsBackend: keyboard_variant=
05-15 20:32 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-15 20:32 DEBUG  CommonBackend: Searching ISOs on USB devices
05-15 20:32 DEBUG  CommonBackend: Searching for local CDs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-15 20:32 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-15 20:32 INFO   root: Running the installer...
05-15 20:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\translations, languages=['en_US', 'en']
05-15 20:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl9D2.tmp\translations, languages=['en_US', 'en']
05-15 20:32 INFO   WindowsFrontend: Operation cancelled
05-15 20:32 DEBUG  WindowsFrontend: frontend.quit
05-15 20:32 DEBUG  WindowsFrontend: frontend.on_quit
05-15 20:32 DEBUG  root: application.on_quit
05-15 20:32 INFO   root: sys.exit
05-16 00:29 INFO   root: === wubi 11.04 rev211 ===
05-16 00:29 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-16 00:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Operating Systems\\wubi.exe"']
05-16 00:29 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\data
05-16 00:29 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\bin\7z.exe
05-16 00:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 00:29 DEBUG  CommonBackend: Fetching basic info...
05-16 00:29 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-16 00:29 DEBUG  CommonBackend: platform=win32
05-16 00:29 DEBUG  CommonBackend: osname=nt
05-16 00:29 DEBUG  CommonBackend: language=en_US
05-16 00:29 DEBUG  CommonBackend: encoding=cp1252
05-16 00:29 DEBUG  WindowsBackend: arch=amd64
05-16 00:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\data\isolist.ini
05-16 00:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 00:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 00:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 00:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 00:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 00:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 00:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 00:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 00:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 00:29 DEBUG  WindowsBackend: Fetching host info...
05-16 00:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 00:29 DEBUG  WindowsBackend: windows version=vista
05-16 00:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 00:29 DEBUG  WindowsBackend: windows_sp=None
05-16 00:29 DEBUG  WindowsBackend: windows_build=7600
05-16 00:29 DEBUG  WindowsBackend: gmt=5
05-16 00:29 DEBUG  WindowsBackend: country=US
05-16 00:29 DEBUG  WindowsBackend: timezone=America/New_York
05-16 00:29 DEBUG  WindowsBackend: windows_username=Amit
05-16 00:29 DEBUG  WindowsBackend: user_full_name=Amit
05-16 00:29 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-16 00:29 DEBUG  WindowsBackend: windows_language_code=1033
05-16 00:29 DEBUG  WindowsBackend: windows_language=English
05-16 00:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-16 00:29 DEBUG  WindowsBackend: bootloader=vista
05-16 00:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26581.78125 mb free ntfs)
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(C: hd 26581.78125 mb free ntfs)
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-16 00:29 DEBUG  WindowsBackend: uninstaller_path=None
05-16 00:29 DEBUG  WindowsBackend: previous_target_dir=None
05-16 00:29 DEBUG  WindowsBackend: previous_distro_name=None
05-16 00:29 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 00:29 DEBUG  WindowsBackend: keyboard_layout=us
05-16 00:29 DEBUG  WindowsBackend: keyboard_variant=
05-16 00:29 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 00:29 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 00:29 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-16 00:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 00:29 DEBUG  CommonBackend: Searching for local CDs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 00:29 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:29 INFO   root: Running the installer...
05-16 00:29 DEBUG  WindowsFrontend: __init__...
05-16 00:29 DEBUG  WindowsFrontend: on_init...
05-16 00:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\translations, languages=['en_US', 'en']
05-16 00:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\translations, languages=['en_US', 'en']
05-16 00:30 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=amit
05-16 00:30 INFO   root: Received settings
05-16 00:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\translations, languages=['en_US', 'en']
05-16 00:30 DEBUG  TaskList: # Running tasklist...
05-16 00:30 DEBUG  TaskList: ## Running select_target_dir...
05-16 00:30 INFO   WindowsBackend: Installing into C:\ubuntu
05-16 00:30 DEBUG  TaskList: ## Finished select_target_dir
05-16 00:30 DEBUG  TaskList: ## Running create_dir_structure...
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-16 00:30 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-16 00:30 DEBUG  TaskList: ## Finished create_dir_structure
05-16 00:30 DEBUG  TaskList: ## Running uncompress_target_dir...
05-16 00:30 DEBUG  TaskList: ## Finished uncompress_target_dir
05-16 00:30 DEBUG  TaskList: ## Running create_uninstaller...
05-16 00:30 DEBUG  WindowsBackend: Copying uninstaller D:\Operating Systems\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-16 00:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-16 00:30 DEBUG  TaskList: ## Finished create_uninstaller
05-16 00:30 DEBUG  TaskList: ## Running copy_installation_files...
05-16 00:30 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-16 00:30 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\winboot -> C:\ubuntu\winboot
05-16 00:30 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-16 00:30 DEBUG  TaskList: ## Finished copy_installation_files
05-16 00:30 DEBUG  TaskList: ## Running get_iso...
05-16 00:30 DEBUG  CommonBackend: Searching for local CD
05-16 00:30 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl4956.tmp\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 00:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 00:30 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 00:30 DEBUG  CommonBackend: Searching for local ISO
05-16 00:30 DEBUG  Distro:   checking Ubuntu ISO D:\Operating Systems\ubuntu-10.10-desktop-i386.iso
05-16 00:30 DEBUG  Distro:     does not contain casper\filesystem.squashfs
05-16 00:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-16 00:30 DEBUG  TaskList: New task get_metalink
05-16 00:30 DEBUG  TaskList: ### Running get_metalink...
05-16 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-16 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-16 00:30 DEBUG  downloader: download finished (read 28363 bytes)
05-16 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-16 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-16 00:30 DEBUG  downloader: download finished (read 874 bytes)
05-16 00:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-16 00:30 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-16 00:30 DEBUG  downloader: download finished (read 198 bytes)
05-16 00:30 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-16 00:30 INFO   saplog: Checking block bindings..
05-16 00:30 INFO   saplog: Key verified successfully.
05-16 00:30 DEBUG  CommonBackend: metalink md5sums:
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

05-16 00:30 DEBUG  TaskList: ### Finished get_metalink
05-16 00:30 DEBUG  TaskList: New task download
05-16 00:30 DEBUG  TaskList: ### Running download...
05-16 00:30 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-16 01:30 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-16 01:30 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-16 01:30 DEBUG  TaskList: ### Finished download
05-16 01:30 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-16 01:30 DEBUG  TaskList: # Cancelling tasklist
05-16 01:30 DEBUG  TaskList: # Finished tasklist
05-16 01:30 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-16 05:27 INFO   root: === wubi 11.04 rev211 ===
05-16 05:27 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-16 05:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Operating Systems\\wubi.exe"']
05-16 05:27 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\data
05-16 05:27 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\bin\7z.exe
05-16 05:27 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 05:27 DEBUG  CommonBackend: Fetching basic info...
05-16 05:27 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-16 05:27 DEBUG  CommonBackend: platform=win32
05-16 05:27 DEBUG  CommonBackend: osname=nt
05-16 05:27 DEBUG  CommonBackend: language=en_US
05-16 05:27 DEBUG  CommonBackend: encoding=cp1252
05-16 05:27 DEBUG  WindowsBackend: arch=amd64
05-16 05:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\data\isolist.ini
05-16 05:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 05:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 05:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 05:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 05:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 05:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 05:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 05:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 05:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 05:27 DEBUG  WindowsBackend: Fetching host info...
05-16 05:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 05:27 DEBUG  WindowsBackend: windows version=vista
05-16 05:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 05:27 DEBUG  WindowsBackend: windows_sp=None
05-16 05:27 DEBUG  WindowsBackend: windows_build=7600
05-16 05:27 DEBUG  WindowsBackend: gmt=5
05-16 05:27 DEBUG  WindowsBackend: country=US
05-16 05:27 DEBUG  WindowsBackend: timezone=America/New_York
05-16 05:27 DEBUG  WindowsBackend: windows_username=Amit
05-16 05:27 DEBUG  WindowsBackend: user_full_name=Amit
05-16 05:27 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-16 05:27 DEBUG  WindowsBackend: windows_language_code=1033
05-16 05:27 DEBUG  WindowsBackend: windows_language=English
05-16 05:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-16 05:27 DEBUG  WindowsBackend: bootloader=vista
05-16 05:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26506.90625 mb free ntfs)
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(C: hd 26506.90625 mb free ntfs)
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-16 05:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 05:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 05:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 05:27 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 05:27 DEBUG  WindowsBackend: keyboard_layout=us
05-16 05:27 DEBUG  WindowsBackend: keyboard_variant=
05-16 05:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 05:27 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 05:27 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-16 05:27 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 05:27 DEBUG  CommonBackend: Searching for local CDs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 05:27 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 05:27 INFO   root: Already installed, running the uninstaller...
05-16 05:27 INFO   root: Running the uninstaller...
05-16 05:27 INFO   CommonBackend: This is the uninstaller running
05-16 05:27 DEBUG  WindowsFrontend: __init__...
05-16 05:27 DEBUG  WindowsFrontend: on_init...
05-16 05:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl27D7.tmp\translations, languages=['en_US', 'en']
05-16 05:27 INFO   WindowsFrontend: Operation cancelled
05-16 05:27 DEBUG  WindowsFrontend: frontend.quit
05-16 05:27 DEBUG  WindowsFrontend: frontend.on_quit
05-16 05:27 DEBUG  root: application.on_quit
05-16 05:27 INFO   root: sys.exit
05-16 06:03 INFO   root: === wubi 11.04 rev211 ===
05-16 06:03 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-16 06:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-16 06:03 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\data
05-16 06:03 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\bin\7z.exe
05-16 06:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 06:03 DEBUG  CommonBackend: Fetching basic info...
05-16 06:03 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-16 06:03 DEBUG  CommonBackend: platform=win32
05-16 06:03 DEBUG  CommonBackend: osname=nt
05-16 06:03 DEBUG  CommonBackend: language=en_US
05-16 06:03 DEBUG  CommonBackend: encoding=cp1252
05-16 06:03 DEBUG  WindowsBackend: arch=amd64
05-16 06:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\data\isolist.ini
05-16 06:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 06:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 06:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 06:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 06:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 06:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 06:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 06:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 06:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 06:03 DEBUG  WindowsBackend: Fetching host info...
05-16 06:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 06:03 DEBUG  WindowsBackend: windows version=vista
05-16 06:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 06:03 DEBUG  WindowsBackend: windows_sp=None
05-16 06:03 DEBUG  WindowsBackend: windows_build=7600
05-16 06:03 DEBUG  WindowsBackend: gmt=5
05-16 06:03 DEBUG  WindowsBackend: country=US
05-16 06:03 DEBUG  WindowsBackend: timezone=America/New_York
05-16 06:03 DEBUG  WindowsBackend: windows_username=Amit
05-16 06:03 DEBUG  WindowsBackend: user_full_name=Amit
05-16 06:03 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-16 06:03 DEBUG  WindowsBackend: windows_language_code=1033
05-16 06:03 DEBUG  WindowsBackend: windows_language=English
05-16 06:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-16 06:03 DEBUG  WindowsBackend: bootloader=vista
05-16 06:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26505.0664063 mb free ntfs)
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(C: hd 26505.0664063 mb free ntfs)
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-16 06:03 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 06:03 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 06:03 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 06:03 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 06:03 DEBUG  WindowsBackend: keyboard_layout=us
05-16 06:03 DEBUG  WindowsBackend: keyboard_variant=
05-16 06:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 06:03 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 06:03 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-16 06:03 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 06:03 DEBUG  CommonBackend: Searching for local CDs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 06:03 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:03 INFO   root: Running the uninstaller...
05-16 06:03 INFO   CommonBackend: This is the uninstaller running
05-16 06:03 DEBUG  WindowsFrontend: __init__...
05-16 06:03 DEBUG  WindowsFrontend: on_init...
05-16 06:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\translations, languages=['en_US', 'en']
05-16 06:03 INFO   root: Received settings
05-16 06:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\translations, languages=['en_US', 'en']
05-16 06:03 DEBUG  TaskList: # Running tasklist...
05-16 06:03 DEBUG  TaskList: ## Running Backup ISO...
05-16 06:03 DEBUG  TaskList: ## Finished Backup ISO
05-16 06:03 DEBUG  TaskList: ## Running Remove bootloader entry...
05-16 06:03 DEBUG  WindowsBackend: Could not find bcd id
05-16 06:03 DEBUG  WindowsBackend: undo_bootini C:
05-16 06:03 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 26505.0664063 mb free ntfs)
05-16 06:03 DEBUG  WindowsBackend: undo_bootini D:
05-16 06:03 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 27195.2578125 mb free ntfs)
05-16 06:03 DEBUG  TaskList: ## Finished Remove bootloader entry
05-16 06:03 DEBUG  TaskList: ## Running Remove target dir...
05-16 06:03 DEBUG  CommonBackend: Deleting C:\ubuntu
05-16 06:03 DEBUG  TaskList: ## Finished Remove target dir
05-16 06:03 DEBUG  TaskList: ## Running Remove registry key...
05-16 06:03 DEBUG  TaskList: ## Finished Remove registry key
05-16 06:03 DEBUG  TaskList: # Finished tasklist
05-16 06:03 INFO   root: Almost finished uninstalling
05-16 06:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylCE94.tmp\translations, languages=['en_US', 'en']
05-16 06:04 INFO   root: Finished uninstallation
05-16 06:04 DEBUG  root: application.quit
05-16 06:04 DEBUG  WindowsFrontend: frontend.quit
05-16 06:04 DEBUG  WindowsFrontend: frontend.on_quit
05-16 06:04 DEBUG  root: application.on_quit
05-16 06:04 INFO   root: sys.exit
05-16 06:07 INFO   root: === wubi 11.04 rev211 ===
05-16 06:07 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-16 06:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\Operating Systems\\wubi.exe"']
05-16 06:07 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\data
05-16 06:07 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\bin\7z.exe
05-16 06:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 06:07 DEBUG  CommonBackend: Fetching basic info...
05-16 06:07 DEBUG  CommonBackend: original_exe=D:\Operating Systems\wubi.exe
05-16 06:07 DEBUG  CommonBackend: platform=win32
05-16 06:07 DEBUG  CommonBackend: osname=nt
05-16 06:07 DEBUG  CommonBackend: language=en_US
05-16 06:07 DEBUG  CommonBackend: encoding=cp1252
05-16 06:07 DEBUG  WindowsBackend: arch=amd64
05-16 06:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\data\isolist.ini
05-16 06:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 06:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 06:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 06:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 06:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 06:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 06:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 06:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 06:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 06:07 DEBUG  WindowsBackend: Fetching host info...
05-16 06:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 06:07 DEBUG  WindowsBackend: windows version=vista
05-16 06:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 06:07 DEBUG  WindowsBackend: windows_sp=None
05-16 06:07 DEBUG  WindowsBackend: windows_build=7600
05-16 06:07 DEBUG  WindowsBackend: gmt=5
05-16 06:07 DEBUG  WindowsBackend: country=US
05-16 06:07 DEBUG  WindowsBackend: timezone=America/New_York
05-16 06:07 DEBUG  WindowsBackend: windows_username=Amit
05-16 06:07 DEBUG  WindowsBackend: user_full_name=Amit
05-16 06:07 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-16 06:07 DEBUG  WindowsBackend: windows_language_code=1033
05-16 06:07 DEBUG  WindowsBackend: windows_language=English
05-16 06:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-16 06:07 DEBUG  WindowsBackend: bootloader=vista
05-16 06:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26580.90625 mb free ntfs)
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(C: hd 26580.90625 mb free ntfs)
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-16 06:07 DEBUG  WindowsBackend: uninstaller_path=None
05-16 06:07 DEBUG  WindowsBackend: previous_target_dir=None
05-16 06:07 DEBUG  WindowsBackend: previous_distro_name=None
05-16 06:07 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 06:07 DEBUG  WindowsBackend: keyboard_layout=us
05-16 06:07 DEBUG  WindowsBackend: keyboard_variant=
05-16 06:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 06:07 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 06:07 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-16 06:07 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 06:07 DEBUG  CommonBackend: Searching for local CDs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 06:07 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:07 INFO   root: Running the installer...
05-16 06:07 DEBUG  WindowsFrontend: __init__...
05-16 06:07 DEBUG  WindowsFrontend: on_init...
05-16 06:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\translations, languages=['en_US', 'en']
05-16 06:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\translations, languages=['en_US', 'en']
05-16 06:09 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=amit
05-16 06:09 INFO   root: Received settings
05-16 06:09 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\translations, languages=['en_US', 'en']
05-16 06:09 DEBUG  TaskList: # Running tasklist...
05-16 06:09 DEBUG  TaskList: ## Running select_target_dir...
05-16 06:09 INFO   WindowsBackend: Installing into C:\ubuntu
05-16 06:09 DEBUG  TaskList: ## Finished select_target_dir
05-16 06:09 DEBUG  TaskList: ## Running create_dir_structure...
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-16 06:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-16 06:09 DEBUG  TaskList: ## Finished create_dir_structure
05-16 06:09 DEBUG  TaskList: ## Running uncompress_target_dir...
05-16 06:09 DEBUG  TaskList: ## Finished uncompress_target_dir
05-16 06:09 DEBUG  TaskList: ## Running create_uninstaller...
05-16 06:09 DEBUG  WindowsBackend: Copying uninstaller D:\Operating Systems\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.04-rev211
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-16 06:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-16 06:09 DEBUG  TaskList: ## Finished create_uninstaller
05-16 06:09 DEBUG  TaskList: ## Running copy_installation_files...
05-16 06:09 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
05-16 06:09 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\winboot -> C:\ubuntu\winboot
05-16 06:09 DEBUG  WindowsBackend: Copying C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
05-16 06:09 DEBUG  TaskList: ## Finished copy_installation_files
05-16 06:09 DEBUG  TaskList: ## Running get_iso...
05-16 06:09 DEBUG  CommonBackend: Searching for local CD
05-16 06:09 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pyl7686.tmp\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 06:09 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 06:09 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 06:09 DEBUG  CommonBackend: Searching for local ISO
05-16 06:09 DEBUG  Distro:   checking Ubuntu ISO D:\Operating Systems\ubuntu-10.10-desktop-i386.iso
05-16 06:09 DEBUG  Distro:     does not contain casper\filesystem.squashfs
05-16 06:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-16 06:09 DEBUG  TaskList: New task get_metalink
05-16 06:09 DEBUG  TaskList: ### Running get_metalink...
05-16 06:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink) > C:\ubuntu\install
05-16 06:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\ubuntu-11.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.metalink, basename=ubuntu-11.04-desktop-amd64.metalink, length=28363, text=None
05-16 06:09 DEBUG  downloader: download finished (read 28363 bytes)
05-16 06:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink](http://releases.ubuntu.com/11.04/MD5SUMS-metalink) > C:\ubuntu\install
05-16 06:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=874, text=None
05-16 06:09 DEBUG  downloader: download finished (read 874 bytes)
05-16 06:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg) > C:\ubuntu\install
05-16 06:09 DEBUG  downloader: Download start filename=C:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/11.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-16 06:09 DEBUG  downloader: download finished (read 198 bytes)
05-16 06:09 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-16 06:09 INFO   saplog: Checking block bindings..
05-16 06:09 INFO   saplog: Key verified successfully.
05-16 06:09 DEBUG  CommonBackend: metalink md5sums:
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

05-16 06:09 DEBUG  TaskList: ### Finished get_metalink
05-16 06:09 DEBUG  TaskList: New task download
05-16 06:09 DEBUG  TaskList: ### Running download...
05-16 06:09 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/11.04/ubuntu-11.04-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-11.04-desktop-amd64.iso
05-16 07:09 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


05-16 07:09 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
05-16 07:09 DEBUG  TaskList: ### Finished download
05-16 07:09 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-16 07:09 DEBUG  TaskList: # Cancelling tasklist
05-16 07:09 DEBUG  TaskList: # Finished tasklist
05-16 07:09 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\application.py", line 131, in select_task
  File "\lib\wubi\application.py", line 157, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 347, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-11.04-desktop-amd64.iso'
05-16 08:38 INFO   root: === wubi 11.04 rev211 ===
05-16 08:38 DEBUG  root: Logfile is c:\users\amit\appdata\local\temp\wubi-11.04-rev211.log
05-16 08:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-16 08:38 DEBUG  CommonBackend: data_dir=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\data
05-16 08:38 DEBUG  WindowsBackend: 7z=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\bin\7z.exe
05-16 08:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-16 08:38 DEBUG  CommonBackend: Fetching basic info...
05-16 08:38 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-16 08:38 DEBUG  CommonBackend: platform=win32
05-16 08:38 DEBUG  CommonBackend: osname=nt
05-16 08:38 DEBUG  CommonBackend: language=en_US
05-16 08:38 DEBUG  CommonBackend: encoding=cp1252
05-16 08:38 DEBUG  WindowsBackend: arch=amd64
05-16 08:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\data\isolist.ini
05-16 08:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-16 08:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-16 08:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-16 08:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-16 08:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-16 08:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-16 08:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-16 08:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-16 08:38 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
05-16 08:38 DEBUG  WindowsBackend: Fetching host info...
05-16 08:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-16 08:38 DEBUG  WindowsBackend: windows version=vista
05-16 08:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
05-16 08:38 DEBUG  WindowsBackend: windows_sp=None
05-16 08:38 DEBUG  WindowsBackend: windows_build=7600
05-16 08:38 DEBUG  WindowsBackend: gmt=5
05-16 08:38 DEBUG  WindowsBackend: country=US
05-16 08:38 DEBUG  WindowsBackend: timezone=America/New_York
05-16 08:38 DEBUG  WindowsBackend: windows_username=Amit
05-16 08:38 DEBUG  WindowsBackend: user_full_name=Amit
05-16 08:38 DEBUG  WindowsBackend: user_directory=C:\Users\Amit
05-16 08:38 DEBUG  WindowsBackend: windows_language_code=1033
05-16 08:38 DEBUG  WindowsBackend: windows_language=English
05-16 08:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
05-16 08:38 DEBUG  WindowsBackend: bootloader=vista
05-16 08:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 26500.0429688 mb free ntfs)
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(C: hd 26500.0429688 mb free ntfs)
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(D: hd 27195.2578125 mb free ntfs)
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
05-16 08:38 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-16 08:38 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-16 08:38 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-16 08:38 DEBUG  WindowsBackend: keyboard_id=67699721
05-16 08:38 DEBUG  WindowsBackend: keyboard_layout=us
05-16 08:38 DEBUG  WindowsBackend: keyboard_variant=
05-16 08:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-16 08:38 DEBUG  CommonBackend: locale=en_US.UTF-8
05-16 08:38 DEBUG  WindowsBackend: total_memory_mb=2045.4921875
05-16 08:38 DEBUG  CommonBackend: Searching ISOs on USB devices
05-16 08:38 DEBUG  CommonBackend: Searching for local CDs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
05-16 08:38 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
05-16 08:38 INFO   root: Running the uninstaller...
05-16 08:38 INFO   CommonBackend: This is the uninstaller running
05-16 08:38 DEBUG  WindowsFrontend: __init__...
05-16 08:38 DEBUG  WindowsFrontend: on_init...
05-16 08:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\translations, languages=['en_US', 'en']
05-16 08:38 INFO   root: Received settings
05-16 08:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\translations, languages=['en_US', 'en']
05-16 08:38 DEBUG  TaskList: # Running tasklist...
05-16 08:38 DEBUG  TaskList: ## Running Backup ISO...
05-16 08:38 DEBUG  TaskList: ## Finished Backup ISO
05-16 08:38 DEBUG  TaskList: ## Running Remove bootloader entry...
05-16 08:38 DEBUG  WindowsBackend: Could not find bcd id
05-16 08:38 DEBUG  WindowsBackend: undo_bootini C:
05-16 08:38 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 26500.0429688 mb free ntfs)
05-16 08:38 DEBUG  WindowsBackend: undo_bootini D:
05-16 08:38 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 27195.2578125 mb free ntfs)
05-16 08:38 DEBUG  TaskList: ## Finished Remove bootloader entry
05-16 08:38 DEBUG  TaskList: ## Running Remove target dir...
05-16 08:38 DEBUG  CommonBackend: Deleting C:\ubuntu
05-16 08:38 DEBUG  TaskList: ## Finished Remove target dir
05-16 08:38 DEBUG  TaskList: ## Running Remove registry key...
05-16 08:38 DEBUG  TaskList: ## Finished Remove registry key
05-16 08:38 DEBUG  TaskList: # Finished tasklist
05-16 08:38 INFO   root: Almost finished uninstalling
05-16 08:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Amit\AppData\Local\Temp\pylC66C.tmp\translations, languages=['en_US', 'en']
05-16 08:38 INFO   root: Finished uninstallation
05-16 08:38 DEBUG  root: application.quit
05-16 08:38 DEBUG  WindowsFrontend: frontend.quit
05-16 08:38 DEBUG  WindowsFrontend: frontend.on_quit
05-16 08:38 DEBUG  root: application.on_quit
05-16 08:38 INFO   root: sys.exit

---

### Post by bcbc on 2011-05-16
The bittorrent client Wubi uses is failing to connect. You need to allow pyrun.exe access to your windows firewall. If you did that and it's still not working (you may be blocked by another firewall or service provider) then download the CD iso yourself and place it in the same folder as wubi.exe before running, or burn to a CD and run from there.

See [https://wiki.ubuntu.com/WubiGuide#Installation](https://wiki.ubuntu.com/WubiGuide#Installation)

---

### Post by amit.neo2000 on 2011-05-16
thanks it worked...!!!

---

