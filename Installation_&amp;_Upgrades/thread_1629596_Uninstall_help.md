---
title: "Uninstall help"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by apbshah on 2010-11-23
Hi,
   I recently installed Kubuntu 10.10 It had some errors and took me through GRUB dark screens. I  tried solving it through different things, i honestly don't remember everything I did. One thing I remember was that I replaced a wubildr file. Nothing seemed to work. So, I finally decided to uninstall the whole thing. However, it would let me uninstall and had some errors. So, I used Uninstall-Ubuntu.exe from the link below. ([https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=view&target=Uninstall-Ubuntu.exe) )

I only have one drive C on my laptop. Windows XP seems to work fine, but the partition occupied by linux still shows as being occupied. I can't uninstall/reinstall or delete c:\ubuntu from my drive because of corrupt root.dsk file. its taken up about 30 gigs on my C drive. I've posted the log below. Any help is appreciated. I just want to delete linux partition and any traces of kubuntu all together for now. Thanks.




11-23 21:14 INFO   root: === wubi 10.10 rev197 ===
11-23 21:14 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.10-rev197.log
11-23 21:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
11-23 21:14 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\data
11-23 21:14 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\bin\7z.exe
11-23 21:14 DEBUG  CommonBackend: Fetching basic info...
11-23 21:14 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-23 21:14 DEBUG  CommonBackend: platform=win32
11-23 21:14 DEBUG  CommonBackend: osname=nt
11-23 21:14 DEBUG  CommonBackend: language=en_US
11-23 21:14 DEBUG  CommonBackend: encoding=cp1252
11-23 21:14 DEBUG  WindowsBackend: arch=amd64
11-23 21:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\data\isolist.ini
11-23 21:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-23 21:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-23 21:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-23 21:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-23 21:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-23 21:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-23 21:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-23 21:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-23 21:14 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-23 21:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-23 21:14 DEBUG  WindowsBackend: Fetching host info...
11-23 21:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-23 21:14 DEBUG  WindowsBackend: windows version=xp
11-23 21:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-23 21:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-23 21:14 DEBUG  WindowsBackend: windows_build=2600
11-23 21:14 DEBUG  WindowsBackend: gmt=-5
11-23 21:14 DEBUG  WindowsBackend: country=US
11-23 21:14 DEBUG  WindowsBackend: timezone=America/New_York
11-23 21:14 DEBUG  WindowsBackend: windows_username=Administrator
11-23 21:14 DEBUG  WindowsBackend: user_full_name=Administrator
11-23 21:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
11-23 21:14 DEBUG  WindowsBackend: windows_language_code=1033
11-23 21:14 DEBUG  WindowsBackend: windows_language=English
11-23 21:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
11-23 21:14 DEBUG  WindowsBackend: bootloader=xp
11-23 21:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9698.71484375 mb free ntfs)
11-23 21:14 DEBUG  WindowsBackend: drive=Drive(C: hd 9698.71484375 mb free ntfs)
11-23 21:14 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-23 21:14 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-23 21:14 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-23 21:14 DEBUG  WindowsBackend: keyboard_id=67699721
11-23 21:14 DEBUG  WindowsBackend: keyboard_layout=us
11-23 21:14 DEBUG  WindowsBackend: keyboard_variant=
11-23 21:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-23 21:14 DEBUG  CommonBackend: locale=en_US.UTF-8
11-23 21:14 DEBUG  WindowsBackend: total_memory_mb=1789.859375
11-23 21:14 DEBUG  CommonBackend: Searching ISOs on USB devices
11-23 21:14 DEBUG  CommonBackend: Searching for local CDs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Ubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Ubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Ubuntu Netbook CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Kubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Kubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Kubuntu Netbook CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Xubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Xubuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Mythbuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp is a valid Mythbuntu CD
11-23 21:14 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\casper\filesystem.squashfs
11-23 21:14 INFO   root: Running the uninstaller...
11-23 21:14 INFO   CommonBackend: This is the uninstaller running
11-23 21:14 DEBUG  WindowsFrontend: __init__...
11-23 21:14 DEBUG  WindowsFrontend: on_init...
11-23 21:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\translations, languages=['en_US', 'en']
11-23 21:14 INFO   root: Received settings
11-23 21:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71A.tmp\translations, languages=['en_US', 'en']
11-23 21:14 DEBUG  TaskList: # Running tasklist...
11-23 21:14 DEBUG  TaskList: ## Running Backup ISO...
11-23 21:14 DEBUG  TaskList: ## Finished Backup ISO
11-23 21:14 DEBUG  TaskList: ## Running Remove bootloader entry...
11-23 21:14 ERROR  WindowsBackend: Cannot find bcdedit
11-23 21:14 DEBUG  WindowsBackend: undo_bootini C:
11-23 21:14 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 9698.71484375 mb free ntfs)
11-23 21:14 DEBUG  TaskList: ## Finished Remove bootloader entry
11-23 21:14 DEBUG  TaskList: ## Running Remove target dir...
11-23 21:14 DEBUG  CommonBackend: Deleting C:\ubuntu
11-23 21:14 ERROR  TaskList: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
11-23 21:14 DEBUG  TaskList: # Cancelling tasklist
11-23 21:14 DEBUG  TaskList: # Finished tasklist
11-23 21:14 ERROR  root: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
11-23 21:15 INFO   root: === wubi 10.10 rev197 ===
11-23 21:15 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.10-rev197.log
11-23 21:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
11-23 21:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\data
11-23 21:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\bin\7z.exe
11-23 21:15 DEBUG  CommonBackend: Fetching basic info...
11-23 21:15 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-23 21:15 DEBUG  CommonBackend: platform=win32
11-23 21:15 DEBUG  CommonBackend: osname=nt
11-23 21:15 DEBUG  CommonBackend: language=en_US
11-23 21:15 DEBUG  CommonBackend: encoding=cp1252
11-23 21:15 DEBUG  WindowsBackend: arch=amd64
11-23 21:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\data\isolist.ini
11-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-23 21:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-23 21:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-23 21:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-23 21:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-23 21:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-23 21:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-23 21:15 DEBUG  WindowsBackend: Fetching host info...
11-23 21:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-23 21:15 DEBUG  WindowsBackend: windows version=xp
11-23 21:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-23 21:15 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-23 21:15 DEBUG  WindowsBackend: windows_build=2600
11-23 21:15 DEBUG  WindowsBackend: gmt=-5
11-23 21:15 DEBUG  WindowsBackend: country=US
11-23 21:15 DEBUG  WindowsBackend: timezone=America/New_York
11-23 21:15 DEBUG  WindowsBackend: windows_username=Administrator
11-23 21:15 DEBUG  WindowsBackend: user_full_name=Administrator
11-23 21:15 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
11-23 21:15 DEBUG  WindowsBackend: windows_language_code=1033
11-23 21:15 DEBUG  WindowsBackend: windows_language=English
11-23 21:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
11-23 21:15 DEBUG  WindowsBackend: bootloader=xp
11-23 21:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9695.21484375 mb free ntfs)
11-23 21:15 DEBUG  WindowsBackend: drive=Drive(C: hd 9695.21484375 mb free ntfs)
11-23 21:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-23 21:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-23 21:15 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-23 21:15 DEBUG  WindowsBackend: keyboard_id=67699721
11-23 21:15 DEBUG  WindowsBackend: keyboard_layout=us
11-23 21:15 DEBUG  WindowsBackend: keyboard_variant=
11-23 21:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-23 21:15 DEBUG  CommonBackend: locale=en_US.UTF-8
11-23 21:15 DEBUG  WindowsBackend: total_memory_mb=1789.859375
11-23 21:15 DEBUG  CommonBackend: Searching ISOs on USB devices
11-23 21:15 DEBUG  CommonBackend: Searching for local CDs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Ubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Ubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Ubuntu Netbook CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Kubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Kubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Kubuntu Netbook CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Xubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Xubuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Mythbuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp is a valid Mythbuntu CD
11-23 21:15 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\casper\filesystem.squashfs
11-23 21:15 INFO   root: Running the uninstaller...
11-23 21:15 INFO   CommonBackend: This is the uninstaller running
11-23 21:15 DEBUG  WindowsFrontend: __init__...
11-23 21:15 DEBUG  WindowsFrontend: on_init...
11-23 21:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\translations, languages=['en_US', 'en']
11-23 21:16 INFO   root: === wubi 10.10 rev197 ===
11-23 21:16 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.10-rev197.log
11-23 21:16 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-23 21:16 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\data
11-23 21:16 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\bin\7z.exe
11-23 21:16 DEBUG  CommonBackend: Fetching basic info...
11-23 21:16 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-23 21:16 DEBUG  CommonBackend: platform=win32
11-23 21:16 DEBUG  CommonBackend: osname=nt
11-23 21:16 DEBUG  CommonBackend: language=en_US
11-23 21:16 DEBUG  CommonBackend: encoding=cp1252
11-23 21:16 DEBUG  WindowsBackend: arch=amd64
11-23 21:16 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\data\isolist.ini
11-23 21:16 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-23 21:16 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-23 21:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-23 21:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-23 21:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-23 21:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-23 21:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-23 21:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-23 21:16 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-23 21:16 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-23 21:16 DEBUG  WindowsBackend: Fetching host info...
11-23 21:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-23 21:16 DEBUG  WindowsBackend: windows version=xp
11-23 21:16 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-23 21:16 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-23 21:16 DEBUG  WindowsBackend: windows_build=2600
11-23 21:16 DEBUG  WindowsBackend: gmt=-5
11-23 21:16 DEBUG  WindowsBackend: country=US
11-23 21:16 DEBUG  WindowsBackend: timezone=America/New_York
11-23 21:16 DEBUG  WindowsBackend: windows_username=Administrator
11-23 21:16 DEBUG  WindowsBackend: user_full_name=Administrator
11-23 21:16 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
11-23 21:16 DEBUG  WindowsBackend: windows_language_code=1033
11-23 21:16 DEBUG  WindowsBackend: windows_language=English
11-23 21:16 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
11-23 21:16 DEBUG  WindowsBackend: bootloader=xp
11-23 21:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9645.359375 mb free ntfs)
11-23 21:16 DEBUG  WindowsBackend: drive=Drive(C: hd 9645.359375 mb free ntfs)
11-23 21:16 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-23 21:16 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-23 21:16 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-23 21:16 DEBUG  WindowsBackend: keyboard_id=67699721
11-23 21:16 DEBUG  WindowsBackend: keyboard_layout=us
11-23 21:16 DEBUG  WindowsBackend: keyboard_variant=
11-23 21:16 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-23 21:16 DEBUG  CommonBackend: locale=en_US.UTF-8
11-23 21:16 DEBUG  WindowsBackend: total_memory_mb=1789.859375
11-23 21:16 DEBUG  CommonBackend: Searching ISOs on USB devices
11-23 21:16 DEBUG  CommonBackend: Searching for local CDs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Ubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Ubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Ubuntu Netbook CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Kubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Kubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Kubuntu Netbook CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Xubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Xubuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Mythbuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp is a valid Mythbuntu CD
11-23 21:16 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\casper\filesystem.squashfs
11-23 21:16 INFO   root: Running the uninstaller...
11-23 21:16 INFO   CommonBackend: This is the uninstaller running
11-23 21:16 DEBUG  WindowsFrontend: __init__...
11-23 21:16 DEBUG  WindowsFrontend: on_init...
11-23 21:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl720.tmp\translations, languages=['en_US', 'en']
11-23 21:16 INFO   root: Received settings
11-23 21:16 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl71C.tmp\translations, languages=['en_US', 'en']
11-23 21:16 DEBUG  TaskList: # Running tasklist...
11-23 21:16 DEBUG  TaskList: ## Running Backup ISO...
11-23 21:16 DEBUG  TaskList: ## Finished Backup ISO
11-23 21:16 DEBUG  TaskList: ## Running Remove bootloader entry...
11-23 21:16 ERROR  WindowsBackend: Cannot find bcdedit
11-23 21:16 DEBUG  WindowsBackend: undo_bootini C:
11-23 21:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 9695.21484375 mb free ntfs)
11-23 21:16 DEBUG  TaskList: ## Finished Remove bootloader entry
11-23 21:16 DEBUG  TaskList: ## Running Remove target dir...
11-23 21:16 DEBUG  CommonBackend: Deleting C:\ubuntu
11-23 21:16 ERROR  TaskList: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
11-23 21:16 DEBUG  TaskList: # Cancelling tasklist
11-23 21:16 DEBUG  TaskList: # Finished tasklist
11-23 21:16 ERROR  root: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
11-23 21:16 INFO   WindowsFrontend: Operation cancelled
11-23 21:16 DEBUG  WindowsFrontend: frontend.quit
11-23 21:16 DEBUG  WindowsFrontend: frontend.on_quit
11-23 21:16 DEBUG  root: application.on_quit
11-23 21:16 INFO   root: sys.exit
11-23 21:18 INFO   root: === wubi 10.10 rev197 ===
11-23 21:18 DEBUG  root: Logfile is c:\docume~1\admini~1\locals~1\temp\wubi-10.10-rev197.log
11-23 21:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
11-23 21:18 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\data
11-23 21:18 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\bin\7z.exe
11-23 21:18 DEBUG  CommonBackend: Fetching basic info...
11-23 21:18 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
11-23 21:18 DEBUG  CommonBackend: platform=win32
11-23 21:18 DEBUG  CommonBackend: osname=nt
11-23 21:18 DEBUG  CommonBackend: language=en_US
11-23 21:18 DEBUG  CommonBackend: encoding=cp1252
11-23 21:18 DEBUG  WindowsBackend: arch=amd64
11-23 21:18 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\data\isolist.ini
11-23 21:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
11-23 21:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
11-23 21:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-23 21:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-23 21:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-23 21:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-23 21:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-23 21:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-23 21:18 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
11-23 21:18 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
11-23 21:18 DEBUG  WindowsBackend: Fetching host info...
11-23 21:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-23 21:18 DEBUG  WindowsBackend: windows version=xp
11-23 21:18 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
11-23 21:18 DEBUG  WindowsBackend: windows_sp=Service Pack 3
11-23 21:18 DEBUG  WindowsBackend: windows_build=2600
11-23 21:18 DEBUG  WindowsBackend: gmt=-5
11-23 21:18 DEBUG  WindowsBackend: country=US
11-23 21:18 DEBUG  WindowsBackend: timezone=America/New_York
11-23 21:18 DEBUG  WindowsBackend: windows_username=Administrator
11-23 21:18 DEBUG  WindowsBackend: user_full_name=Administrator
11-23 21:18 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Administrator
11-23 21:18 DEBUG  WindowsBackend: windows_language_code=1033
11-23 21:18 DEBUG  WindowsBackend: windows_language=English
11-23 21:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 CPU         U7600  @ 1.20GHz
11-23 21:18 DEBUG  WindowsBackend: bootloader=xp
11-23 21:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 9635.17578125 mb free ntfs)
11-23 21:18 DEBUG  WindowsBackend: drive=Drive(C: hd 9635.17578125 mb free ntfs)
11-23 21:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
11-23 21:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
11-23 21:18 DEBUG  WindowsBackend: previous_distro_name=Kubuntu
11-23 21:18 DEBUG  WindowsBackend: keyboard_id=67699721
11-23 21:18 DEBUG  WindowsBackend: keyboard_layout=us
11-23 21:18 DEBUG  WindowsBackend: keyboard_variant=
11-23 21:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-23 21:18 DEBUG  CommonBackend: locale=en_US.UTF-8
11-23 21:18 DEBUG  WindowsBackend: total_memory_mb=1789.859375
11-23 21:18 DEBUG  CommonBackend: Searching ISOs on USB devices
11-23 21:18 DEBUG  CommonBackend: Searching for local CDs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Ubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Ubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Ubuntu Netbook CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Kubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Kubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Kubuntu Netbook CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Xubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Xubuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Mythbuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 DEBUG  Distro:   checking whether C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp is a valid Mythbuntu CD
11-23 21:18 DEBUG  Distro:     does not contain C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\casper\filesystem.squashfs
11-23 21:18 INFO   root: Running the uninstaller...
11-23 21:18 INFO   CommonBackend: This is the uninstaller running
11-23 21:18 DEBUG  WindowsFrontend: __init__...
11-23 21:18 DEBUG  WindowsFrontend: on_init...
11-23 21:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\translations, languages=['en_US', 'en']
11-23 21:18 INFO   root: Received settings
11-23 21:18 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\ADMINI~1\LOCALS~1\Temp\pyl721.tmp\translations, languages=['en_US', 'en']
11-23 21:18 DEBUG  TaskList: # Running tasklist...
11-23 21:18 DEBUG  TaskList: ## Running Backup ISO...
11-23 21:18 DEBUG  TaskList: ## Finished Backup ISO
11-23 21:18 DEBUG  TaskList: ## Running Remove bootloader entry...
11-23 21:18 ERROR  WindowsBackend: Cannot find bcdedit
11-23 21:18 DEBUG  WindowsBackend: undo_bootini C:
11-23 21:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 9635.17578125 mb free ntfs)
11-23 21:18 DEBUG  TaskList: ## Finished Remove bootloader entry
11-23 21:18 DEBUG  TaskList: ## Running Remove target dir...
11-23 21:18 DEBUG  CommonBackend: Deleting C:\ubuntu
11-23 21:18 ERROR  TaskList: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
11-23 21:18 DEBUG  TaskList: # Cancelling tasklist
11-23 21:18 DEBUG  TaskList: # Finished tasklist
11-23 21:18 ERROR  root: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
  File "\lib\wubi\backends\common\utils.py", line 316, in rm_tree
  File "\lib\shutil.py", line 142, in rmtree
OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk

---

### Post by garvinrick4 on 2010-11-23
Can you go to C: drive and navigate right next to Users it will say Ubuntu and open that folder and choose uninstall?
If not in ADD and REMOVE programs in Windows and remove Ubuntu?

---

### Post by apbshah on 2010-11-23
Its not there in ADD or Remove program list. I think it already uninstalled using Ubuntu-uninstall.exe. For some reason, the space is still occupied on my hard drive..prolly due to root.dsk file.

---

### Post by garvinrick4 on 2010-11-23
Is it in C: Drive under UBUNTU? 
If is not:
Did you run:
chkdsk /f
defrag your drive a couple of times:
In other words try maintainance on the Windows side to see if
that will get rid of the fouled installation. Best I got.

---

### Post by apbshah on 2010-11-23
yes. exact location
c:\ubuntu\disks\root.disk

---

### Post by garvinrick4 on 2010-11-24
So the uninstall is not in the folder anymore and it does not show in 
Add and Remove programs. I sure hope someone sees this thread that
knows more about getting rid of that folder and all its contents. This post will bump
it up in the forum, good luck to you. I do not know anymore except those
two ways of getting rid of a Wubi install.

---

### Post by bcbc on 2010-11-24
Run chkdsk as garvinrick suggested: Go to My computer, right click on the drive containing the root.disk, Properties, Tools, Check disk for errors, Fix automatically. It will tell you it has to reboot to run. (if you did this already ignore)

Try to uninstall again after that. If that fails try to manually uninstall using these[instructions]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

Finally, if all else fails, I've heard that some people have better luck booting an Ubuntu CD in live CD mode (Try without installing) and then mounting the windows partition and deleting the broken files from there. I'd do this as a last resort.

---

