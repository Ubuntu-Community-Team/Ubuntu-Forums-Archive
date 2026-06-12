---
title: "installation error: &quot;1% is not a valid win32 application&quot;"
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by omerori on 2011-12-03
Hi,

I'm trying to install wubi for the first time, but the installation program stops and says  "1% is not a valid win32 application".

Does anyone know why it happens and what I can do about it?

Thanks,
Omer


log:
```

12-03 11:44 DEBUG  TaskList: New task download
12-03 11:44 DEBUG  TaskList: ### Running download...
12-03 11:44 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-03 11:44 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-03 11:59 DEBUG  TaskList: ### Finished download
12-03 11:59 DEBUG  downloader: download finished (read 507143012 bytes)
12-03 11:59 DEBUG  TaskList: ## Finished get_diskimage
12-03 11:59 DEBUG  TaskList: ## Running extract_diskimage...
12-03 12:01 DEBUG  TaskList: ## Finished extract_diskimage
12-03 12:01 DEBUG  TaskList: ## Running choose_disk_sizes...
12-03 12:01 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-03 12:01 DEBUG  TaskList: ## Finished choose_disk_sizes
12-03 12:01 DEBUG  TaskList: ## Running expand_diskimage...
12-03 12:02 DEBUG  TaskList: ## Finished expand_diskimage
12-03 12:02 DEBUG  TaskList: ## Running create_swap_diskimage...
12-03 12:02 ERROR  TaskList: [Errno 193] %1 is not a valid Win32 application
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 58, in run_command
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 193] %1 is not a valid Win32 application
12-03 12:02 DEBUG  TaskList: # Cancelling tasklist
12-03 12:02 DEBUG  TaskList: # Finished tasklist
12-03 12:02 ERROR  root: [Errno 193] %1 is not a valid Win32 application
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 58, in run_command
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 193] %1 is not a valid Win32 application
12-03 13:25 INFO   root: === wubi 11.10 rev245 ===
12-03 13:25 DEBUG  root: Logfile is c:\docume~1\taub\locals~1\temp\wubi-11.10-rev245.log
12-03 13:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\My Documents\\\xe4\xe5\xf8\xe3\xe5\xfa\\wubi.exe"']
12-03 13:25 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\data
12-03 13:25 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\bin\7z.exe
12-03 13:25 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-03 13:25 DEBUG  CommonBackend: Fetching basic info...
12-03 13:25 DEBUG  CommonBackend: original_exe=D:\My Documents\&#1492;&#1493;&#1512;&#1491;&#1493;&#1514;\wubi.exe
12-03 13:25 DEBUG  CommonBackend: platform=win32
12-03 13:25 DEBUG  CommonBackend: osname=nt
12-03 13:25 DEBUG  CommonBackend: language=he_IL
12-03 13:25 DEBUG  CommonBackend: encoding=cp1255
12-03 13:25 DEBUG  WindowsBackend: arch=amd64
12-03 13:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
12-03 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-03 13:25 DEBUG  WindowsBackend: Fetching host info...
12-03 13:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-03 13:25 DEBUG  WindowsBackend: windows version=2003
12-03 13:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-03 13:25 DEBUG  WindowsBackend: windows_sp=Service Pack 2
12-03 13:25 DEBUG  WindowsBackend: windows_build=3790
12-03 13:25 DEBUG  WindowsBackend: gmt=2
12-03 13:25 DEBUG  WindowsBackend: country=IL
12-03 13:25 DEBUG  WindowsBackend: timezone=Asia/Jerusalem
12-03 13:25 DEBUG  WindowsBackend: windows_username=Taub
12-03 13:25 DEBUG  WindowsBackend: user_full_name=Taub
12-03 13:25 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Taub
12-03 13:25 DEBUG  WindowsBackend: windows_language_code=1037
12-03 13:25 DEBUG  WindowsBackend: windows_language=Hebrew
12-03 13:25 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-03 13:25 DEBUG  WindowsBackend: bootloader=xp
12-03 13:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 40344.265625 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(C: hd 40344.265625 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(D: hd 217190.285156 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-03 13:25 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
12-03 13:25 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
12-03 13:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-03 13:25 DEBUG  WindowsBackend: keyboard_id=67699721
12-03 13:25 DEBUG  WindowsBackend: keyboard_layout=us
12-03 13:25 DEBUG  WindowsBackend: keyboard_variant=
12-03 13:25 DEBUG  CommonBackend: python locale=('he_IL', 'cp1255')
12-03 13:25 DEBUG  CommonBackend: locale=he_IL.UTF-8
12-03 13:25 DEBUG  WindowsBackend: total_memory_mb=1919.26171875
12-03 13:25 DEBUG  CommonBackend: Searching ISOs on USB devices
12-03 13:25 DEBUG  CommonBackend: Searching for local CDs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 INFO   root: Already installed, running the uninstaller...
12-03 13:25 INFO   root: Running the uninstaller...
12-03 13:25 INFO   CommonBackend: This is the uninstaller running
12-03 13:25 DEBUG  WindowsFrontend: __init__...
12-03 13:25 DEBUG  WindowsFrontend: on_init...
12-03 13:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['he_IL', 'he']
12-03 13:25 INFO   root: Received settings
12-03 13:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['he_IL', 'he']
12-03 13:25 DEBUG  TaskList: # Running tasklist...
12-03 13:25 DEBUG  TaskList: ## Running &#1523;”&#1523;¨&#1523;©&#1523;•&#1523;ž&#1523;” &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;× &#1523;ž&#1523;ž&#1523; &#1523;”&#1523;œ &#1523;”&#1523;&#1523;×&#1523;¨&#1523;—&#1523;•&#1523;œ...
12-03 13:25 ERROR  WindowsBackend: Cannot find bcdedit
12-03 13:25 DEBUG  WindowsBackend: undo_bootini C:
12-03 13:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 40344.265625 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: undo_bootini D:
12-03 13:25 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 217190.285156 mb free ntfs)
12-03 13:25 DEBUG  TaskList: ## Finished &#1523;”&#1523;¨&#1523;©&#1523;•&#1523;ž&#1523;” &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;× &#1523;ž&#1523;ž&#1523; &#1523;”&#1523;œ &#1523;”&#1523;&#1523;×&#1523;¨&#1523;—&#1523;•&#1523;œ
12-03 13:25 DEBUG  TaskList: ## Running &#1523;×&#1523;™&#1523;§&#1523;™&#1523;™&#1523;× &#1523;”&#1523;™&#1523;¢&#1523;“ &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;×...
12-03 13:25 DEBUG  CommonBackend: Deleting C:\ubuntu
12-03 13:25 DEBUG  TaskList: ## Finished &#1523;×&#1523;™&#1523;§&#1523;™&#1523;™&#1523;× &#1523;”&#1523;™&#1523;¢&#1523;“ &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;×
12-03 13:25 DEBUG  TaskList: ## Running &#1523;¨&#1523;™&#1523;©&#1523;•&#1523;ž&#1523;™ &#1523;”&#1523;ž&#1523;¢&#1523;¨&#1523;›&#1523;× &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;™&#1523;...
12-03 13:25 DEBUG  TaskList: ## Finished &#1523;¨&#1523;™&#1523;©&#1523;•&#1523;ž&#1523;™ &#1523;”&#1523;ž&#1523;¢&#1523;¨&#1523;›&#1523;× &#1523;ž&#1523;•&#1523;¡&#1523;¨&#1523;™&#1523;
12-03 13:25 DEBUG  TaskList: # Finished tasklist
12-03 13:25 INFO   root: Almost finished uninstalling
12-03 13:25 INFO   root: Finished uninstallation
12-03 13:25 DEBUG  CommonBackend: Fetching basic info...
12-03 13:25 DEBUG  CommonBackend: original_exe=D:\My Documents\&#1492;&#1493;&#1512;&#1491;&#1493;&#1514;\wubi.exe
12-03 13:25 DEBUG  CommonBackend: platform=win32
12-03 13:25 DEBUG  CommonBackend: osname=nt
12-03 13:25 DEBUG  WindowsBackend: arch=amd64
12-03 13:25 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
12-03 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-03 13:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-03 13:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-03 13:25 DEBUG  WindowsBackend: Fetching host info...
12-03 13:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-03 13:25 DEBUG  WindowsBackend: windows version=2003
12-03 13:25 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-03 13:25 DEBUG  WindowsBackend: windows_sp=Service Pack 2
12-03 13:25 DEBUG  WindowsBackend: windows_build=3790
12-03 13:25 DEBUG  WindowsBackend: gmt=2
12-03 13:25 DEBUG  WindowsBackend: country=IL
12-03 13:25 DEBUG  WindowsBackend: timezone=Asia/Jerusalem
12-03 13:25 DEBUG  WindowsBackend: windows_username=Taub
12-03 13:25 DEBUG  WindowsBackend: user_full_name=Taub
12-03 13:25 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Taub
12-03 13:25 DEBUG  WindowsBackend: windows_language_code=1037
12-03 13:25 DEBUG  WindowsBackend: windows_language=Hebrew
12-03 13:25 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
12-03 13:25 DEBUG  WindowsBackend: bootloader=xp
12-03 13:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43174.0703125 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(C: hd 43174.0703125 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(D: hd 217190.285156 mb free ntfs)
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
12-03 13:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
12-03 13:25 DEBUG  WindowsBackend: uninstaller_path=None
12-03 13:25 DEBUG  WindowsBackend: previous_target_dir=None
12-03 13:25 DEBUG  WindowsBackend: previous_distro_name=None
12-03 13:25 DEBUG  WindowsBackend: keyboard_id=67699721
12-03 13:25 DEBUG  WindowsBackend: keyboard_layout=us
12-03 13:25 DEBUG  WindowsBackend: keyboard_variant=
12-03 13:25 DEBUG  WindowsBackend: total_memory_mb=1919.26171875
12-03 13:25 DEBUG  CommonBackend: Searching ISOs on USB devices
12-03 13:25 DEBUG  CommonBackend: Searching for local CDs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 INFO   root: Running the installer...
12-03 13:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['he_IL', 'he']
12-03 13:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['he_IL', 'he']
12-03 13:25 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=he_IL, locale=he_IL.UTF-8, username=omer
12-03 13:25 INFO   root: Received settings
12-03 13:25 DEBUG  CommonBackend: Searching for local CD
12-03 13:25 DEBUG  Distro:   checking whether C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-03 13:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-03 13:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-03 13:25 DEBUG  CommonBackend: Searching for local ISO
12-03 13:25 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Taub\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['he_IL', 'he']
12-03 13:25 DEBUG  TaskList: # Running tasklist...
12-03 13:25 DEBUG  TaskList: ## Running select_target_dir...
12-03 13:25 INFO   WindowsBackend: Installing into C:\ubuntu
12-03 13:25 DEBUG  TaskList: ## Finished select_target_dir
12-03 13:25 DEBUG  TaskList: ## Running create_dir_structure...
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-03 13:25 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-03 13:25 DEBUG  TaskList: ## Finished create_dir_structure
12-03 13:25 DEBUG  TaskList: ## Running create_uninstaller...
12-03 13:25 DEBUG  WindowsBackend: Copying uninstaller D:\My Documents\&#1492;&#1493;&#1512;&#1491;&#1493;&#1514;\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
12-03 13:25 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
12-03 13:25 DEBUG  TaskList: ## Finished create_uninstaller
12-03 13:25 DEBUG  TaskList: ## Running create_preseed_diskimage...
12-03 13:25 DEBUG  TaskList: ## Finished create_preseed_diskimage
12-03 13:25 DEBUG  TaskList: ## Running get_diskimage...
12-03 13:25 DEBUG  TaskList: New task download
12-03 13:25 DEBUG  TaskList: ### Running download...
12-03 13:25 DEBUG  downloader: downloading http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
12-03 13:26 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
12-03 13:40 DEBUG  TaskList: ### Finished download
12-03 13:40 DEBUG  downloader: download finished (read 507143012 bytes)
12-03 13:40 DEBUG  TaskList: ## Finished get_diskimage
12-03 13:40 DEBUG  TaskList: ## Running extract_diskimage...
12-03 13:42 DEBUG  TaskList: ## Finished extract_diskimage
12-03 13:42 DEBUG  TaskList: ## Running choose_disk_sizes...
12-03 13:42 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
12-03 13:42 DEBUG  TaskList: ## Finished choose_disk_sizes
12-03 13:42 DEBUG  TaskList: ## Running expand_diskimage...
12-03 13:43 DEBUG  TaskList: ## Finished expand_diskimage
12-03 13:43 DEBUG  TaskList: ## Running create_swap_diskimage...
12-03 13:43 ERROR  TaskList: [Errno 193] %1 is not a valid Win32 application
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 58, in run_command
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 193] %1 is not a valid Win32 application
12-03 13:43 DEBUG  TaskList: # Cancelling tasklist
12-03 13:43 DEBUG  TaskList: # Finished tasklist
12-03 13:43 ERROR  root: [Errno 193] %1 is not a valid Win32 application
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 468, in create_swap_diskimage
  File "\lib\wubi\backends\common\utils.py", line 58, in run_command
  File "\lib\wubi\backends\common\utils.py", line 52, in spawn_command
  File "\lib\subprocess.py", line 547, in __init__
  File "\lib\subprocess.py", line 701, in _execute_child
WindowsError: [Errno 193] %1 is not a valid Win32 application

```

