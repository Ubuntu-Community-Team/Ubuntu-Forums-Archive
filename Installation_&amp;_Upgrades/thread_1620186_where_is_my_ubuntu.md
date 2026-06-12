---
title: "where is my ubuntu?"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by haoweishow on 2010-11-12
1. I download the wubi.exe.

2. run it,and it downloads the ubuntu of 700MB.

3. after finished download, the window disapper(i did nothing). and i can't find what and where it downloads..

4. help me ,thanks:popcorn:

---

### Post by bcbc on 2010-11-12
Look in the log file to see what happened or post it here (within [CODE[SIZE="1"] [/SIZE]][/CODE] tags.

You can find it in the *%temp%* folder named wubi-10.04.1-rev190.log

---

### Post by haoweishow on 2010-11-12
thanks,and my os is xp,sp2 or sp3.
```

11-13 00:14 INFO   root: === wubi 10.10 rev197 ===
11-13 00:14 DEBUG  root: Logfile is f:\docume~1\&#37085;&#20255;\locals~1\temp\wubi-10.10-rev197.log
11-13 00:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\QQDownload\\wubi.exe"']
11-13 00:14 DEBUG  CommonBackend: data_dir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\data
11-13 00:14 DEBUG  WindowsBackend: 7z=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\bin\7z.exe
11-13 00:14 DEBUG  CommonBackend: Fetching basic info...
11-13 00:14 DEBUG  CommonBackend: original_exe=C:\QQDownload\wubi.exe
11-13 00:14 DEBUG  CommonBackend: platform=win32
11-13 00:14 DEBUG  CommonBackend: osname=nt
11-13 00:14 DEBUG  CommonBackend: language=zh_CN
11-13 00:14 DEBUG  CommonBackend: encoding=cp936
11-13 00:14 DEBUG  WindowsBackend: arch=amd64
11-13 00:14 DEBUG  CommonBackend: Parsing isolist=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\data\isolist.ini
11-13 00:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 00:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 00:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 00:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 00:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 00:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 00:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 00:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 00:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 00:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 00:14 DEBUG  WindowsBackend: Fetching host info...
11-13 00:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 00:14 DEBUG  WindowsBackend: windows version=xp
11-13 00:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 00:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 00:14 DEBUG  WindowsBackend: windows_build=2600
11-13 00:14 DEBUG  WindowsBackend: gmt=8
11-13 00:14 DEBUG  WindowsBackend: country=CN
11-13 00:14 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-13 00:14 DEBUG  WindowsBackend: windows_username=
11-13 00:14 DEBUG  WindowsBackend: user_full_name=
11-13 00:14 DEBUG  WindowsBackend: user_directory=F:\Documents and Settings\
11-13 00:14 DEBUG  WindowsBackend: windows_language_code=1028
11-13 00:14 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-13 00:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
11-13 00:14 DEBUG  WindowsBackend: bootloader=xp
11-13 00:14 DEBUG  WindowsBackend: system_drive=Drive(F: hd 52804.640625 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(C: hd 985.896484375 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(D: hd 50180.6367188 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(E: hd 20990.8125 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(F: hd 52804.640625 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(G: hd 3794.21875 mb free ntfs)
11-13 00:14 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
11-13 00:14 DEBUG  WindowsBackend: uninstaller_path=None
11-13 00:14 DEBUG  WindowsBackend: previous_target_dir=None
11-13 00:14 DEBUG  WindowsBackend: previous_distro_name=None
11-13 00:14 DEBUG  WindowsBackend: keyboard_id=134481924
11-13 00:14 DEBUG  WindowsBackend: keyboard_layout=us
11-13 00:14 DEBUG  WindowsBackend: keyboard_variant=
11-13 00:14 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
11-13 00:14 DEBUG  CommonBackend: locale=zh_CN.UTF-8
11-13 00:14 DEBUG  WindowsBackend: total_memory_mb=2047.23046875
11-13 00:14 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 00:14 DEBUG  CommonBackend: Searching for local CDs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 INFO   root: Running the installer...
11-13 00:14 DEBUG  WindowsFrontend: __init__...
11-13 00:14 DEBUG  WindowsFrontend: on_init...
11-13 00:14 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\translations, languages=['zh_CN', 'zh']
11-13 00:14 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\translations, languages=['zh_CN', 'zh']
11-13 00:14 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=zh_CN, locale=zh_CN.UTF-8, username=haowei
11-13 00:14 INFO   root: Received settings
11-13 00:14 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\translations, languages=['zh_CN', 'zh']
11-13 00:14 DEBUG  TaskList: # Running tasklist...
11-13 00:14 DEBUG  TaskList: ## Running select_target_dir...
11-13 00:14 INFO   WindowsBackend: Installing into D:\ubuntu
11-13 00:14 DEBUG  TaskList: ## Finished select_target_dir
11-13 00:14 DEBUG  TaskList: ## Running create_dir_structure...
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-13 00:14 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-13 00:14 DEBUG  TaskList: ## Finished create_dir_structure
11-13 00:14 DEBUG  TaskList: ## Running uncompress_target_dir...
11-13 00:14 DEBUG  TaskList: ## Finished uncompress_target_dir
11-13 00:14 DEBUG  TaskList: ## Running create_uninstaller...
11-13 00:14 DEBUG  WindowsBackend: Copying uninstaller C:\QQDownload\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-13 00:14 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-13 00:14 DEBUG  TaskList: ## Finished create_uninstaller
11-13 00:14 DEBUG  TaskList: ## Running copy_installation_files...
11-13 00:14 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-13 00:14 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\winboot -> D:\ubuntu\winboot
11-13 00:14 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-13 00:14 DEBUG  TaskList: ## Finished copy_installation_files
11-13 00:14 DEBUG  TaskList: ## Running get_iso...
11-13 00:14 DEBUG  CommonBackend: Searching for local CD
11-13 00:14 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl10D.tmp\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 00:14 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 00:14 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 00:14 DEBUG  CommonBackend: Searching for local ISO
11-13 00:14 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-13 00:14 DEBUG  TaskList: New task get_metalink
11-13 00:14 DEBUG  TaskList: ### Running get_metalink...
11-13 00:14 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > D:\ubuntu\install
11-13 00:14 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
11-13 00:14 DEBUG  downloader: download finished (read 9135 bytes)
11-13 00:14 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > D:\ubuntu\install
11-13 00:15 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
11-13 00:15 DEBUG  downloader: download finished (read 488 bytes)
11-13 00:15 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
11-13 00:15 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
11-13 00:15 DEBUG  downloader: download finished (read 198 bytes)
11-13 00:15 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-13 00:15 INFO   saplog: Checking block bindings..
11-13 00:15 INFO   saplog: Key verified successfully.
11-13 00:15 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

11-13 00:15 DEBUG  TaskList: ### Finished get_metalink
11-13 00:15 DEBUG  TaskList: New task download
11-13 00:15 DEBUG  TaskList: ### Running download...
11-13 00:15 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 01:20 DEBUG  TaskList: ### Finished download
11-13 01:20 DEBUG  TaskList: New task check_iso
11-13 01:20 DEBUG  TaskList: ### Running check_iso...
11-13 01:20 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 01:20 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 01:20 ERROR  WindowsBackend: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 464, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 54, in run_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 664, in _execute_child
  File "\lib\subprocess.py", line 492, in list2cmdline
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
11-13 01:20 ERROR  TaskList: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 275, in check_iso
  File "\lib\wubi\backends\common\distro.py", line 106, in is_valid_iso
  File "\lib\wubi\backends\win32\backend.py", line 467, in get_iso_file_names
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
11-13 01:20 DEBUG  TaskList: # Cancelling tasklist
11-13 01:20 ERROR  root: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 275, in check_iso
  File "\lib\wubi\backends\common\distro.py", line 106, in is_valid_iso
  File "\lib\wubi\backends\win32\backend.py", line 467, in get_iso_file_names
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
11-13 05:58 INFO   root: === wubi 10.10 rev197 ===
11-13 05:58 DEBUG  root: Logfile is f:\docume~1\&#37085;&#20255;\locals~1\temp\wubi-10.10-rev197.log
11-13 05:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\QQDownload\\wubi.exe"']
11-13 05:58 DEBUG  CommonBackend: data_dir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\data
11-13 05:58 DEBUG  WindowsBackend: 7z=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\bin\7z.exe
11-13 05:58 DEBUG  CommonBackend: Fetching basic info...
11-13 05:58 DEBUG  CommonBackend: original_exe=C:\QQDownload\wubi.exe
11-13 05:58 DEBUG  CommonBackend: platform=win32
11-13 05:58 DEBUG  CommonBackend: osname=nt
11-13 05:58 DEBUG  CommonBackend: language=zh_CN
11-13 05:58 DEBUG  CommonBackend: encoding=cp936
11-13 05:58 DEBUG  WindowsBackend: arch=amd64
11-13 05:58 DEBUG  CommonBackend: Parsing isolist=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
11-13 05:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 05:58 DEBUG  WindowsBackend: Fetching host info...
11-13 05:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 05:58 DEBUG  WindowsBackend: windows version=xp
11-13 05:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 05:58 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 05:58 DEBUG  WindowsBackend: windows_build=2600
11-13 05:58 DEBUG  WindowsBackend: gmt=8
11-13 05:58 DEBUG  WindowsBackend: country=CN
11-13 05:58 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-13 05:58 DEBUG  WindowsBackend: windows_username=
11-13 05:58 DEBUG  WindowsBackend: user_full_name=
11-13 05:58 DEBUG  WindowsBackend: user_directory=F:\Documents and Settings\
11-13 05:58 DEBUG  WindowsBackend: windows_language_code=1028
11-13 05:58 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-13 05:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
11-13 05:58 DEBUG  WindowsBackend: bootloader=xp
11-13 05:58 DEBUG  WindowsBackend: system_drive=Drive(F: hd 52805.4140625 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(C: hd 985.896484375 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(D: hd 50199.9609375 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(E: hd 20990.8125 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(F: hd 52805.4140625 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(G: hd 3794.21875 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
11-13 05:58 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-13 05:58 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-13 05:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-13 05:58 DEBUG  WindowsBackend: keyboard_id=134481924
11-13 05:58 DEBUG  WindowsBackend: keyboard_layout=us
11-13 05:58 DEBUG  WindowsBackend: keyboard_variant=
11-13 05:58 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
11-13 05:58 DEBUG  CommonBackend: locale=zh_CN.UTF-8
11-13 05:58 DEBUG  WindowsBackend: total_memory_mb=2047.23046875
11-13 05:58 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 05:58 DEBUG  CommonBackend: Searching for local CDs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 INFO   root: Already installed, running the uninstaller...
11-13 05:58 INFO   root: Running the uninstaller...
11-13 05:58 INFO   CommonBackend: This is the uninstaller running
11-13 05:58 DEBUG  WindowsFrontend: __init__...
11-13 05:58 DEBUG  WindowsFrontend: on_init...
11-13 05:58 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\translations, languages=['zh_CN', 'zh']
11-13 05:58 INFO   root: Received settings
11-13 05:58 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\translations, languages=['zh_CN', 'zh']
11-13 05:58 DEBUG  TaskList: # Running tasklist...
11-13 05:58 DEBUG  TaskList: ## Running &#28598;&#22246;&#21796; ISO &#37711;&#22796;&#27919;&#38336;&#28355;&#20762;&#37826;&#22246;&#27426;...
11-13 05:58 DEBUG  TaskList: ## Finished &#28598;&#22246;&#21796; ISO &#37711;&#22796;&#27919;&#38336;&#28355;&#20762;&#37826;&#22246;&#27426;
11-13 05:58 DEBUG  TaskList: ## Running &#37714;&#29371;&#27342;&#23534;&#26334;&#57841;&#26916;?..
11-13 05:58 ERROR  WindowsBackend: Cannot find bcdedit
11-13 05:58 DEBUG  WindowsBackend: undo_bootini C:
11-13 05:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 985.896484375 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: undo_bootini D:
11-13 05:58 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 50199.9609375 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: undo_bootini E:
11-13 05:58 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20990.8125 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: undo_bootini F:
11-13 05:58 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 52805.4140625 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: undo_bootini G:
11-13 05:58 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 3794.21875 mb free ntfs)
11-13 05:58 DEBUG  TaskList: ## Finished &#37714;&#29371;&#27342;&#23534;&#26334;&#57841;&#26916;?
11-13 05:58 DEBUG  TaskList: ## Running &#37714;&#29371;&#27342;&#37929;&#57789;&#29219;&#37929;&#57788;&#32141;...
11-13 05:58 DEBUG  CommonBackend: Deleting D:\ubuntu
11-13 05:58 DEBUG  TaskList: ## Finished &#37714;&#29371;&#27342;&#37929;&#57789;&#29219;&#37929;&#57788;&#32141;
11-13 05:58 DEBUG  TaskList: ## Running &#37714;&#29371;&#27342;&#23049;&#12581;&#21821;&#29723;&#12585;&#25965;&#37706;?..
11-13 05:58 DEBUG  TaskList: ## Finished &#37714;&#29371;&#27342;&#23049;&#12581;&#21821;&#29723;&#12585;&#25965;&#37706;?
11-13 05:58 DEBUG  TaskList: # Finished tasklist
11-13 05:58 INFO   root: Almost finished uninstalling
11-13 05:58 INFO   root: Finished uninstallation
11-13 05:58 DEBUG  CommonBackend: Fetching basic info...
11-13 05:58 DEBUG  CommonBackend: original_exe=C:\QQDownload\wubi.exe
11-13 05:58 DEBUG  CommonBackend: platform=win32
11-13 05:58 DEBUG  CommonBackend: osname=nt
11-13 05:58 DEBUG  WindowsBackend: arch=amd64
11-13 05:58 DEBUG  CommonBackend: Parsing isolist=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\data\isolist.ini
11-13 05:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 05:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 05:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 05:58 DEBUG  WindowsBackend: Fetching host info...
11-13 05:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 05:58 DEBUG  WindowsBackend: windows version=xp
11-13 05:58 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 05:58 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 05:58 DEBUG  WindowsBackend: windows_build=2600
11-13 05:58 DEBUG  WindowsBackend: gmt=8
11-13 05:58 DEBUG  WindowsBackend: country=CN
11-13 05:58 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-13 05:58 DEBUG  WindowsBackend: windows_username=
11-13 05:58 DEBUG  WindowsBackend: user_full_name=
11-13 05:58 DEBUG  WindowsBackend: user_directory=F:\Documents and Settings\
11-13 05:58 DEBUG  WindowsBackend: windows_language_code=1028
11-13 05:58 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-13 05:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
11-13 05:58 DEBUG  WindowsBackend: bootloader=xp
11-13 05:58 DEBUG  WindowsBackend: system_drive=Drive(F: hd 52922.9648438 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(C: hd 985.896484375 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(D: hd 50201.5664063 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(E: hd 20990.8125 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(F: hd 52922.9648438 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(G: hd 3794.21875 mb free ntfs)
11-13 05:58 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
11-13 05:58 DEBUG  WindowsBackend: uninstaller_path=None
11-13 05:58 DEBUG  WindowsBackend: previous_target_dir=None
11-13 05:58 DEBUG  WindowsBackend: previous_distro_name=None
11-13 05:58 DEBUG  WindowsBackend: keyboard_id=134481924
11-13 05:58 DEBUG  WindowsBackend: keyboard_layout=us
11-13 05:58 DEBUG  WindowsBackend: keyboard_variant=
11-13 05:58 DEBUG  WindowsBackend: total_memory_mb=2047.23046875
11-13 05:58 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 05:58 DEBUG  CommonBackend: Searching for local CDs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 05:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:58 INFO   root: Running the installer...
11-13 05:58 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\translations, languages=['zh_CN', 'zh']
11-13 05:58 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\translations, languages=['zh_CN', 'zh']
11-13 05:59 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=zh_CN, locale=zh_CN.UTF-8, username=haowei
11-13 05:59 INFO   root: Received settings
11-13 05:59 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\translations, languages=['zh_CN', 'zh']
11-13 05:59 DEBUG  TaskList: # Running tasklist...
11-13 05:59 DEBUG  TaskList: ## Running select_target_dir...
11-13 05:59 INFO   WindowsBackend: Installing into D:\ubuntu
11-13 05:59 DEBUG  TaskList: ## Finished select_target_dir
11-13 05:59 DEBUG  TaskList: ## Running create_dir_structure...
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-13 05:59 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-13 05:59 DEBUG  TaskList: ## Finished create_dir_structure
11-13 05:59 DEBUG  TaskList: ## Running uncompress_target_dir...
11-13 05:59 DEBUG  TaskList: ## Finished uncompress_target_dir
11-13 05:59 DEBUG  TaskList: ## Running create_uninstaller...
11-13 05:59 DEBUG  WindowsBackend: Copying uninstaller C:\QQDownload\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
11-13 05:59 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
11-13 05:59 DEBUG  TaskList: ## Finished create_uninstaller
11-13 05:59 DEBUG  TaskList: ## Running copy_installation_files...
11-13 05:59 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
11-13 05:59 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\winboot -> D:\ubuntu\winboot
11-13 05:59 DEBUG  WindowsBackend: Copying F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
11-13 05:59 DEBUG  TaskList: ## Finished copy_installation_files
11-13 05:59 DEBUG  TaskList: ## Running get_iso...
11-13 05:59 DEBUG  CommonBackend: Searching for local CD
11-13 05:59 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 05:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 05:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 05:59 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl3.tmp\casper\filesystem.squashfs
11-13 05:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 05:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 05:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 05:59 DEBUG  CommonBackend: Searching for local ISO
11-13 05:59 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-13 05:59 DEBUG  TaskList: New task get_metalink
11-13 05:59 DEBUG  TaskList: ### Running get_metalink...
11-13 05:59 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink > D:\ubuntu\install
11-13 05:59 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.10-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.metalink, basename=ubuntu-10.10-desktop-amd64.metalink, length=9135, text=None
11-13 05:59 DEBUG  downloader: download finished (read 9135 bytes)
11-13 05:59 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink > D:\ubuntu\install
11-13 05:59 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=488, text=None
11-13 05:59 DEBUG  downloader: download finished (read 488 bytes)
11-13 05:59 DEBUG  downloader: downloading http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg > D:\ubuntu\install
11-13 05:59 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.10/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
11-13 05:59 DEBUG  downloader: download finished (read 198 bytes)
11-13 05:59 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
11-13 05:59 INFO   saplog: Checking block bindings..
11-13 05:59 INFO   saplog: Key verified successfully.
11-13 05:59 DEBUG  CommonBackend: metalink md5sums:
8347c9445946263135e546b5b405ab53  ubuntu-10.10-alternate-amd64.metalink
fa54b4b9e6bf5eca925e6349354eaa21  ubuntu-10.10-alternate-i386.metalink
d50f0a43d72bc46f847e4b80474e9bf4  ubuntu-10.10-desktop-amd64.metalink
96710a504292b579234bcc78405f4deb  ubuntu-10.10-desktop-i386.metalink
43d96efc68bfb9d2be5fcb5d480e6436  ubuntu-10.10-netbook-i386.metalink
9bb7b8e69d37e73638309e9647d46092  ubuntu-10.10-server-amd64.metalink
ec1ffd21842e4d6447b3dfa668afb070  ubuntu-10.10-server-i386.metalink

11-13 05:59 DEBUG  TaskList: ### Finished get_metalink
11-13 05:59 DEBUG  TaskList: New task download
11-13 05:59 DEBUG  TaskList: ### Running download...
11-13 05:59 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.10/ubuntu-10.10-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 06:59 DEBUG  TaskList: ### Finished download
11-13 06:59 DEBUG  TaskList: New task check_iso
11-13 06:59 DEBUG  TaskList: ### Running check_iso...
11-13 06:59 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 06:59 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.10-desktop-amd64.iso
11-13 06:59 ERROR  WindowsBackend: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 464, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 54, in run_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 664, in _execute_child
  File "\lib\subprocess.py", line 492, in list2cmdline
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
11-13 06:59 ERROR  TaskList: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 275, in check_iso
  File "\lib\wubi\backends\common\distro.py", line 106, in is_valid_iso
  File "\lib\wubi\backends\win32\backend.py", line 467, in get_iso_file_names
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
11-13 06:59 DEBUG  TaskList: # Cancelling tasklist
11-13 06:59 ERROR  root: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 275, in check_iso
  File "\lib\wubi\backends\common\distro.py", line 106, in is_valid_iso
  File "\lib\wubi\backends\win32\backend.py", line 467, in get_iso_file_names
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)
11-13 07:00 INFO   root: === wubi 10.10 rev197 ===
11-13 07:00 DEBUG  root: Logfile is f:\docume~1\&#37085;&#20255;\locals~1\temp\wubi-10.10-rev197.log
11-13 07:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\QQDownload\\wubi.exe"']
11-13 07:00 DEBUG  CommonBackend: data_dir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\data
11-13 07:00 DEBUG  WindowsBackend: 7z=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
11-13 07:00 DEBUG  CommonBackend: Fetching basic info...
11-13 07:00 DEBUG  CommonBackend: original_exe=C:\QQDownload\wubi.exe
11-13 07:00 DEBUG  CommonBackend: platform=win32
11-13 07:00 DEBUG  CommonBackend: osname=nt
11-13 07:00 DEBUG  CommonBackend: language=zh_CN
11-13 07:00 DEBUG  CommonBackend: encoding=cp936
11-13 07:00 DEBUG  WindowsBackend: arch=amd64
11-13 07:00 DEBUG  CommonBackend: Parsing isolist=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
11-13 07:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-13 07:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-13 07:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-13 07:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-13 07:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-13 07:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-13 07:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-13 07:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-13 07:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-13 07:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-13 07:00 DEBUG  WindowsBackend: Fetching host info...
11-13 07:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-13 07:00 DEBUG  WindowsBackend: windows version=xp
11-13 07:00 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-13 07:00 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-13 07:00 DEBUG  WindowsBackend: windows_build=2600
11-13 07:00 DEBUG  WindowsBackend: gmt=8
11-13 07:00 DEBUG  WindowsBackend: country=CN
11-13 07:00 DEBUG  WindowsBackend: timezone=Asia/Shanghai
11-13 07:00 DEBUG  WindowsBackend: windows_username=
11-13 07:00 DEBUG  WindowsBackend: user_full_name=
11-13 07:00 DEBUG  WindowsBackend: user_directory=F:\Documents and Settings\
11-13 07:00 DEBUG  WindowsBackend: windows_language_code=1028
11-13 07:00 DEBUG  WindowsBackend: windows_language=Chinese (Traditional)
11-13 07:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T6670  @ 2.20GHz
11-13 07:00 DEBUG  WindowsBackend: bootloader=xp
11-13 07:00 DEBUG  WindowsBackend: system_drive=Drive(F: hd 52810.1523438 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(C: hd 985.896484375 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(D: hd 50197.671875 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(E: hd 20990.8125 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(F: hd 52810.1523438 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(G: hd 3794.21875 mb free ntfs)
11-13 07:00 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
11-13 07:00 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
11-13 07:00 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
11-13 07:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-13 07:00 DEBUG  WindowsBackend: keyboard_id=134481924
11-13 07:00 DEBUG  WindowsBackend: keyboard_layout=us
11-13 07:00 DEBUG  WindowsBackend: keyboard_variant=
11-13 07:00 DEBUG  CommonBackend: python locale=('zh_CN', 'cp936')
11-13 07:00 DEBUG  CommonBackend: locale=zh_CN.UTF-8
11-13 07:00 DEBUG  WindowsBackend: total_memory_mb=2047.23046875
11-13 07:00 DEBUG  CommonBackend: Searching ISOs on USB devices
11-13 07:00 DEBUG  CommonBackend: Searching for local CDs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether C:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain C:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
11-13 07:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
11-13 07:00 INFO   root: Already installed, running the uninstaller...
11-13 07:00 INFO   root: Running the uninstaller...
11-13 07:00 INFO   CommonBackend: This is the uninstaller running
11-13 07:00 DEBUG  WindowsFrontend: __init__...
11-13 07:00 DEBUG  WindowsFrontend: on_init...
11-13 07:00 INFO   WinuiPage: appname=wubi, localedir=F:\DOCUME~1\&#37085;&#20255;\LOCALS~1\Temp\pyl18.tmp\translations, languages=['zh_CN', 'zh']
11-13 07:00 INFO   WindowsFrontend: Operation cancelled
11-13 07:00 DEBUG  WindowsFrontend: frontend.quit
11-13 07:00 DEBUG  WindowsFrontend: frontend.on_quit
11-13 07:00 DEBUG  root: application.on_quit
11-13 07:00 INFO   root: sys.exit


```

---

### Post by Frogs Hair on 2010-11-12
Something went wrong with your download . A dialog box will appear and   Wubi will ask to restart the computer after the download completes. You may have to start over.

---

### Post by bcbc on 2010-11-12
It's complaining - probably about your user name not being ascii. I saw a similar problem mentioned here: [http://art.ubuntuforums.org/showthread.php?p=7309290](http://art.ubuntuforums.org/showthread.php?p=7309290)

It seems this problem existed previously and was fixed [https://bugs.launchpad.net/wubi/+bug/365648](https://bugs.launchpad.net/wubi/+bug/365648) - maybe this is a regression or the bug was never properly fixed.

```
11-13 01:20 ERROR  WindowsBackend: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 464, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 54, in run_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 664, in _execute_child
  File "\lib\subprocess.py", line 492, in list2cmdline
UnicodeDecodeError: 'ascii' codec can't decode byte 0xba in position 0: ordinal not in range(128)
11-13 01:20 ERROR  TaskList: 'ascii' codec can't decode byte 0xba in position 12: ordinal not in range(128)

```

---

### Post by haoweishow on 2010-11-12
> **Frogs Hair said:**
> Something went wrong with your download . A dialog box will appear and   Wubi will ask to restart the computer after the download completes. You may have to start over.

no any dialog appear,the wubi.exe finished download, and disappear immediately.

and then i try to find where the ubuntu is stored,but failed.

---

### Post by Frogs Hair on 2010-11-12
> **haoweishow said:**
> no any dialog appear,the wubi.exe finished download, and disappear immediately.

and then i try to find where the ubuntu is stored,but failed.

If you have to start over and have the option  , download the ISO and then you have the option of running from the disc dual booting or using Wubi from the disc.

---

