---
title: "Installing Kubuntu : could not retrieve the required installation files"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by zoey2 on 2014-05-22
I tried installing kubuntu using various versions of wubi (13.04,13.10,14.04) but all of them give the same error after 4 hours of installation : "could not retrieve the required installation files ".I have included the log file. Thanks in advance !

```
05-23 02:29 INFO   root: === wubi 13.10 rev284 ===
05-23 02:29 DEBUG  root: Logfile is c:\users\$wati\appdata\local\temp\wubi-13.10-rev284.log
05-23 02:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\softwares\\ubuntu-13.10-desktop-amd64\\wubi.exe"']
05-23 02:29 DEBUG  CommonBackend: data_dir=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\data
05-23 02:29 DEBUG  WindowsBackend: 7z=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\bin\7z.exe
05-23 02:29 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-23 02:29 DEBUG  CommonBackend: Fetching basic info...
05-23 02:29 DEBUG  CommonBackend: original_exe=C:\softwares\ubuntu-13.10-desktop-amd64\wubi.exe
05-23 02:29 DEBUG  CommonBackend: platform=win32
05-23 02:29 DEBUG  CommonBackend: osname=nt
05-23 02:29 DEBUG  CommonBackend: language=en_IN
05-23 02:29 DEBUG  CommonBackend: encoding=cp1252
05-23 02:29 DEBUG  WindowsBackend: arch=amd64
05-23 02:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\data\isolist.ini
05-23 02:29 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-23 02:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-23 02:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-amd64
05-23 02:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-23 02:29 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-23 02:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Ubuntu Studio-i386
05-23 02:29 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-23 02:29 DEBUG  WindowsBackend: Fetching host info...
05-23 02:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-23 02:29 DEBUG  WindowsBackend: windows version=vista
05-23 02:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
05-23 02:29 DEBUG  WindowsBackend: windows_sp=None
05-23 02:29 DEBUG  WindowsBackend: windows_build=7601
05-23 02:29 DEBUG  WindowsBackend: gmt=5
05-23 02:29 DEBUG  WindowsBackend: country=IN
05-23 02:29 DEBUG  WindowsBackend: timezone=Asia/Calcutta
05-23 02:29 DEBUG  WindowsBackend: windows_username=$wati
05-23 02:29 DEBUG  WindowsBackend: user_full_name=$wati
05-23 02:29 DEBUG  WindowsBackend: user_directory=C:\Users\$wati
05-23 02:29 DEBUG  WindowsBackend: windows_language_code=1033
05-23 02:29 DEBUG  WindowsBackend: windows_language=English
05-23 02:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2450M CPU @ 2.50GHz
05-23 02:29 DEBUG  WindowsBackend: bootloader=vista
05-23 02:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28633.3554688 mb free ntfs)
05-23 02:29 DEBUG  WindowsBackend: drive=Drive(C: hd 28633.3554688 mb free ntfs)
05-23 02:29 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
05-23 02:29 DEBUG  WindowsBackend: drive=Drive(E: hd 23617.2304688 mb free ntfs)
05-23 02:29 DEBUG  WindowsBackend: drive=Drive(F: hd 81.4404296875 mb free fat32)
05-23 02:29 DEBUG  WindowsBackend: drive=Drive(G: hd 61348.3710938 mb free ntfs)
05-23 02:29 DEBUG  WindowsBackend: uninstaller_path=None
05-23 02:29 DEBUG  WindowsBackend: previous_target_dir=None
05-23 02:29 DEBUG  WindowsBackend: previous_distro_name=None
05-23 02:29 DEBUG  WindowsBackend: keyboard_id=-256884727
05-23 02:29 DEBUG  WindowsBackend: keyboard_layout=us
05-23 02:29 DEBUG  WindowsBackend: keyboard_variant=
05-23 02:29 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
05-23 02:29 DEBUG  CommonBackend: locale=en_IN
05-23 02:29 DEBUG  WindowsBackend: total_memory_mb=3992.359375
05-23 02:29 DEBUG  CommonBackend: Searching ISOs on USB devices
05-23 02:29 DEBUG  CommonBackend: Searching for local CDs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Studio CD
05-23 02:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:29 INFO   root: Running the installer...
05-23 02:29 DEBUG  WindowsFrontend: __init__...
05-23 02:29 DEBUG  WindowsFrontend: on_init...
05-23 02:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\translations, languages=['en_IN', 'en']
05-23 02:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\translations, languages=['en_IN', 'en']
05-23 02:31 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=30000MB, distro_name=Kubuntu, language=en_US, locale=en_US.UTF-8, username=swati
05-23 02:31 INFO   root: Received settings
05-23 02:31 DEBUG  CommonBackend: Searching for local CD
05-23 02:31 DEBUG  Distro:   checking whether C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp is a valid Kubuntu CD
05-23 02:31 DEBUG  Distro:     does not contain C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\casper\filesystem.squashfs
05-23 02:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-23 02:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-23 02:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
05-23 02:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
05-23 02:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-23 02:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-23 02:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
05-23 02:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
05-23 02:31 DEBUG  CommonBackend: Searching for local ISO
05-23 02:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\translations, languages=['en_US', 'en']
05-23 02:31 DEBUG  TaskList: # Running tasklist...
05-23 02:31 DEBUG  TaskList: ## Running select_target_dir...
05-23 02:31 INFO   WindowsBackend: Installing into G:\ubuntu
05-23 02:31 DEBUG  TaskList: ## Finished select_target_dir
05-23 02:31 DEBUG  TaskList: ## Running create_dir_structure...
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
05-23 02:31 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
05-23 02:31 DEBUG  TaskList: ## Finished create_dir_structure
05-23 02:31 DEBUG  TaskList: ## Running uncompress_target_dir...
05-23 02:31 DEBUG  TaskList: ## Finished uncompress_target_dir
05-23 02:31 DEBUG  TaskList: ## Running create_uninstaller...
05-23 02:31 DEBUG  WindowsBackend: Copying uninstaller C:\softwares\ubuntu-13.10-desktop-amd64\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Kubuntu
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Kubuntu.ico
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 13.10-rev284
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Kubuntu
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.kubuntu.org](http://www.kubuntu.org)
05-23 02:31 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-23 02:31 DEBUG  TaskList: ## Finished create_uninstaller
05-23 02:31 DEBUG  TaskList: ## Running copy_installation_files...
05-23 02:31 DEBUG  WindowsBackend: Copying C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
05-23 02:31 DEBUG  WindowsBackend: Copying C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\winboot -> G:\ubuntu\winboot
05-23 02:31 DEBUG  WindowsBackend: Copying C:\Users\$wati\AppData\Local\Temp\pyl4C9.tmp\data\images\Kubuntu.ico -> G:\ubuntu\Kubuntu.ico
05-23 02:31 DEBUG  TaskList: ## Finished copy_installation_files
05-23 02:31 DEBUG  TaskList: ## Running get_iso...
05-23 02:31 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
05-23 02:31 DEBUG  TaskList: New task get_metalink
05-23 02:31 DEBUG  TaskList: ### Running get_metalink...
05-23 02:31 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.metalink) > G:\ubuntu\install
05-23 02:31 DEBUG  downloader: Download start filename=G:\ubuntu\install\kubuntu-13.10-desktop-amd64.metalink, url=http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.metalink, basename=kubuntu-13.10-desktop-amd64.metalink, length=1041, text=None
05-23 02:31 DEBUG  downloader: download finished (read 1041 bytes)
05-23 02:31 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink) > G:\ubuntu\install
05-23 02:31 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=141, text=None
05-23 02:31 DEBUG  downloader: download finished (read 141 bytes)
05-23 02:31 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink.gpg) > G:\ubuntu\install
05-23 02:31 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
05-23 02:31 DEBUG  downloader: download finished (read 198 bytes)
05-23 02:31 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
05-23 02:31 INFO   saplog: Checking block bindings..
05-23 02:31 INFO   saplog: Key verified successfully.
05-23 02:31 DEBUG  CommonBackend: metalink md5sums:
c74ee7937f02a3b047fdfe2e32538a8f *kubuntu-13.10-desktop-amd64.metalink
1ff011af32e9b4befc4b8d49c56584b0 *kubuntu-13.10-desktop-i386.metalink


05-23 02:31 ERROR  CommonBackend: The md5 of the metalink does match
05-23 02:31 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
None
05-23 02:31 DEBUG  TaskList: ### Finished get_metalink
05-23 02:31 DEBUG  TaskList: New task download
05-23 02:31 DEBUG  TaskList: ### Running download...
05-23 02:31 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.iso.torrent](http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.iso.torrent) > G:\ubuntu\install\kubuntu-13.10-desktop-amd64.iso
05-23 02:44 ERROR  TaskList: problem getting response info - HTTP Error -1: 
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 78, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 69, in error_callback
DownloadError: problem getting response info - HTTP Error -1: 
05-23 02:44 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error -1:  in task download
05-23 02:44 DEBUG  TaskList: ### Finished download
05-23 02:44 DEBUG  TaskList: New task download
05-23 02:44 DEBUG  TaskList: ### Running download...
05-23 02:44 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.iso) > G:\ubuntu\install\kubuntu-13.10-desktop-amd64.iso
05-23 02:44 DEBUG  downloader: Download start filename=G:\ubuntu\install\kubuntu-13.10-desktop-amd64.iso, url=http://cdimage.ubuntu.com/kubuntu/releases/13.10/release/kubuntu-13.10-desktop-amd64.iso, basename=kubuntu-13.10-desktop-amd64.iso, length=1023410176, text=None
05-23 03:00 DEBUG  TaskList: ### Finished download
05-23 03:00 DEBUG  downloader: download finished (read 1023410176 bytes)
05-23 03:00 DEBUG  TaskList: New task check_iso
05-23 03:00 DEBUG  TaskList: ### Running check_iso...
05-23 03:00 DEBUG  CommonBackend: Checking G:\ubuntu\install\kubuntu-13.10-desktop-amd64.iso
05-23 03:00 DEBUG  Distro:   checking Kubuntu ISO G:\ubuntu\install\kubuntu-13.10-desktop-amd64.iso
05-23 03:00 DEBUG  Distro:     does not contain casper\vmlinuz
05-23 03:00 DEBUG  TaskList: ### Finished check_iso
05-23 03:00 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
05-23 03:00 DEBUG  TaskList: # Cancelling tasklist
05-23 03:00 DEBUG  TaskList: # Finished tasklist
05-23 03:00 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
```

---

### Post by QIII on 2014-05-22
Hello!

There is little use in spending too much time trying to figure out what has gone wrong with a Wubi install.  It is no longer recommended even by the developers and, even though it is still included on some images, it is going to be dropped completely.

It will not work at all with a Windows 8.1 installation with UEFI.

I would recommend a dual boot or virtualization.

---

### Post by zoey2 on 2014-05-23
i am trying to install with windows 7.
i am new to ubuntu so could you please tell me how to dual boot or virtualization.?

---

### Post by SeijiSensei on 2014-05-23
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

