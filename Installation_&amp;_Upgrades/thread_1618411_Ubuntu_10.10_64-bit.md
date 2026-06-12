---
title: "Ubuntu 10.10 64-bit"
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by devil89 on 2010-11-10
[SIZE=5]Hello guys

I am new to ubuntu. I have installed this new ubuntu in my laptop..It's great, but unfortunately during installation i've messed up with my original windows 7 home premium 64-bit, causing it to be erased from hdd and could not be reinstalled because windows installation disk somehow did not found my hdd.maybe it is my fault who did not understand how to install.so maybe after this i will try to reinstall windows and try to dual boot back with this ubuntu 10.10 64-bit. I am hoping that i can get the correct guide for doing this because i did not want to messed up my computer again. Sorry if i'm using bad english. I'm an Asian.
[/SIZE]

---

### Post by sikander3786 on 2010-11-11
Seems like you format your whole drive to ext3 or ext4 i.e, Linux filesystems so Windows might not recognize the partitions. But it should recognize the HDD itself saying something like unknown partition.

If you want to reinstall Windows, it should be simply straight forward. Once you get it reinstalled, boot into an Ubuntu LiveCD and from the terminal, it is under Applications > Accessories > Terminal, post the output of

```
sudo fdisk -l
```

That will help us understand your partitioning scheme and help you accordingly.

See this for dual-boot instructions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by devil89 on 2010-11-12
I just managed to reinstall windows back. But unfortunately i lost all my downloaded files. Actually, i've read the guide for dual-boot. But the option at my LiveCD is different(only 2 choice available, which is erase entire disk and set partition manually[the advance option]).

---

### Post by sikander3786 on 2010-11-13
You can either select to install side by side with Windows.

Or free up some space using the partitioning tool in Windows. Resize your C: drive and leave the unacllocated space. Later in Ubuntu installer, select that space and create partitions in it by select the manual partitioning.

It would be better if you could post the output of above mentioned command from Live CD so we can advise better.

Basically you need just 2 partitions for Ubuntu installation.

1. / Ubuntu Root partition formatted ext3 or ext4, Mount Point '/'.

2. Swap Partition, size=RAM X 2.

There should also be an option in the Ubuntu installer to use the largest free space. I haven't used 10.10 installer yet so am not sure how it looks like. It has been renamed, but it is still there.

---

### Post by devil89 on 2010-11-14
Well, now i try to install it inside windows. But now i got this error...

invalid argument

below is the error log file

btw, i am using Acer Aspire 4740G..that should not be a problem right? 

sorry i could not upload it as attachment because file size is too large