---

### Post by Rubi1200 on 2011-12-04
Hi and welcome to the forums :)

Download the wubi.exe and relevant Desktop ISO and place them in the same folder before running the executable.

Let us know if that helps.

---

### Post by omerori on 2011-12-05
it worked! thanx

---

### Post by bcbc on 2011-12-05
I created a bug report for you: [https://bugs.launchpad.net/wubi/+bug/900331](https://bugs.launchpad.net/wubi/+bug/900331)

You can subscribe to it in case something interesting happens with it - or to add more info etc.

---

### Post by omerori on 2011-12-05
Thank you bcbc.

In future cases, how do I know whether to file a bug report or not? should I just let more experienced users (like you) do it for me? or just file a report and let others decide about it? I'm not sure what's considered a bug and what the conventions are...

---

### Post by bcbc on 2011-12-05
> **omerori said:**
> Thank you bcbc.

In future cases, how do I know whether to file a bug report or not? should I just let more experienced users (like you) do it for me? or just file a report and let others decide about it? I'm not sure what's considered a bug and what the conventions are...

If you think it's a bug, just go ahead and file it. It's better if you do it yourself - so the devs can contact you through your launchpad id if they need more info.

---

### Post by Rubi1200 on 2011-12-05
Excellent! Glad you got things sorted out and can enjoy Ubuntu.

---

