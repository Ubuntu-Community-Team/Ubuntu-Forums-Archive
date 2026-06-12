---
title: "Unable to install ubuntu in windows with wubi"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by waqas300 on 2012-09-28
i have windows 64bit and downloaded ubuntu 64bit. i am trying to install it inside windows but unable to do so. please refer to the log.


09-29 00:33 INFO   root: === wubi 12.04 rev266 ===
09-29 00:33 DEBUG  root: Logfile is c:\users\waqas\appdata\local\temp\wubi-12.04-rev266.log
09-29 00:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu-12.04-desktop-amd64\\wubi.exe"']
09-29 00:33 DEBUG  CommonBackend: data_dir=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\data
09-29 00:33 DEBUG  WindowsBackend: 7z=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\bin\7z.exe
09-29 00:33 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 00:33 DEBUG  CommonBackend: Fetching basic info...
09-29 00:33 DEBUG  CommonBackend: original_exe=D:\ubuntu-12.04-desktop-amd64\wubi.exe
09-29 00:33 DEBUG  CommonBackend: platform=win32
09-29 00:33 DEBUG  CommonBackend: osname=nt
09-29 00:33 DEBUG  CommonBackend: language=en_US
09-29 00:33 DEBUG  CommonBackend: encoding=cp1252
09-29 00:33 DEBUG  WindowsBackend: arch=amd64
09-29 00:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\data\isolist.ini
09-29 00:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 00:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 00:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-29 00:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 00:33 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 00:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 00:33 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-29 00:33 DEBUG  WindowsBackend: Fetching host info...
09-29 00:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 00:33 DEBUG  WindowsBackend: windows version=vista
09-29 00:33 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 00:33 DEBUG  WindowsBackend: windows_sp=None
09-29 00:33 DEBUG  WindowsBackend: windows_build=7601
09-29 00:33 DEBUG  WindowsBackend: gmt=4
09-29 00:33 DEBUG  WindowsBackend: country=US
09-29 00:33 DEBUG  WindowsBackend: timezone=America/New_York
09-29 00:33 DEBUG  WindowsBackend: windows_username=waqas
09-29 00:33 DEBUG  WindowsBackend: user_full_name=waqas
09-29 00:33 DEBUG  WindowsBackend: user_directory=C:\Users\waqas
09-29 00:33 DEBUG  WindowsBackend: windows_language_code=1033
09-29 00:33 DEBUG  WindowsBackend: windows_language=English
09-29 00:33 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
09-29 00:33 DEBUG  WindowsBackend: bootloader=vista
09-29 00:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53071.84375 mb free ntfs)
09-29 00:33 DEBUG  WindowsBackend: drive=Drive(C: hd 53071.84375 mb free ntfs)
09-29 00:33 DEBUG  WindowsBackend: drive=Drive(D: hd 449833.796875 mb free ntfs)
09-29 00:33 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 00:33 DEBUG  WindowsBackend: uninstaller_path=None
09-29 00:33 DEBUG  WindowsBackend: previous_target_dir=None
09-29 00:33 DEBUG  WindowsBackend: previous_distro_name=None
09-29 00:33 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 00:33 DEBUG  WindowsBackend: keyboard_layout=us
09-29 00:33 DEBUG  WindowsBackend: keyboard_variant=
09-29 00:33 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 00:33 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 00:33 DEBUG  WindowsBackend: total_memory_mb=4010.171875
09-29 00:33 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 00:33 DEBUG  Distro:   checking Ubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Ubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Kubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Kubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Xubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Xubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Mythbuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Mythbuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Edubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Edubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Lubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking Lubuntu ISO D:\DVD_ROM.iso
09-29 00:33 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:33 DEBUG  CommonBackend: Searching for local CDs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 INFO   root: Running the installer...
09-29 00:33 DEBUG  WindowsFrontend: __init__...
09-29 00:33 DEBUG  WindowsFrontend: on_init...
09-29 00:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\translations, languages=['en_US', 'en']
09-29 00:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\translations, languages=['en_US', 'en']
09-29 00:33 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=waqas
09-29 00:33 INFO   root: Received settings
09-29 00:33 DEBUG  CommonBackend: Searching for local CD
09-29 00:33 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylD873.tmp is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:33 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:33 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:33 DEBUG  CommonBackend: Searching for local ISO
09-29 00:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylD873.tmp\translations, languages=['en_US', 'en']
09-29 00:33 DEBUG  TaskList: # Running tasklist...
09-29 00:33 DEBUG  TaskList: ## Running select_target_dir...
09-29 00:33 ERROR  TaskList: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
09-29 00:33 DEBUG  TaskList: # Cancelling tasklist
09-29 00:33 DEBUG  TaskList: # Finished tasklist
09-29 00:33 ERROR  root: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into D:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
09-29 00:34 INFO   root: === wubi 12.04 rev266 ===
09-29 00:34 DEBUG  root: Logfile is c:\users\waqas\appdata\local\temp\wubi-12.04-rev266.log
09-29 00:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu-12.04-desktop-amd64\\wubi.exe"']
09-29 00:34 DEBUG  CommonBackend: data_dir=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\data
09-29 00:34 DEBUG  WindowsBackend: 7z=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\bin\7z.exe
09-29 00:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
09-29 00:34 DEBUG  CommonBackend: Fetching basic info...
09-29 00:34 DEBUG  CommonBackend: original_exe=D:\ubuntu-12.04-desktop-amd64\wubi.exe
09-29 00:34 DEBUG  CommonBackend: platform=win32
09-29 00:34 DEBUG  CommonBackend: osname=nt
09-29 00:34 DEBUG  CommonBackend: language=en_US
09-29 00:34 DEBUG  CommonBackend: encoding=cp1252
09-29 00:34 DEBUG  WindowsBackend: arch=amd64
09-29 00:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\data\isolist.ini
09-29 00:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-29 00:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-29 00:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
09-29 00:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-29 00:34 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-29 00:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-29 00:34 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
09-29 00:34 DEBUG  WindowsBackend: Fetching host info...
09-29 00:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-29 00:34 DEBUG  WindowsBackend: windows version=vista
09-29 00:34 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
09-29 00:34 DEBUG  WindowsBackend: windows_sp=None
09-29 00:34 DEBUG  WindowsBackend: windows_build=7601
09-29 00:34 DEBUG  WindowsBackend: gmt=4
09-29 00:34 DEBUG  WindowsBackend: country=US
09-29 00:34 DEBUG  WindowsBackend: timezone=America/New_York
09-29 00:34 DEBUG  WindowsBackend: windows_username=waqas
09-29 00:34 DEBUG  WindowsBackend: user_full_name=waqas
09-29 00:34 DEBUG  WindowsBackend: user_directory=C:\Users\waqas
09-29 00:34 DEBUG  WindowsBackend: windows_language_code=1033
09-29 00:34 DEBUG  WindowsBackend: windows_language=English
09-29 00:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
09-29 00:34 DEBUG  WindowsBackend: bootloader=vista
09-29 00:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 53076.0859375 mb free ntfs)
09-29 00:34 DEBUG  WindowsBackend: drive=Drive(C: hd 53076.0859375 mb free ntfs)
09-29 00:34 DEBUG  WindowsBackend: drive=Drive(D: hd 450534.121094 mb free ntfs)
09-29 00:34 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-29 00:34 DEBUG  WindowsBackend: uninstaller_path=None
09-29 00:34 DEBUG  WindowsBackend: previous_target_dir=None
09-29 00:34 DEBUG  WindowsBackend: previous_distro_name=None
09-29 00:34 DEBUG  WindowsBackend: keyboard_id=67699721
09-29 00:34 DEBUG  WindowsBackend: keyboard_layout=us
09-29 00:34 DEBUG  WindowsBackend: keyboard_variant=
09-29 00:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
09-29 00:34 DEBUG  CommonBackend: locale=en_US.UTF-8
09-29 00:34 DEBUG  WindowsBackend: total_memory_mb=4010.171875
09-29 00:34 DEBUG  CommonBackend: Searching ISOs on USB devices
09-29 00:34 DEBUG  Distro:   checking Ubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Ubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Kubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Kubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Xubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Xubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Mythbuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Mythbuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Edubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Edubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Lubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking Lubuntu ISO D:\DVD_ROM.iso
09-29 00:34 DEBUG  Distro:     does not contain casper\filesystem.squashfs
09-29 00:34 DEBUG  CommonBackend: Searching for local CDs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 INFO   root: Running the installer...
09-29 00:34 DEBUG  WindowsFrontend: __init__...
09-29 00:34 DEBUG  WindowsFrontend: on_init...
09-29 00:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\translations, languages=['en_US', 'en']
09-29 00:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\translations, languages=['en_US', 'en']
09-29 00:34 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=waqas
09-29 00:34 INFO   root: Received settings
09-29 00:34 DEBUG  CommonBackend: Searching for local CD
09-29 00:34 DEBUG  Distro:   checking whether C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-29 00:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-29 00:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-29 00:34 DEBUG  CommonBackend: Searching for local ISO
09-29 00:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\waqas\AppData\Local\Temp\pylB9DC.tmp\translations, languages=['en_US', 'en']
09-29 00:34 DEBUG  TaskList: # Running tasklist...
09-29 00:34 DEBUG  TaskList: ## Running select_target_dir...
09-29 00:34 INFO   WindowsBackend: Installing into D:\ubuntu
09-29 00:34 DEBUG  TaskList: ## Finished select_target_dir
09-29 00:34 DEBUG  TaskList: ## Running create_dir_structure...
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
09-29 00:34 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
09-29 00:34 DEBUG  TaskList: ## Finished create_dir_structure
09-29 00:34 DEBUG  TaskList: ## Running create_uninstaller...
09-29 00:34 DEBUG  WindowsBackend: Copying uninstaller D:\ubuntu-12.04-desktop-amd64\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev266
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-29 00:34 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-29 00:34 DEBUG  TaskList: ## Finished create_uninstaller
09-29 00:34 DEBUG  TaskList: ## Running create_preseed_diskimage...
09-29 00:34 DEBUG  TaskList: ## Finished create_preseed_diskimage
09-29 00:34 DEBUG  TaskList: ## Running get_diskimage...
09-29 00:34 DEBUG  TaskList: New task download
09-29 00:34 DEBUG  TaskList: ### Running download...
09-29 00:34 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04/ubuntu-12.04-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-12.04-wubi-amd64.tar.xz
09-29 00:34 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 00:34 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-29 00:34 DEBUG  TaskList: ### Finished download
09-29 00:34 DEBUG  TaskList: New task download
09-29 00:34 DEBUG  TaskList: ### Running download...
09-29 00:34 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz](http://cdimage.ubuntu.com/wubi/current/amd64.tar.xz) > D:\ubuntu\disks\amd64.tar.xz
09-29 00:34 ERROR  TaskList: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\downloader.py", line 77, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1188, in _make_request
URLGrabError: [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-29 00:34 ERROR  TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download
09-29 00:34 DEBUG  TaskList: ### Finished download
09-29 00:34 ERROR  TaskList: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files
09-29 00:34 DEBUG  TaskList: # Cancelling tasklist
09-29 00:34 DEBUG  TaskList: # Finished tasklist
09-29 00:34 ERROR  root: Could not retrieve the required disk image files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 592, in get_diskimage
Exception: Could not retrieve the required disk image files

---

### Post by bcbc on 2012-09-28
It failed to download the disk image
> 09-29 00:34 ERROR TaskList: Non fatal error [Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')> in task download


Make sure you're connected to the internet.

EDIT: actually, scrap that, you're using an old version of Wubi. Get the latest and that will work better (your URLs are wrong).

---

### Post by AndreiQC on 2012-09-28
Yes that only one point of all his installation error. I don't think that a single download problem can be the source of an internet issue. In my point of view i begin to thing that Windows 64bits and Ubuntu doesn't work fit together i had the same experience. 

In the past few years it was easy to have ubuntu running in windows, i don't remember if it was wubi but one thing i know is that it was ways up easier to make it work than today. I didn't see positive point or post telling that wubi is working under Windows 7 64 bits edition. 

I'm almost sure that there is no issue making it work.

---

### Post by bcbc on 2012-09-28
What's happening is:
1. running wubi.exe from a mounted or extracted ISO CD image
2. wubi.exe doesn't detect the ISO and goes to the net to download the image
3. the ISO is old (12.04 instead of 12.04.1) which means that wubi.exe is old and the url's don't exist anymore
4. wubi fails to find the the download.

It's not magic. It's not pretty. It's wubi.

---

### Post by waqas300 on 2012-09-29
Thanks guys. i have connected to the internet now i can install it. Actually it was downloading ubuntu from the internet. i have the complete setup but wonder why its downloading again. The problem doesnt exist in windows 32 bit along with ubuntu 32 bit.

---