11-14 22:29 INFO   root: === wubi 10.10 rev197 ===
11-14 22:29 DEBUG  root: Logfile is c:\users\devil\appdata\local\temp\wubi-10.10-rev197.log
11-14 22:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-14 22:29 DEBUG  CommonBackend: data_dir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\data
11-14 22:29 DEBUG  WindowsBackend: 7z=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\bin\7z.exe
11-14 22:29 DEBUG  CommonBackend: Fetching basic info...
11-14 22:29 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-14 22:29 DEBUG  CommonBackend: platform=win32
11-14 22:29 DEBUG  CommonBackend: osname=nt
11-14 22:29 DEBUG  CommonBackend: language=en_MY
11-14 22:29 DEBUG  CommonBackend: encoding=cp1252
11-14 22:29 DEBUG  WindowsBackend: arch=amd64
11-14 22:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\data\isolist.ini
11-14 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-14 22:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-14 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-14 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-14 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-14 22:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-14 22:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-14 22:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-14 22:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-14 22:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-14 22:29 DEBUG  WindowsBackend: Fetching host info...
11-14 22:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-14 22:29 DEBUG  WindowsBackend: windows version=vista
11-14 22:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-14 22:29 DEBUG  WindowsBackend: windows_sp=None
11-14 22:29 DEBUG  WindowsBackend: windows_build=7600
11-14 22:29 DEBUG  WindowsBackend: gmt=8
11-14 22:29 DEBUG  WindowsBackend: country=MY
11-14 22:29 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
11-14 22:29 DEBUG  WindowsBackend: windows_username=Devil
11-14 22:29 DEBUG  WindowsBackend: user_full_name=Devil
11-14 22:29 DEBUG  WindowsBackend: user_directory=C:\Users\Devil
11-14 22:29 DEBUG  WindowsBackend: windows_language_code=1033
11-14 22:29 DEBUG  WindowsBackend: windows_language=English
11-14 22:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-14 22:29 DEBUG  WindowsBackend: bootloader=vista
11-14 22:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147242.851563 mb free ntfs)
11-14 22:29 DEBUG  WindowsBackend: drive=Drive(C: hd 147242.851563 mb free ntfs)
11-14 22:29 DEBUG  WindowsBackend: drive=Drive(D: hd 275194.203125 mb free ntfs)
11-14 22:29 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-14 22:29 DEBUG  WindowsBackend: uninstaller_path=None
11-14 22:29 DEBUG  WindowsBackend: previous_target_dir=None
11-14 22:29 DEBUG  WindowsBackend: previous_distro_name=None
11-14 22:29 DEBUG  WindowsBackend: keyboard_id=67699721
11-14 22:29 DEBUG  WindowsBackend: keyboard_layout=us
11-14 22:29 DEBUG  WindowsBackend: keyboard_variant=
11-14 22:29 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
11-14 22:29 DEBUG  CommonBackend: locale=en_US.UTF-8
11-14 22:29 DEBUG  WindowsBackend: total_memory_mb=1974.70703125
11-14 22:29 DEBUG  CommonBackend: Searching ISOs on USB devices
11-14 22:29 DEBUG  CommonBackend: Searching for local CDs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Ubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Ubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Ubuntu Netbook CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Kubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Kubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Kubuntu Netbook CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Xubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Xubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Mythbuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp is a valid Mythbuntu CD
11-14 22:29 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-14 22:29 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-14 22:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-14 22:29 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-14 22:29 INFO   root: Running the CD menu...
11-14 22:29 DEBUG  WindowsFrontend: __init__...
11-14 22:29 DEBUG  WindowsFrontend: on_init...
11-14 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\translations, languages=['en_US', 'en']
11-14 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\translations, languages=['en_US', 'en']
11-14 22:29 INFO   root: CD menu finished
11-14 22:29 INFO   root: Running the installer...
11-14 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\translations, languages=['en_US', 'en']
11-14 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\translations, languages=['en_US', 'en']
11-14 22:29 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=eddie
11-14 22:29 INFO   root: Received settings
11-14 22:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\translations, languages=['en_US', 'en']
11-14 22:29 DEBUG  TaskList: # Running tasklist...
11-14 22:29 DEBUG  TaskList: ## Running select_target_dir...
11-14 22:29 INFO   WindowsBackend: Installing into C:\ubuntu
11-14 22:29 DEBUG  TaskList: ## Finished select_target_dir
11-14 22:29 DEBUG  TaskList: ## Running create_dir_structure...
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-14 22:29 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-14 22:29 DEBUG  TaskList: ## Finished create_dir_structure
11-14 22:29 DEBUG  TaskList: ## Running uncompress_target_dir...
11-14 22:29 DEBUG  TaskList: ## Finished uncompress_target_dir
11-14 22:29 DEBUG  TaskList: ## Running create_uninstaller...
11-14 22:29 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-14 22:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-14 22:29 DEBUG  TaskList: ## Finished create_uninstaller
11-14 22:29 DEBUG  TaskList: ## Running copy_installation_files...
11-14 22:29 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-14 22:29 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\winboot -> C:\ubuntu\winboot
11-14 22:29 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pylBF8A.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-14 22:29 DEBUG  TaskList: ## Finished copy_installation_files
11-14 22:29 DEBUG  TaskList: ## Running get_iso...
11-14 22:29 DEBUG  TaskList: New task copy_file
11-14 22:29 DEBUG  TaskList: ### Running copy_file...
11-14 22:36 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-14 22:36 DEBUG  TaskList: # Cancelling tasklist
11-14 22:36 DEBUG  TaskList: New task check_iso
11-14 22:36 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-14 22:36 DEBUG  CommonBackend: Searching for local ISO
11-14 22:36 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-14 22:36 DEBUG  TaskList: New task get_metalink
11-14 22:36 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-14 22:36 DEBUG  TaskList: # Cancelling tasklist
11-14 22:36 DEBUG  TaskList: # Finished tasklist
11-14 22:40 INFO   root: === wubi 10.10 rev197 ===
11-14 22:40 DEBUG  root: Logfile is c:\users\devil\appdata\local\temp\wubi-10.10-rev197.log
11-14 22:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-14 22:40 DEBUG  CommonBackend: data_dir=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\data
11-14 22:40 DEBUG  WindowsBackend: 7z=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\bin\7z.exe
11-14 22:40 DEBUG  CommonBackend: Fetching basic info...
11-14 22:40 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-14 22:40 DEBUG  CommonBackend: platform=win32
11-14 22:40 DEBUG  CommonBackend: osname=nt
11-14 22:40 DEBUG  CommonBackend: language=en_MY
11-14 22:40 DEBUG  CommonBackend: encoding=cp1252
11-14 22:40 DEBUG  WindowsBackend: arch=amd64
11-14 22:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\data\isolist.ini
11-14 22:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-14 22:40 DEBUG  WindowsBackend: Fetching host info...
11-14 22:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-14 22:40 DEBUG  WindowsBackend: windows version=vista
11-14 22:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-14 22:40 DEBUG  WindowsBackend: windows_sp=None
11-14 22:40 DEBUG  WindowsBackend: windows_build=7600
11-14 22:40 DEBUG  WindowsBackend: gmt=8
11-14 22:40 DEBUG  WindowsBackend: country=MY
11-14 22:40 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
11-14 22:40 DEBUG  WindowsBackend: windows_username=Devil
11-14 22:40 DEBUG  WindowsBackend: user_full_name=Devil
11-14 22:40 DEBUG  WindowsBackend: user_directory=C:\Users\Devil
11-14 22:40 DEBUG  WindowsBackend: windows_language_code=1033
11-14 22:40 DEBUG  WindowsBackend: windows_language=English
11-14 22:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-14 22:40 DEBUG  WindowsBackend: bootloader=vista
11-14 22:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 146652.003906 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(C: hd 146652.0 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(D: hd 275194.203125 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-14 22:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-14 22:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-14 22:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
11-14 22:40 DEBUG  WindowsBackend: keyboard_id=67699721
11-14 22:40 DEBUG  WindowsBackend: keyboard_layout=us
11-14 22:40 DEBUG  WindowsBackend: keyboard_variant=
11-14 22:40 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
11-14 22:40 DEBUG  CommonBackend: locale=en_US.UTF-8
11-14 22:40 DEBUG  WindowsBackend: total_memory_mb=1974.70703125
11-14 22:40 DEBUG  CommonBackend: Searching ISOs on USB devices
11-14 22:40 DEBUG  CommonBackend: Searching for local CDs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Ubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Kubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-14 22:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-14 22:40 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-14 22:40 INFO   root: Running the uninstaller...
11-14 22:40 INFO   CommonBackend: This is the uninstaller running
11-14 22:40 DEBUG  WindowsFrontend: __init__...
11-14 22:40 DEBUG  WindowsFrontend: on_init...
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\translations, languages=['en_US', 'en']
11-14 22:40 INFO   root: Received settings
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\translations, languages=['en_US', 'en']
11-14 22:40 DEBUG  TaskList: # Running tasklist...
11-14 22:40 DEBUG  TaskList: ## Running Backup ISO...
11-14 22:40 DEBUG  TaskList: ## Finished Backup ISO
11-14 22:40 DEBUG  TaskList: ## Running Remove bootloader entry...
11-14 22:40 DEBUG  WindowsBackend: Could not find bcd id
11-14 22:40 DEBUG  WindowsBackend: undo_bootini C:
11-14 22:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 146652.0 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: undo_bootini D:
11-14 22:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 275194.203125 mb free ntfs)
11-14 22:40 DEBUG  TaskList: ## Finished Remove bootloader entry
11-14 22:40 DEBUG  TaskList: ## Running Remove target dir...
11-14 22:40 DEBUG  CommonBackend: Deleting C:\ubuntu
11-14 22:40 DEBUG  TaskList: ## Finished Remove target dir
11-14 22:40 DEBUG  TaskList: ## Running Remove registry key...
11-14 22:40 DEBUG  TaskList: ## Finished Remove registry key
11-14 22:40 DEBUG  TaskList: # Finished tasklist
11-14 22:40 INFO   root: Almost finished uninstalling
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pylC69C.tmp\translations, languages=['en_US', 'en']
11-14 22:40 INFO   root: Finished uninstallation
11-14 22:40 DEBUG  root: application.quit
11-14 22:40 DEBUG  WindowsFrontend: frontend.quit
11-14 22:40 DEBUG  WindowsFrontend: frontend.on_quit
11-14 22:40 DEBUG  root: application.on_quit
11-14 22:40 INFO   root: sys.exit
11-14 22:40 INFO   root: === wubi 10.10 rev197 ===
11-14 22:40 DEBUG  root: Logfile is c:\users\devil\appdata\local\temp\wubi-10.10-rev197.log
11-14 22:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"', '--cdmenu']
11-14 22:40 DEBUG  CommonBackend: data_dir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\data
11-14 22:40 DEBUG  WindowsBackend: 7z=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\bin\7z.exe
11-14 22:40 DEBUG  CommonBackend: Fetching basic info...
11-14 22:40 DEBUG  CommonBackend: original_exe=E:\wubi.exe
11-14 22:40 DEBUG  CommonBackend: platform=win32
11-14 22:40 DEBUG  CommonBackend: osname=nt
11-14 22:40 DEBUG  CommonBackend: language=en_MY
11-14 22:40 DEBUG  CommonBackend: encoding=cp1252
11-14 22:40 DEBUG  WindowsBackend: arch=amd64
11-14 22:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\data\isolist.ini
11-14 22:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-14 22:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-14 22:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-14 22:40 DEBUG  WindowsBackend: Fetching host info...
11-14 22:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-14 22:40 DEBUG  WindowsBackend: windows version=vista
11-14 22:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
11-14 22:40 DEBUG  WindowsBackend: windows_sp=None
11-14 22:40 DEBUG  WindowsBackend: windows_build=7600
11-14 22:40 DEBUG  WindowsBackend: gmt=8
11-14 22:40 DEBUG  WindowsBackend: country=MY
11-14 22:40 DEBUG  WindowsBackend: timezone=Asia/Kuala_Lumpur
11-14 22:40 DEBUG  WindowsBackend: windows_username=Devil
11-14 22:40 DEBUG  WindowsBackend: user_full_name=Devil
11-14 22:40 DEBUG  WindowsBackend: user_directory=C:\Users\Devil
11-14 22:40 DEBUG  WindowsBackend: windows_language_code=1033
11-14 22:40 DEBUG  WindowsBackend: windows_language=English
11-14 22:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 430  @ 2.27GHz
11-14 22:40 DEBUG  WindowsBackend: bootloader=vista
11-14 22:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 147242.554688 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(C: hd 147242.554688 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(D: hd 275194.203125 mb free ntfs)
11-14 22:40 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
11-14 22:40 DEBUG  WindowsBackend: uninstaller_path=None
11-14 22:40 DEBUG  WindowsBackend: previous_target_dir=None
11-14 22:40 DEBUG  WindowsBackend: previous_distro_name=None
11-14 22:40 DEBUG  WindowsBackend: keyboard_id=67699721
11-14 22:40 DEBUG  WindowsBackend: keyboard_layout=us
11-14 22:40 DEBUG  WindowsBackend: keyboard_variant=
11-14 22:40 DEBUG  CommonBackend: python locale=('en_MY', 'cp1252')
11-14 22:40 DEBUG  CommonBackend: locale=en_US.UTF-8
11-14 22:40 DEBUG  WindowsBackend: total_memory_mb=1974.70703125
11-14 22:40 DEBUG  CommonBackend: Searching ISOs on USB devices
11-14 22:40 DEBUG  CommonBackend: Searching for local CDs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Ubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Kubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
11-14 22:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
11-14 22:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
11-14 22:40 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release amd64 (20101007)
11-14 22:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'amd64'}
11-14 22:40 INFO   Distro: Found a valid CD for Ubuntu: E:\
11-14 22:40 INFO   root: Running the CD menu...
11-14 22:40 DEBUG  WindowsFrontend: __init__...
11-14 22:40 DEBUG  WindowsFrontend: on_init...
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\translations, languages=['en_US', 'en']
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\translations, languages=['en_US', 'en']
11-14 22:40 INFO   root: CD menu finished
11-14 22:40 INFO   root: Running the installer...
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\translations, languages=['en_US', 'en']
11-14 22:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\translations, languages=['en_US', 'en']
11-14 22:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=devil
11-14 22:41 INFO   root: Received settings
11-14 22:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\translations, languages=['en_US', 'en']
11-14 22:41 DEBUG  TaskList: # Running tasklist...
11-14 22:41 DEBUG  TaskList: ## Running select_target_dir...
11-14 22:41 INFO   WindowsBackend: Installing into C:\ubuntu
11-14 22:41 DEBUG  TaskList: ## Finished select_target_dir
11-14 22:41 DEBUG  TaskList: ## Running create_dir_structure...
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
11-14 22:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
11-14 22:41 DEBUG  TaskList: ## Finished create_dir_structure
11-14 22:41 DEBUG  TaskList: ## Running uncompress_target_dir...
11-14 22:41 DEBUG  TaskList: ## Finished uncompress_target_dir
11-14 22:41 DEBUG  TaskList: ## Running create_uninstaller...
11-14 22:41 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
11-14 22:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
11-14 22:41 DEBUG  TaskList: ## Finished create_uninstaller
11-14 22:41 DEBUG  TaskList: ## Running copy_installation_files...
11-14 22:41 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
11-14 22:41 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\winboot -> C:\ubuntu\winboot
11-14 22:41 DEBUG  WindowsBackend: Copying C:\Users\Devil\AppData\Local\Temp\pyl12E7.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
11-14 22:41 DEBUG  TaskList: ## Finished copy_installation_files
11-14 22:41 DEBUG  TaskList: ## Running get_iso...
11-14 22:41 DEBUG  TaskList: New task copy_file
11-14 22:41 DEBUG  TaskList: ### Running copy_file...
11-14 23:00 ERROR  TaskList: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-14 23:00 DEBUG  TaskList: # Cancelling tasklist
11-14 23:00 ERROR  root: [Errno 22] Invalid argument
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 22] Invalid argument
11-14 23:00 DEBUG  TaskList: New task check_iso
11-14 23:00 DEBUG  CommonBackend: Searching for local ISO
11-14 23:00 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
11-14 23:00 DEBUG  TaskList: New task get_metalink
11-14 23:00 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
11-14 23:00 DEBUG  TaskList: # Cancelling tasklist
11-14 23:00 DEBUG  TaskList: # Finished tasklist

