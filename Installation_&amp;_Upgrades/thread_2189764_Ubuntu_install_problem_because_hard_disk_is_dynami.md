---
title: "Ubuntu install problem because hard disk is dynamic"
date: 2013-11-23
forum: Installation &amp; Upgrades
---

### Post by schittia on 2013-11-23
Hi all,
I tried to install ubuntu on my hardisk(windows 7) but the options are too confusing(new/sda1,2,3,4) so i skipped and tried to install it using wubi but after an hour of extraction and installation it shows an error. I've installed wubi long time ago , it worked fine and i uninstalled, it worked fine then. In the process of installing I lost my recovery image file. I tried to install linux mint but afraid it too will be a flop. This is the error i get after the whole process.
>>stderr = An error has occurred setting element data.The request is not supported. This is the log file info:
```
11-23 20:35 INFO   root: === wubi 12.04.1 rev273 ===11-23 20:35 DEBUG  root: Logfile is c:\users\sanjeev\appdata\local\temp\wubi-12.04.1-rev273.log
11-23 20:35 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
11-23 20:35 DEBUG  CommonBackend: data_dir=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\data
11-23 20:35 DEBUG  WindowsBackend: 7z=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\bin\7z.exe
11-23 20:35 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-23 20:35 DEBUG  CommonBackend: Fetching basic info...
11-23 20:35 DEBUG  CommonBackend: original_exe=F:\wubi.exe
11-23 20:35 DEBUG  CommonBackend: platform=win32
11-23 20:35 DEBUG  CommonBackend: osname=nt
11-23 20:35 DEBUG  CommonBackend: language=en_US
11-23 20:35 DEBUG  CommonBackend: encoding=cp1252
11-23 20:35 DEBUG  WindowsBackend: arch=amd64
11-23 20:35 DEBUG  CommonBackend: Parsing isolist=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\data\isolist.ini
11-23 20:35 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-23 20:35 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-23 20:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-23 20:35 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-23 20:35 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-23 20:35 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-23 20:35 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-23 20:35 DEBUG  WindowsBackend: Fetching host info...
11-23 20:35 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-23 20:35 DEBUG  WindowsBackend: windows version=vista
11-23 20:35 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-23 20:35 DEBUG  WindowsBackend: windows_sp=None
11-23 20:35 DEBUG  WindowsBackend: windows_build=7601
11-23 20:35 DEBUG  WindowsBackend: gmt=-7
11-23 20:35 DEBUG  WindowsBackend: country=US
11-23 20:35 DEBUG  WindowsBackend: timezone=America/Denver
11-23 20:35 DEBUG  WindowsBackend: windows_username=SANJEEV
11-23 20:35 DEBUG  WindowsBackend: user_full_name=SANJEEV
11-23 20:35 DEBUG  WindowsBackend: user_directory=C:\Users\SANJEEV
11-23 20:35 DEBUG  WindowsBackend: windows_language_code=1033
11-23 20:35 DEBUG  WindowsBackend: windows_language=English
11-23 20:35 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
11-23 20:35 DEBUG  WindowsBackend: bootloader=vista
11-23 20:35 DEBUG  WindowsBackend: system_drive=Drive(C: hd 307929.003906 mb free ntfs)
11-23 20:35 DEBUG  WindowsBackend: drive=Drive(C: hd 307929.003906 mb free ntfs)
11-23 20:35 DEBUG  WindowsBackend: drive=Drive(D: hd 14717.7929688 mb free ntfs)
11-23 20:35 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
11-23 20:35 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
11-23 20:35 DEBUG  WindowsBackend: drive=Drive(G: hd 107361.773438 mb free ntfs)
11-23 20:35 DEBUG  WindowsBackend: uninstaller_path=None
11-23 20:35 DEBUG  WindowsBackend: previous_target_dir=None
11-23 20:35 DEBUG  WindowsBackend: previous_distro_name=None
11-23 20:35 DEBUG  WindowsBackend: keyboard_id=67699721
11-23 20:35 DEBUG  WindowsBackend: keyboard_layout=us
11-23 20:35 DEBUG  WindowsBackend: keyboard_variant=
11-23 20:35 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-23 20:35 DEBUG  CommonBackend: locale=en_US.UTF-8
11-23 20:35 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
11-23 20:35 DEBUG  CommonBackend: Searching ISOs on USB devices
11-23 20:35 DEBUG  CommonBackend: Searching for local CDs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:   parsing info from str=Ubuntu 12.04.3 LTS "Precise Pangolin" - Release amd64 (20130820.1)
11-23 20:35 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '12.04.3', 'build': '20130820.1', 'codename': 'Precise Pangolin', 'arch': 'amd64'}
11-23 20:35 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain F:\casper\vmlinuz
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
11-23 20:35 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:35 INFO   root: Running the installer...
11-23 20:35 DEBUG  WindowsFrontend: __init__...
11-23 20:35 DEBUG  WindowsFrontend: on_init...
11-23 20:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
11-23 20:35 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
11-23 20:36 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=9000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=sanjeev
11-23 20:36 INFO   root: Received settings
11-23 20:36 DEBUG  CommonBackend: Searching for local CD
11-23 20:36 DEBUG  Distro:   checking whether C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp is a valid Ubuntu CD
11-23 20:36 DEBUG  Distro:     does not contain C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\casper\filesystem.squashfs
11-23 20:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-23 20:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-23 20:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-23 20:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
11-23 20:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
11-23 20:36 DEBUG  Distro: wrong version: 12.04.3 != 12.04.2
11-23 20:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
11-23 20:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
11-23 20:36 DEBUG  CommonBackend: Searching for local ISO
11-23 20:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\SANJEEV\AppData\Local\Temp\pylA90A.tmp\translations, languages=['en_US', 'en']
11-23 20:36 DEBUG  TaskList: # Running tasklist...
11-23 20:36 DEBUG  TaskList: ## Running select_target_dir...
11-23 20:36 INFO   WindowsBackend: Installing into D:\ubuntu
11-23 20:36 DEBUG  TaskList: ## Finished select_target_dir
11-23 20:36 DEBUG  TaskList: ## Running create_dir_structure...
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
11-23 20:36 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
11-23 20:36 DEBUG  TaskList: ## Finished create_dir_structure
11-23 20:36 DEBUG  TaskList: ## Running create_uninstaller...
11-23 20:36 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04.1-rev273
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-23 20:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-23 20:36 DEBUG  TaskList: ## Finished create_uninstaller
11-23 20:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
11-23 20:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
11-23 20:36 DEBUG  TaskList: ## Running get_diskimage...
11-23 20:36 DEBUG  TaskList: New task download
11-23 20:36 DEBUG  TaskList: ### Running download...
11-23 20:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
11-23 20:36 ERROR  TaskList: [Errno 14] HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
11-23 20:36 ERROR  TaskList: Non fatal error [Errno 14] HTTP Error 404: Not Found in task download
11-23 20:36 DEBUG  TaskList: ### Finished download
11-23 20:36 DEBUG  TaskList: New task download
11-23 20:36 DEBUG  TaskList: ### Running download...
11-23 20:36 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz) > D:\ubuntu\disks\amd64.tar.xz
11-23 20:36 DEBUG  downloader: Download start filename=D:\ubuntu\disks\amd64.tar.xz, url=http://cdimage.ubuntu.com/precise/wubi/current/amd64.tar.xz, basename=amd64.tar.xz, length=545608520, text=None
11-23 20:56 DEBUG  TaskList: ### Finished download
11-23 20:56 DEBUG  downloader: download finished (read 545608520 bytes)
11-23 20:56 DEBUG  TaskList: ## Finished get_diskimage
11-23 20:56 DEBUG  TaskList: ## Running extract_diskimage...
11-23 20:57 DEBUG  TaskList: ## Finished extract_diskimage
11-23 20:57 DEBUG  TaskList: ## Running choose_disk_sizes...
11-23 20:57 DEBUG  WindowsBackend: total size=9000
  root=8744
  swap=256
  home=0
  usr=0
11-23 20:57 DEBUG  TaskList: ## Finished choose_disk_sizes
11-23 20:57 DEBUG  TaskList: ## Running expand_diskimage...
11-23 20:58 DEBUG  TaskList: ## Finished expand_diskimage
11-23 20:58 DEBUG  TaskList: ## Running create_swap_diskimage...
11-23 20:58 DEBUG  TaskList: ## Finished create_swap_diskimage
11-23 20:58 DEBUG  TaskList: ## Running modify_bootloader...
11-23 20:58 DEBUG  TaskList: New task modify_bcd
11-23 20:58 DEBUG  TaskList: ### Running modify_bcd...
11-23 20:58 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 307929.003906 mb free ntfs)
11-23 20:58 ERROR  TaskList: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {397a89ba-3465-11e1-8c17-e2e4c6392984} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {397a89ba-3465-11e1-8c17-e2e4c6392984} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
11-23 20:58 DEBUG  TaskList: # Cancelling tasklist
11-23 20:58 DEBUG  TaskList: New task modify_bcd
11-23 20:58 ERROR  root: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {397a89ba-3465-11e1-8c17-e2e4c6392984} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /set {397a89ba-3465-11e1-8c17-e2e4c6392984} device partition=D:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
11-23 20:58 DEBUG  TaskList: New task modify_bcd
11-23 20:58 DEBUG  TaskList: ## Finished modify_bootloader
11-23 20:58 DEBUG  TaskList: # Finished tasklist



```
Any help is greatly thanked.

