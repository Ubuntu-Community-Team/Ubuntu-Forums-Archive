---
title: "Wubi install - TypeError: unscriptable object"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by mtr4 on 2012-02-04
Hi all,

I've just tried installing Wubi onto my work laptop (has had a recent rebuild so everything should be fine with!), and when I try to install Wubi I get a TypeError: unsubscriptable object error in the log file.

N:, W:, S: are network drives and D: is my DVD drive

Below is the entire log file
```

02-04 10:07 INFO   root: === wubi 11.10 rev245 ===
02-04 10:07 DEBUG  root: Logfile is c:\docume~1\mruthe~1\locals~1\temp\wubi-11.10-rev245.log
02-04 10:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\mrutherford\\My Documents\\Downloads\\wubi.exe"']
02-04 10:07 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\data
02-04 10:07 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\bin\7z.exe
02-04 10:07 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-04 10:07 DEBUG  CommonBackend: Fetching basic info...
02-04 10:07 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\mrutherford\My Documents\Downloads\wubi.exe
02-04 10:07 DEBUG  CommonBackend: platform=win32
02-04 10:07 DEBUG  CommonBackend: osname=nt
02-04 10:07 DEBUG  CommonBackend: language=en_GB
02-04 10:07 DEBUG  CommonBackend: encoding=cp1252
02-04 10:07 DEBUG  WindowsBackend: arch=amd64
02-04 10:07 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\data\isolist.ini
02-04 10:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-04 10:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-04 10:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-04 10:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-04 10:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-04 10:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-04 10:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-04 10:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-04 10:07 DEBUG  WindowsBackend: Fetching host info...
02-04 10:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-04 10:07 DEBUG  WindowsBackend: windows version=xp
02-04 10:07 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-04 10:07 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-04 10:07 DEBUG  WindowsBackend: windows_build=2600
02-04 10:07 DEBUG  WindowsBackend: gmt=0
02-04 10:07 DEBUG  WindowsBackend: country=GB
02-04 10:07 DEBUG  WindowsBackend: timezone=Europe/London
02-04 10:07 DEBUG  WindowsBackend: windows_username=mrutherford
02-04 10:07 DEBUG  WindowsBackend: user_full_name=mrutherford
02-04 10:07 DEBUG  WindowsBackend: user_directory=N:\
02-04 10:07 DEBUG  WindowsBackend: windows_language_code=1033
02-04 10:07 DEBUG  WindowsBackend: windows_language=English
02-04 10:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
02-04 10:07 DEBUG  WindowsBackend: bootloader=xp
02-04 10:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139210.25 mb free ntfs)
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(C: hd 139210.25 mb free ntfs)
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(N: remote 0.0 mb free )
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(P: remote 0.0 mb free )
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(S: remote 0.0 mb free )
02-04 10:07 DEBUG  WindowsBackend: drive=Drive(W: remote 0.0 mb free )
02-04 10:07 DEBUG  WindowsBackend: uninstaller_path=None
02-04 10:07 DEBUG  WindowsBackend: previous_target_dir=None
02-04 10:07 DEBUG  WindowsBackend: previous_distro_name=None
02-04 10:07 DEBUG  WindowsBackend: keyboard_id=134809609
02-04 10:07 DEBUG  WindowsBackend: keyboard_layout=gb
02-04 10:07 DEBUG  WindowsBackend: keyboard_variant=
02-04 10:07 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-04 10:07 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-04 10:07 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-04 10:07 DEBUG  CommonBackend: Searching ISOs on USB devices
02-04 10:07 DEBUG  CommonBackend: Searching for local CDs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:07 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:07 INFO   root: Running the installer...
02-04 10:07 DEBUG  WindowsFrontend: __init__...
02-04 10:07 DEBUG  WindowsFrontend: on_init...
02-04 10:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\translations, languages=['en_GB', 'en']
02-04 10:07 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\translations, languages=['en_GB', 'en']
02-04 10:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mrutherford
02-04 10:07 INFO   root: Received settings
02-04 10:07 DEBUG  CommonBackend: Searching for local CD
02-04 10:07 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:07 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:07 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  CommonBackend: Searching for local ISO
02-04 10:08 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\mrutherford\My Documents\Downloads\VS2010Express1.iso
02-04 10:08 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-04 10:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7214.tmp\translations, languages=['en_GB', 'en']
02-04 10:08 DEBUG  TaskList: # Running tasklist...
02-04 10:08 DEBUG  TaskList: ## Running select_target_dir...
02-04 10:08 INFO   WindowsBackend: Installing into C:\ubuntu
02-04 10:08 DEBUG  TaskList: ## Finished select_target_dir
02-04 10:08 DEBUG  TaskList: ## Running create_dir_structure...
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-04 10:08 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-04 10:08 DEBUG  TaskList: ## Finished create_dir_structure
02-04 10:08 DEBUG  TaskList: ## Running create_uninstaller...
02-04 10:08 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\mrutherford\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
02-04 10:08 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-04 10:08 DEBUG  TaskList: ## Finished create_uninstaller
02-04 10:08 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-04 10:08 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-04 10:08 DEBUG  TaskList: ## Running get_diskimage...
02-04 10:08 DEBUG  TaskList: New task download
02-04 10:08 DEBUG  TaskList: ### Running download...
02-04 10:08 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-04 10:08 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
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
02-04 10:08 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
02-04 10:08 DEBUG  TaskList: ### Finished download
02-04 10:08 DEBUG  TaskList: ## Finished get_diskimage
02-04 10:08 DEBUG  TaskList: ## Running extract_diskimage...
02-04 10:08 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
02-04 10:08 DEBUG  TaskList: # Cancelling tasklist
02-04 10:08 DEBUG  TaskList: # Finished tasklist
02-04 10:08 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
02-04 10:08 INFO   root: === wubi 11.10 rev245 ===
02-04 10:08 DEBUG  root: Logfile is c:\docume~1\mruthe~1\locals~1\temp\wubi-11.10-rev245.log
02-04 10:08 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\mrutherford\\My Documents\\Downloads\\wubi.exe"']
02-04 10:08 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\data
02-04 10:08 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\bin\7z.exe
02-04 10:08 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
02-04 10:08 DEBUG  CommonBackend: Fetching basic info...
02-04 10:08 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\mrutherford\My Documents\Downloads\wubi.exe
02-04 10:08 DEBUG  CommonBackend: platform=win32
02-04 10:08 DEBUG  CommonBackend: osname=nt
02-04 10:08 DEBUG  CommonBackend: language=en_GB
02-04 10:08 DEBUG  CommonBackend: encoding=cp1252
02-04 10:08 DEBUG  WindowsBackend: arch=amd64
02-04 10:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\data\isolist.ini
02-04 10:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-04 10:08 DEBUG  WindowsBackend: Fetching host info...
02-04 10:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-04 10:08 DEBUG  WindowsBackend: windows version=xp
02-04 10:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-04 10:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-04 10:08 DEBUG  WindowsBackend: windows_build=2600
02-04 10:08 DEBUG  WindowsBackend: gmt=0
02-04 10:08 DEBUG  WindowsBackend: country=GB
02-04 10:08 DEBUG  WindowsBackend: timezone=Europe/London
02-04 10:08 DEBUG  WindowsBackend: windows_username=mrutherford
02-04 10:08 DEBUG  WindowsBackend: user_full_name=mrutherford
02-04 10:08 DEBUG  WindowsBackend: user_directory=N:\
02-04 10:08 DEBUG  WindowsBackend: windows_language_code=1033
02-04 10:08 DEBUG  WindowsBackend: windows_language=English
02-04 10:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
02-04 10:08 DEBUG  WindowsBackend: bootloader=xp
02-04 10:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139208.644531 mb free ntfs)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(C: hd 139208.644531 mb free ntfs)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(N: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(P: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(S: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(W: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
02-04 10:08 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
02-04 10:08 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
02-04 10:08 DEBUG  WindowsBackend: keyboard_id=134809609
02-04 10:08 DEBUG  WindowsBackend: keyboard_layout=gb
02-04 10:08 DEBUG  WindowsBackend: keyboard_variant=
02-04 10:08 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
02-04 10:08 DEBUG  CommonBackend: locale=en_GB.UTF-8
02-04 10:08 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-04 10:08 DEBUG  CommonBackend: Searching ISOs on USB devices
02-04 10:08 DEBUG  CommonBackend: Searching for local CDs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 INFO   root: Already installed, running the uninstaller...
02-04 10:08 INFO   root: Running the uninstaller...
02-04 10:08 INFO   CommonBackend: This is the uninstaller running
02-04 10:08 DEBUG  WindowsFrontend: __init__...
02-04 10:08 DEBUG  WindowsFrontend: on_init...
02-04 10:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\translations, languages=['en_GB', 'en']
02-04 10:08 INFO   root: Received settings
02-04 10:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\translations, languages=['en_GB', 'en']
02-04 10:08 DEBUG  TaskList: # Running tasklist...
02-04 10:08 DEBUG  TaskList: ## Running Remove bootloader entry....
02-04 10:08 ERROR  WindowsBackend: Cannot find bcdedit
02-04 10:08 DEBUG  WindowsBackend: undo_bootini C:
02-04 10:08 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 139208.644531 mb free ntfs)
02-04 10:08 DEBUG  TaskList: ## Finished Remove bootloader entry.
02-04 10:08 DEBUG  TaskList: ## Running Remove target dir....
02-04 10:08 DEBUG  CommonBackend: Deleting C:\ubuntu
02-04 10:08 DEBUG  TaskList: ## Finished Remove target dir.
02-04 10:08 DEBUG  TaskList: ## Running Remove registry key....
02-04 10:08 DEBUG  TaskList: ## Finished Remove registry key.
02-04 10:08 DEBUG  TaskList: # Finished tasklist
02-04 10:08 INFO   root: Almost finished uninstalling
02-04 10:08 INFO   root: Finished uninstallation
02-04 10:08 DEBUG  CommonBackend: Fetching basic info...
02-04 10:08 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\mrutherford\My Documents\Downloads\wubi.exe
02-04 10:08 DEBUG  CommonBackend: platform=win32
02-04 10:08 DEBUG  CommonBackend: osname=nt
02-04 10:08 DEBUG  WindowsBackend: arch=amd64
02-04 10:08 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\data\isolist.ini
02-04 10:08 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
02-04 10:08 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
02-04 10:08 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
02-04 10:08 DEBUG  WindowsBackend: Fetching host info...
02-04 10:08 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
02-04 10:08 DEBUG  WindowsBackend: windows version=xp
02-04 10:08 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
02-04 10:08 DEBUG  WindowsBackend: windows_sp=Service Pack 3
02-04 10:08 DEBUG  WindowsBackend: windows_build=2600
02-04 10:08 DEBUG  WindowsBackend: gmt=0
02-04 10:08 DEBUG  WindowsBackend: country=GB
02-04 10:08 DEBUG  WindowsBackend: timezone=Europe/London
02-04 10:08 DEBUG  WindowsBackend: windows_username=mrutherford
02-04 10:08 DEBUG  WindowsBackend: user_full_name=mrutherford
02-04 10:08 DEBUG  WindowsBackend: user_directory=N:\
02-04 10:08 DEBUG  WindowsBackend: windows_language_code=1033
02-04 10:08 DEBUG  WindowsBackend: windows_language=English
02-04 10:08 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5670  @ 1.80GHz
02-04 10:08 DEBUG  WindowsBackend: bootloader=xp
02-04 10:08 DEBUG  WindowsBackend: system_drive=Drive(C: hd 139210.933594 mb free ntfs)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(C: hd 139210.933594 mb free ntfs)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free udf)
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(N: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(P: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(S: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: drive=Drive(W: remote 0.0 mb free )
02-04 10:08 DEBUG  WindowsBackend: uninstaller_path=None
02-04 10:08 DEBUG  WindowsBackend: previous_target_dir=None
02-04 10:08 DEBUG  WindowsBackend: previous_distro_name=None
02-04 10:08 DEBUG  WindowsBackend: keyboard_id=134809609
02-04 10:08 DEBUG  WindowsBackend: keyboard_layout=gb
02-04 10:08 DEBUG  WindowsBackend: keyboard_variant=
02-04 10:08 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
02-04 10:08 DEBUG  CommonBackend: Searching ISOs on USB devices
02-04 10:08 DEBUG  CommonBackend: Searching for local CDs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether N:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether P:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether S:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
02-04 10:08 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:08 INFO   root: Running the installer...
02-04 10:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\translations, languages=['en_GB', 'en']
02-04 10:08 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\translations, languages=['en_GB', 'en']
02-04 10:08 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=mrutherford
02-04 10:08 INFO   root: Received settings
02-04 10:08 DEBUG  CommonBackend: Searching for local CD
02-04 10:08 DEBUG  Distro:   checking whether C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\casper\filesystem.squashfs
02-04 10:08 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
02-04 10:08 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
02-04 10:09 DEBUG  Distro:   checking whether N:\ is a valid Ubuntu CD
02-04 10:09 DEBUG  Distro:     does not contain N:\casper\filesystem.squashfs
02-04 10:09 DEBUG  Distro:   checking whether P:\ is a valid Ubuntu CD
02-04 10:09 DEBUG  Distro:     does not contain P:\casper\filesystem.squashfs
02-04 10:09 DEBUG  Distro:   checking whether S:\ is a valid Ubuntu CD
02-04 10:09 DEBUG  Distro:     does not contain S:\casper\filesystem.squashfs
02-04 10:09 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
02-04 10:09 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
02-04 10:09 DEBUG  CommonBackend: Searching for local ISO
02-04 10:09 DEBUG  Distro:   checking Ubuntu ISO C:\Documents and Settings\mrutherford\My Documents\Downloads\VS2010Express1.iso
02-04 10:09 DEBUG  Distro:     does not contain casper\filesystem.squashfs
02-04 10:09 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\MRUTHE~1\LOCALS~1\Temp\pyl7215.tmp\translations, languages=['en_GB', 'en']
02-04 10:09 DEBUG  TaskList: # Running tasklist...
02-04 10:09 DEBUG  TaskList: ## Running select_target_dir...
02-04 10:09 INFO   WindowsBackend: Installing into C:\ubuntu
02-04 10:09 DEBUG  TaskList: ## Finished select_target_dir
02-04 10:09 DEBUG  TaskList: ## Running create_dir_structure...
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
02-04 10:09 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
02-04 10:09 DEBUG  TaskList: ## Finished create_dir_structure
02-04 10:09 DEBUG  TaskList: ## Running create_uninstaller...
02-04 10:09 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\mrutherford\My Documents\Downloads\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com]("http://www.ubuntu.com/")
02-04 10:09 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
02-04 10:09 DEBUG  TaskList: ## Finished create_uninstaller
02-04 10:09 DEBUG  TaskList: ## Running create_preseed_diskimage...
02-04 10:09 DEBUG  TaskList: ## Finished create_preseed_diskimage
02-04 10:09 DEBUG  TaskList: ## Running get_diskimage...
02-04 10:09 DEBUG  TaskList: New task download
02-04 10:09 DEBUG  TaskList: ### Running download...
02-04 10:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-04 10:09 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
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
02-04 10:09 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
02-04 10:09 DEBUG  TaskList: ### Finished download
02-04 10:09 DEBUG  TaskList: ## Finished get_diskimage
02-04 10:09 DEBUG  TaskList: ## Running extract_diskimage...
02-04 10:09 ERROR  TaskList: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
02-04 10:09 DEBUG  TaskList: # Cancelling tasklist
02-04 10:09 DEBUG  TaskList: # Finished tasklist
02-04 10:09 ERROR  root: unsubscriptable object
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 439, in extract_diskimage
  File "\lib\ntpath.py", line 199, in basename
  File "\lib\ntpath.py", line 163, in split
  File "\lib\ntpath.py", line 118, in splitdrive
TypeError: unsubscriptable object
```

----------

Any help greatfully received!!! :)

Cheers,

Matt

---

### Post by oldfred on 2012-02-05
Added code tags to make it easier to review. But I do not know wubi.

Since this is a company computer, do you have permission to install another operating system? 

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by bcbc on 2012-02-05
It's having a problem when it tries to download the 'preinstalled' image. Are you connected to the internet?
> 02-04 10:09 DEBUG  TaskList: ### Running download...
02-04 10:09 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubu...i-amd64.tar.xz]("http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz") > C:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
02-04 10:09 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):

---

### Post by jtmedin on 2012-02-16
Ok i have the same error with wubi. Wonder if u have a solution? TIA

---

### Post by jtmedin on 2012-02-16
May have misread the instructions for wubi. Looked like it was looking for a iso cd. So generated a cd & then started the cd. It gave me the option of installing withing windows so after a couple of miscues got it installed :-). Installation is not without problems (wireless internet connection) but i am working on that.

---