---

### Post by efflandt on 2010-11-14
I don't know if Wubi totally uninstalled itself, because it looks like after it did that, it tried to install again. Is Win7 still able to boot?

For Vista and Win7 it is generally recommended to shrink its system partition with its own tools under Computer Management.  I would free up about 30 GB plus whatever you need for swap.  Swap does NOT need to be 2 times RAM (that is old info from before computers had much RAM).  Swap just needs to be slightly larger than RAM if you want to be able to hibernate (which saves RAM to swap).  Swap is not needed for suspend (to sleep in a low power state).

Then boot the install CD to a live system and use System > Administration > Gparted to make a swap partition a bit bigger than your RAM and make the rest into an ext3 or ext4 partition for Ubuntu.

Then double click the install icon and when it gets to partitioning, do that manually.  It will automatically use any swap, but you need to assign the partition you just made as /

Note that a disk can only have 4 primary or extended partitions.  So if that drive already has 3 partitions, you would first need to create an extended partition, and then logical partitions for swap and /

---

### Post by devil89 on 2010-11-14
[SIZE=3]Yes windows 7 still can boot..this happens when i try to install ubuntu in windows..my previous attempt to install it alongside windows had made my windows crash(because the partitions gone haywire), resulting me reformat entire disk just to reinstall windows back..so this time i want to try installing ubuntu in windows
[/SIZE]

---

### Post by devil89 on 2010-11-18
anyone??

---

### Post by bcbc on 2010-11-18
Looks like there was an error copying from the CD to the temporary install .iso image (wubi copies and modifies the CD image). For some reason wubi can have a problem with certain CD/DVD drives and/or the CD.

Instead, you can download and place the ubuntu install .iso in the same folder as wubi.exe, and run it from there. Make sure you run it as administrator, allow access to the internet (and firewall access to pyrun.exe - the python runtime that wubi uses).

---