---

### Post by electrohandyman501 on 2013-11-23
It won't work.

Text from link below.
[h=3]Neither Ubuntu nor Wubi will boot from a dynamic disk[/h]  Neither Ubuntu's bootloader GRUB nor Wubi's bootloader GRUB4DOS can  recognize a Microsoft dynamic disk/volume/partition (SFS), and so they  cannot boot from it; there is no sense in installing either when you  won't be able to boot.
  [h=3]You have three options:[/h]  
[LIST]
[*]Convert the dynamic disk to basic *(backup all data first!)*, after which you can install Wubi or dual-boot with Ubuntu.
[*]Add another hard disk to your system, install Ubuntu on it and set  your system to boot from it; you can choose to boot Windows or Ubuntu  from the GRUB menu at startup
[*]Keep the disk as is, and run Ubuntu in a virtual machine, such as Virtualbox or VMWare Player.
[/LIST]



read here.
[URL="http://askubuntu.com/questions/179215/why-cant-i-install-ubuntu-or-wubi-on-a-dynamic-disk-the-request-isnt-suppor"]http://askubuntu.com/questions/179215/why-cant-i-install-ubuntu-or-wubi-on-a-dynamic-disk-the-request-isnt-suppor


[/URL]

---

### Post by schittia on 2013-11-24
I tried converting dynamic HD to basic with no avail. the microsoft tutorial doesn't match with any of what I have on my screen, well other tutorials use softwares which are paid. I will try using USB but my question is the files that I create on ubuntu after booting from USB will save on USB or just get deleted after shutting down?

---

### Post by coffeecat on 2013-11-24
> **schittia said:**
> I tried converting dynamic HD to basic with no avail. the microsoft tutorial doesn't match with any of what I have on my screen

Some people report success with Partition Wizard MiniTool for converting a dynamic disk back to a basic one. I have no personal experience of this but it might be worth a try.

As far as wubi is concerned, I notice from your output that you were attempting to install Ubuntu 12.04 with wubi. That's fine, but please be aware that wubi is not supported in Ubuntu 13.04 and 13.10 in case you were considering trying a later version of Ubuntu.

---

### Post by fantab on 2013-11-24
Dynamic Disk is created when you force a fifth primary partition, when you can have only FOUR on a 'msdos' disk.
First of all you have to delete the Fifth partition, then try converting back dynamic to basic.

Post a screen shot of your HDD partitions from Windows Disk Management tool.

---

