---
title: "[wubi] wubi install problems windows 8 log attached"
date: 2013-05-24
forum: Installation &amp; Upgrades
---

### Post by jbyeung on 2013-05-24
hi guys, having issues installing via wubi for some reason.  should add i had previously installed 12.04 lts via wubi with no problems, only to have it borked from some update or something... uninstalled via wubi thru windows 8, trying to reinstall.  spent the better part of the day with no luck.

wubi completes but has an error at the very end everytime.

I should add that I have no cd drive on this laptop because I swapped it out for an ssd, and this sony vaio sa cannot boot from usb for some reason.

log follows:

05-09 01:04 INFO   root: === wubi 12.04 rev272 ===
05-09 01:04 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-09 01:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\JBYEU_~1\\AppData\\Local\\Temp\\7zOF84.tmp\\wubi.exe"']
05-09 01:04 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\data
05-09 01:04 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\bin\7z.exe
05-09 01:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 01:04 DEBUG  CommonBackend: Fetching basic info...
05-09 01:04 DEBUG  CommonBackend: original_exe=C:\Users\JBYEU_~1\AppData\Local\Temp\7zOF84.tmp\wubi.exe
05-09 01:04 DEBUG  CommonBackend: platform=win32
05-09 01:04 DEBUG  CommonBackend: osname=nt
05-09 01:04 DEBUG  CommonBackend: language=en_US
05-09 01:04 DEBUG  CommonBackend: encoding=cp1252
05-09 01:04 DEBUG  WindowsBackend: arch=amd64
05-09 01:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\data\isolist.ini
05-09 01:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 01:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 01:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-09 01:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 01:04 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 01:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 01:04 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-09 01:04 DEBUG  WindowsBackend: Fetching host info...
05-09 01:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 01:04 DEBUG  WindowsBackend: windows version=vista
05-09 01:04 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-09 01:04 DEBUG  WindowsBackend: windows_sp=None
05-09 01:04 DEBUG  WindowsBackend: windows_build=9200
05-09 01:04 DEBUG  WindowsBackend: gmt=-5
05-09 01:04 DEBUG  WindowsBackend: country=US
05-09 01:04 DEBUG  WindowsBackend: timezone=America/New_York
05-09 01:04 DEBUG  WindowsBackend: windows_username=Jeffrey
05-09 01:04 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-09 01:04 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-09 01:04 DEBUG  WindowsBackend: windows_language_code=1033
05-09 01:04 DEBUG  WindowsBackend: windows_language=English
05-09 01:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-09 01:04 DEBUG  WindowsBackend: bootloader=vista
05-09 01:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 44375.1601563 mb free ntfs)
05-09 01:04 DEBUG  WindowsBackend: drive=Drive(C: hd 44375.1601563 mb free ntfs)
05-09 01:04 DEBUG  WindowsBackend: drive=Drive(D: hd 68.046875 mb free ntfs)
05-09 01:04 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-09 01:04 DEBUG  WindowsBackend: uninstaller_path=None
05-09 01:04 DEBUG  WindowsBackend: previous_target_dir=None
05-09 01:04 DEBUG  WindowsBackend: previous_distro_name=None
05-09 01:04 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 01:04 DEBUG  WindowsBackend: keyboard_layout=us
05-09 01:04 DEBUG  WindowsBackend: keyboard_variant=
05-09 01:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-09 01:04 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 01:04 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-09 01:04 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 01:04 DEBUG  CommonBackend: Searching for local CDs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 INFO   root: Running the installer...
05-09 01:04 DEBUG  WindowsFrontend: __init__...
05-09 01:04 DEBUG  WindowsFrontend: on_init...
05-09 01:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\translations, languages=['en_US', 'en']
05-09 01:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\translations, languages=['en_US', 'en']
05-09 01:04 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-09 01:04 INFO   root: Received settings
05-09 01:04 DEBUG  CommonBackend: Searching for local CD
05-09 01:04 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:04 DEBUG  CommonBackend: Searching for local ISO
05-09 01:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl108E.tmp\translations, languages=['en_US', 'en']
05-09 01:04 DEBUG  TaskList: # Running tasklist...
05-09 01:04 DEBUG  TaskList: ## Running select_target_dir...
05-09 01:04 INFO   WindowsBackend: Installing into F:\ubuntu
05-09 01:04 DEBUG  TaskList: ## Finished select_target_dir
05-09 01:04 DEBUG  TaskList: ## Running create_dir_structure...
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
05-09 01:04 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
05-09 01:04 DEBUG  TaskList: ## Finished create_dir_structure
05-09 01:04 DEBUG  TaskList: ## Running create_uninstaller...
05-09 01:04 DEBUG  WindowsBackend: Copying uninstaller C:\Users\JBYEU_~1\AppData\Local\Temp\7zOF84.tmp\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
05-09 01:04 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\Users\\JBYEU_~1\\AppData\\Local\\Temp\\7zOF84.tmp\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\JBYEU_~1\\AppData\\Local\\Temp\\7zOF84.tmp\\wubi.exe'
05-09 01:04 DEBUG  TaskList: # Cancelling tasklist
05-09 01:04 DEBUG  TaskList: # Finished tasklist
05-09 01:04 ERROR  root: [Errno 2] No such file or directory: 'C:\\Users\\JBYEU_~1\\AppData\\Local\\Temp\\7zOF84.tmp\\wubi.exe'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 116, in create_uninstaller
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\Users\\JBYEU_~1\\AppData\\Local\\Temp\\7zOF84.tmp\\wubi.exe'
05-09 01:06 INFO   root: === wubi 12.04 rev272 ===
05-09 01:06 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-09 01:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Dropbox\\Install files\\ubuntu-12.04.2-desktop-amd64\\wubi.exe"']
05-09 01:06 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\data
05-09 01:06 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\bin\7z.exe
05-09 01:06 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 01:06 DEBUG  CommonBackend: Fetching basic info...
05-09 01:06 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Dropbox\Install files\ubuntu-12.04.2-desktop-amd64\wubi.exe
05-09 01:06 DEBUG  CommonBackend: platform=win32
05-09 01:06 DEBUG  CommonBackend: osname=nt
05-09 01:06 DEBUG  CommonBackend: language=en_US
05-09 01:06 DEBUG  CommonBackend: encoding=cp1252
05-09 01:06 DEBUG  WindowsBackend: arch=amd64
05-09 01:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\data\isolist.ini
05-09 01:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-09 01:06 DEBUG  WindowsBackend: Fetching host info...
05-09 01:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 01:06 DEBUG  WindowsBackend: windows version=vista
05-09 01:06 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-09 01:06 DEBUG  WindowsBackend: windows_sp=None
05-09 01:06 DEBUG  WindowsBackend: windows_build=9200
05-09 01:06 DEBUG  WindowsBackend: gmt=-5
05-09 01:06 DEBUG  WindowsBackend: country=US
05-09 01:06 DEBUG  WindowsBackend: timezone=America/New_York
05-09 01:06 DEBUG  WindowsBackend: windows_username=Jeffrey
05-09 01:06 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-09 01:06 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-09 01:06 DEBUG  WindowsBackend: windows_language_code=1033
05-09 01:06 DEBUG  WindowsBackend: windows_language=English
05-09 01:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-09 01:06 DEBUG  WindowsBackend: bootloader=vista
05-09 01:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43684.4296875 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(C: hd 43684.4296875 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(D: hd 68.046875 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: uninstaller_path=None
05-09 01:06 DEBUG  WindowsBackend: previous_target_dir=None
05-09 01:06 DEBUG  WindowsBackend: previous_distro_name=None
05-09 01:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 01:06 DEBUG  WindowsBackend: keyboard_layout=us
05-09 01:06 DEBUG  WindowsBackend: keyboard_variant=
05-09 01:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-09 01:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 01:06 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-09 01:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 01:06 DEBUG  CommonBackend: Searching for local CDs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 INFO   root: Running the installer...
05-09 01:06 DEBUG  WindowsFrontend: __init__...
05-09 01:06 DEBUG  WindowsFrontend: on_init...
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\translations, languages=['en_US', 'en']
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\translations, languages=['en_US', 'en']
05-09 01:06 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-09 01:06 INFO   root: Received settings
05-09 01:06 DEBUG  CommonBackend: Searching for local CD
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  CommonBackend: Searching for local ISO
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylF432.tmp\translations, languages=['en_US', 'en']
05-09 01:06 DEBUG  TaskList: # Running tasklist...
05-09 01:06 DEBUG  TaskList: ## Running select_target_dir...
05-09 01:06 ERROR  TaskList: Cannot install into F:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into F:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
05-09 01:06 DEBUG  TaskList: # Cancelling tasklist
05-09 01:06 DEBUG  TaskList: # Finished tasklist
05-09 01:06 ERROR  root: Cannot install into F:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 81, in select_target_dir
Exception: Cannot install into F:\ubuntu.
There is another file or directory with this name.
Please remove it before continuing.
05-09 01:06 INFO   root: === wubi 12.04 rev272 ===
05-09 01:06 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-09 01:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Dropbox\\Install files\\ubuntu-12.04.2-desktop-amd64\\wubi.exe"']
05-09 01:06 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\data
05-09 01:06 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\bin\7z.exe
05-09 01:06 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-09 01:06 DEBUG  CommonBackend: Fetching basic info...
05-09 01:06 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Dropbox\Install files\ubuntu-12.04.2-desktop-amd64\wubi.exe
05-09 01:06 DEBUG  CommonBackend: platform=win32
05-09 01:06 DEBUG  CommonBackend: osname=nt
05-09 01:06 DEBUG  CommonBackend: language=en_US
05-09 01:06 DEBUG  CommonBackend: encoding=cp1252
05-09 01:06 DEBUG  WindowsBackend: arch=amd64
05-09 01:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\data\isolist.ini
05-09 01:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-09 01:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-09 01:06 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-09 01:06 DEBUG  WindowsBackend: Fetching host info...
05-09 01:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-09 01:06 DEBUG  WindowsBackend: windows version=vista
05-09 01:06 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-09 01:06 DEBUG  WindowsBackend: windows_sp=None
05-09 01:06 DEBUG  WindowsBackend: windows_build=9200
05-09 01:06 DEBUG  WindowsBackend: gmt=-5
05-09 01:06 DEBUG  WindowsBackend: country=US
05-09 01:06 DEBUG  WindowsBackend: timezone=America/New_York
05-09 01:06 DEBUG  WindowsBackend: windows_username=Jeffrey
05-09 01:06 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-09 01:06 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-09 01:06 DEBUG  WindowsBackend: windows_language_code=1033
05-09 01:06 DEBUG  WindowsBackend: windows_language=English
05-09 01:06 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-09 01:06 DEBUG  WindowsBackend: bootloader=vista
05-09 01:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43680.9023438 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(C: hd 43680.9023438 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(D: hd 68.046875 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-09 01:06 DEBUG  WindowsBackend: uninstaller_path=None
05-09 01:06 DEBUG  WindowsBackend: previous_target_dir=None
05-09 01:06 DEBUG  WindowsBackend: previous_distro_name=None
05-09 01:06 DEBUG  WindowsBackend: keyboard_id=67699721
05-09 01:06 DEBUG  WindowsBackend: keyboard_layout=us
05-09 01:06 DEBUG  WindowsBackend: keyboard_variant=
05-09 01:06 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-09 01:06 DEBUG  CommonBackend: locale=en_US.UTF-8
05-09 01:06 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-09 01:06 DEBUG  CommonBackend: Searching ISOs on USB devices
05-09 01:06 DEBUG  CommonBackend: Searching for local CDs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 INFO   root: Running the installer...
05-09 01:06 DEBUG  WindowsFrontend: __init__...
05-09 01:06 DEBUG  WindowsFrontend: on_init...
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\translations, languages=['en_US', 'en']
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\translations, languages=['en_US', 'en']
05-09 01:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-09 01:06 INFO   root: Received settings
05-09 01:06 DEBUG  CommonBackend: Searching for local CD
05-09 01:06 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-09 01:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-09 01:06 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-09 01:06 DEBUG  CommonBackend: Searching for local ISO
05-09 01:06 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\translations, languages=['en_US', 'en']
05-09 01:06 DEBUG  TaskList: # Running tasklist...
05-09 01:06 DEBUG  TaskList: ## Running select_target_dir...
05-09 01:06 INFO   WindowsBackend: Installing into C:\ubuntu
05-09 01:06 DEBUG  TaskList: ## Finished select_target_dir
05-09 01:06 DEBUG  TaskList: ## Running create_dir_structure...
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-09 01:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-09 01:06 DEBUG  TaskList: ## Finished create_dir_structure
05-09 01:06 DEBUG  TaskList: ## Running create_uninstaller...
05-09 01:06 DEBUG  WindowsBackend: Copying uninstaller C:\Users\jbyeu_000\Dropbox\Install files\ubuntu-12.04.2-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-09 01:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-09 01:06 DEBUG  TaskList: ## Finished create_uninstaller
05-09 01:06 DEBUG  TaskList: ## Running create_preseed_diskimage...
05-09 01:06 DEBUG  TaskList: ## Finished create_preseed_diskimage
05-09 01:06 DEBUG  TaskList: ## Running get_diskimage...
05-09 01:06 DEBUG  TaskList: New task download
05-09 01:06 DEBUG  TaskList: ### Running download...
05-09 01:06 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
05-09 01:06 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
05-09 01:13 DEBUG  TaskList: ### Finished download
05-09 01:13 DEBUG  downloader: download finished (read 549666608 bytes)
05-09 01:13 DEBUG  TaskList: ## Finished get_diskimage
05-09 01:13 DEBUG  TaskList: ## Running extract_diskimage...
05-09 01:14 DEBUG  TaskList: ## Finished extract_diskimage
05-09 01:14 DEBUG  TaskList: ## Running choose_disk_sizes...
05-09 01:14 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
05-09 01:14 DEBUG  TaskList: ## Finished choose_disk_sizes
05-09 01:14 DEBUG  TaskList: ## Running expand_diskimage...
05-09 01:15 DEBUG  TaskList: ## Finished expand_diskimage
05-09 01:15 DEBUG  TaskList: ## Running create_swap_diskimage...
05-09 01:15 DEBUG  TaskList: ## Finished create_swap_diskimage
05-09 01:15 DEBUG  TaskList: ## Running modify_bootloader...
05-09 01:15 DEBUG  TaskList: New task modify_bcd
05-09 01:15 DEBUG  TaskList: ### Running modify_bcd...
05-09 01:15 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 43680.9023438 mb free ntfs)
05-09 01:15 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive {4856c31d-9dfb-11e0-8d87-fecf882cd189}
05-09 01:15 DEBUG  TaskList: ### Finished modify_bcd
05-09 01:15 DEBUG  TaskList: New task modify_bcd
05-09 01:15 DEBUG  TaskList: ### Running modify_bcd...
05-09 01:15 DEBUG  WindowsBackend: modify_bcd Drive(D: hd 68.046875 mb free ntfs)
05-09 01:15 DEBUG  WindowsBackend: BCD has already been modified
05-09 01:15 DEBUG  TaskList: ### Finished modify_bcd
05-09 01:15 DEBUG  TaskList: New task modify_bcd
05-09 01:15 DEBUG  TaskList: ### Running modify_bcd...
05-09 01:15 DEBUG  WindowsBackend: modify_bcd Drive(F: hd 268134.824219 mb free ntfs)
05-09 01:15 DEBUG  WindowsBackend: BCD has already been modified
05-09 01:15 DEBUG  TaskList: ### Finished modify_bcd
05-09 01:15 DEBUG  TaskList: ## Finished modify_bootloader
05-09 01:15 DEBUG  TaskList: ## Running diskimage_bootloader...
05-09 01:15 DEBUG  WindowsBackend: Copying C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\winboot -> C:\ubuntu\winboot
05-09 01:15 DEBUG  TaskList: ## Finished diskimage_bootloader
05-09 01:15 DEBUG  TaskList: # Finished tasklist
05-09 01:15 INFO   root: Almost finished installing
05-09 01:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl56E4.tmp\translations, languages=['en_US', 'en']
05-09 01:39 INFO   root: Finished installation
05-09 01:39 INFO   root: Rebooting
05-09 01:39 DEBUG  TaskList: # Running tasklist...
05-09 01:39 DEBUG  TaskList: ## Running reboot...
05-09 01:39 DEBUG  TaskList: ## Finished reboot
05-09 01:39 DEBUG  TaskList: # Finished tasklist
05-09 01:39 DEBUG  root: application.quit
05-09 01:39 DEBUG  WindowsFrontend: frontend.quit
05-09 01:39 DEBUG  WindowsFrontend: frontend.on_quit
05-09 01:39 DEBUG  root: application.on_quit
05-09 01:39 INFO   root: sys.exit
05-24 13:39 INFO   root: === wubi 12.04 rev272 ===
05-24 13:39 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 13:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
05-24 13:39 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\data
05-24 13:39 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\bin\7z.exe
05-24 13:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 13:39 DEBUG  CommonBackend: Fetching basic info...
05-24 13:39 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-24 13:39 DEBUG  CommonBackend: platform=win32
05-24 13:39 DEBUG  CommonBackend: osname=nt
05-24 13:39 DEBUG  CommonBackend: language=en_US
05-24 13:39 DEBUG  CommonBackend: encoding=cp1252
05-24 13:39 DEBUG  WindowsBackend: arch=amd64
05-24 13:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\data\isolist.ini
05-24 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 13:39 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 13:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 13:39 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 13:39 DEBUG  WindowsBackend: Fetching host info...
05-24 13:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 13:39 DEBUG  WindowsBackend: windows version=vista
05-24 13:39 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 13:39 DEBUG  WindowsBackend: windows_sp=None
05-24 13:39 DEBUG  WindowsBackend: windows_build=9200
05-24 13:39 DEBUG  WindowsBackend: gmt=-5
05-24 13:39 DEBUG  WindowsBackend: country=US
05-24 13:39 DEBUG  WindowsBackend: timezone=America/New_York
05-24 13:39 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 13:39 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 13:39 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 13:39 DEBUG  WindowsBackend: windows_language_code=1033
05-24 13:39 DEBUG  WindowsBackend: windows_language=English
05-24 13:39 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 13:39 DEBUG  WindowsBackend: bootloader=vista
05-24 13:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 14414.3828125 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: drive=Drive(C: hd 14414.3867188 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: drive=Drive(D: hd 67.64453125 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.691406 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-24 13:39 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-24 13:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-24 13:39 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 13:39 DEBUG  WindowsBackend: keyboard_layout=us
05-24 13:39 DEBUG  WindowsBackend: keyboard_variant=
05-24 13:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 13:39 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 13:39 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 13:39 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 13:39 DEBUG  CommonBackend: Searching for local CDs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 13:39 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 13:39 INFO   root: Running the uninstaller...
05-24 13:39 INFO   CommonBackend: This is the uninstaller running
05-24 13:39 DEBUG  WindowsFrontend: __init__...
05-24 13:39 DEBUG  WindowsFrontend: on_init...
05-24 13:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\translations, languages=['en_US', 'en']
05-24 13:39 INFO   root: Received settings
05-24 13:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\translations, languages=['en_US', 'en']
05-24 13:39 DEBUG  TaskList: # Running tasklist...
05-24 13:39 DEBUG  TaskList: ## Running Remove bootloader entry...
05-24 13:39 DEBUG  WindowsBackend: Removing bcd entry {4856c31d-9dfb-11e0-8d87-fecf882cd189}
05-24 13:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi VistaBootDrive 
05-24 13:39 DEBUG  WindowsBackend: undo_bootini C:
05-24 13:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 14414.3867188 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: undo_bootini D:
05-24 13:39 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 67.64453125 mb free ntfs)
05-24 13:39 DEBUG  WindowsBackend: undo_bootini F:
05-24 13:39 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 268134.691406 mb free ntfs)
05-24 13:39 DEBUG  TaskList: ## Finished Remove bootloader entry
05-24 13:39 DEBUG  TaskList: ## Running Remove target dir...
05-24 13:39 DEBUG  CommonBackend: Deleting C:\ubuntu
05-24 13:39 DEBUG  TaskList: ## Finished Remove target dir
05-24 13:39 DEBUG  TaskList: ## Running Remove registry key...
05-24 13:39 DEBUG  TaskList: ## Finished Remove registry key
05-24 13:39 DEBUG  TaskList: # Finished tasklist
05-24 13:39 INFO   root: Almost finished uninstalling
05-24 13:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylDE1.tmp\translations, languages=['en_US', 'en']
05-24 13:39 INFO   root: Finished uninstallation
05-24 13:39 DEBUG  root: application.quit
05-24 13:39 DEBUG  WindowsFrontend: frontend.quit
05-24 13:39 DEBUG  WindowsFrontend: frontend.on_quit
05-24 13:39 DEBUG  root: application.on_quit
05-24 13:39 INFO   root: sys.exit
05-24 14:14 INFO   root: === wubi 12.04 rev272 ===
05-24 14:14 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 14:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Downloads\\ubuntu-12.04.2-desktop-amd64\\wubi.exe"']
05-24 14:14 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\data
05-24 14:14 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\bin\7z.exe
05-24 14:14 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 14:14 DEBUG  CommonBackend: Fetching basic info...
05-24 14:14 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Downloads\ubuntu-12.04.2-desktop-amd64\wubi.exe
05-24 14:14 DEBUG  CommonBackend: platform=win32
05-24 14:14 DEBUG  CommonBackend: osname=nt
05-24 14:14 DEBUG  CommonBackend: language=en_US
05-24 14:14 DEBUG  CommonBackend: encoding=cp1252
05-24 14:14 DEBUG  WindowsBackend: arch=amd64
05-24 14:14 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\data\isolist.ini
05-24 14:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 14:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 14:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 14:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 14:14 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 14:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 14:14 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 14:14 DEBUG  WindowsBackend: Fetching host info...
05-24 14:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 14:14 DEBUG  WindowsBackend: windows version=vista
05-24 14:14 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 14:14 DEBUG  WindowsBackend: windows_sp=None
05-24 14:14 DEBUG  WindowsBackend: windows_build=9200
05-24 14:14 DEBUG  WindowsBackend: gmt=-5
05-24 14:14 DEBUG  WindowsBackend: country=US
05-24 14:14 DEBUG  WindowsBackend: timezone=America/New_York
05-24 14:14 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 14:14 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 14:14 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 14:14 DEBUG  WindowsBackend: windows_language_code=1033
05-24 14:14 DEBUG  WindowsBackend: windows_language=English
05-24 14:14 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 14:14 DEBUG  WindowsBackend: bootloader=vista
05-24 14:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43980.703125 mb free ntfs)
05-24 14:14 DEBUG  WindowsBackend: drive=Drive(C: hd 43980.703125 mb free ntfs)
05-24 14:14 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:14 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-24 14:14 DEBUG  WindowsBackend: uninstaller_path=None
05-24 14:14 DEBUG  WindowsBackend: previous_target_dir=None
05-24 14:14 DEBUG  WindowsBackend: previous_distro_name=None
05-24 14:14 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 14:14 DEBUG  WindowsBackend: keyboard_layout=us
05-24 14:14 DEBUG  WindowsBackend: keyboard_variant=
05-24 14:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 14:14 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 14:14 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 14:14 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 14:14 DEBUG  CommonBackend: Searching for local CDs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:14 INFO   root: Running the installer...
05-24 14:14 DEBUG  WindowsFrontend: __init__...
05-24 14:14 DEBUG  WindowsFrontend: on_init...
05-24 14:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\translations, languages=['en_US', 'en']
05-24 14:14 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl46EB.tmp\translations, languages=['en_US', 'en']
05-24 14:14 INFO   WindowsFrontend: Operation cancelled
05-24 14:14 DEBUG  WindowsFrontend: frontend.quit
05-24 14:14 DEBUG  WindowsFrontend: frontend.on_quit
05-24 14:14 DEBUG  root: application.on_quit
05-24 14:14 INFO   root: sys.exit
05-24 14:25 INFO   root: === wubi 12.04 rev272 ===
05-24 14:25 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 14:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Downloads\\ubuntu-12.04.2-desktop-amd64\\wubi.exe"']
05-24 14:25 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\data
05-24 14:25 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\bin\7z.exe
05-24 14:25 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 14:25 DEBUG  CommonBackend: Fetching basic info...
05-24 14:25 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Downloads\ubuntu-12.04.2-desktop-amd64\wubi.exe
05-24 14:25 DEBUG  CommonBackend: platform=win32
05-24 14:25 DEBUG  CommonBackend: osname=nt
05-24 14:25 DEBUG  CommonBackend: language=en_US
05-24 14:25 DEBUG  CommonBackend: encoding=cp1252
05-24 14:25 DEBUG  WindowsBackend: arch=amd64
05-24 14:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\data\isolist.ini
05-24 14:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 14:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 14:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 14:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 14:25 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 14:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 14:25 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 14:25 DEBUG  WindowsBackend: Fetching host info...
05-24 14:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 14:25 DEBUG  WindowsBackend: windows version=vista
05-24 14:25 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 14:25 DEBUG  WindowsBackend: windows_sp=None
05-24 14:25 DEBUG  WindowsBackend: windows_build=9200
05-24 14:25 DEBUG  WindowsBackend: gmt=-5
05-24 14:25 DEBUG  WindowsBackend: country=US
05-24 14:25 DEBUG  WindowsBackend: timezone=America/New_York
05-24 14:25 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 14:25 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 14:25 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 14:25 DEBUG  WindowsBackend: windows_language_code=1033
05-24 14:25 DEBUG  WindowsBackend: windows_language=English
05-24 14:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 14:25 DEBUG  WindowsBackend: bootloader=vista
05-24 14:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 45616.5664063 mb free ntfs)
05-24 14:25 DEBUG  WindowsBackend: drive=Drive(C: hd 45616.5664063 mb free ntfs)
05-24 14:25 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:25 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-24 14:25 DEBUG  WindowsBackend: uninstaller_path=None
05-24 14:25 DEBUG  WindowsBackend: previous_target_dir=None
05-24 14:25 DEBUG  WindowsBackend: previous_distro_name=None
05-24 14:25 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 14:25 DEBUG  WindowsBackend: keyboard_layout=us
05-24 14:25 DEBUG  WindowsBackend: keyboard_variant=
05-24 14:25 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 14:25 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 14:25 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 14:25 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 14:25 DEBUG  CommonBackend: Searching for local CDs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:25 INFO   root: Running the installer...
05-24 14:25 DEBUG  WindowsFrontend: __init__...
05-24 14:25 DEBUG  WindowsFrontend: on_init...
05-24 14:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\translations, languages=['en_US', 'en']
05-24 14:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\translations, languages=['en_US', 'en']
05-24 14:26 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-24 14:26 INFO   root: Received settings
05-24 14:26 DEBUG  CommonBackend: Searching for local CD
05-24 14:26 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp is a valid Ubuntu CD
05-24 14:26 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\casper\filesystem.squashfs
05-24 14:26 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:26 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:26 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:26 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:26 DEBUG  CommonBackend: Searching for local ISO
05-24 14:26 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl3534.tmp\translations, languages=['en_US', 'en']
05-24 14:26 DEBUG  TaskList: # Running tasklist...
05-24 14:26 DEBUG  TaskList: ## Running select_target_dir...
05-24 14:26 INFO   WindowsBackend: Installing into F:\ubuntu
05-24 14:26 DEBUG  TaskList: ## Finished select_target_dir
05-24 14:26 DEBUG  TaskList: ## Running create_dir_structure...
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
05-24 14:26 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
05-24 14:26 DEBUG  TaskList: ## Finished create_dir_structure
05-24 14:26 DEBUG  TaskList: ## Running create_uninstaller...
05-24 14:26 DEBUG  WindowsBackend: Copying uninstaller C:\Users\jbyeu_000\Downloads\ubuntu-12.04.2-desktop-amd64\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-24 14:26 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-24 14:26 DEBUG  TaskList: ## Finished create_uninstaller
05-24 14:26 DEBUG  TaskList: ## Running create_preseed_diskimage...
05-24 14:26 DEBUG  TaskList: ## Finished create_preseed_diskimage
05-24 14:26 DEBUG  TaskList: ## Running get_diskimage...
05-24 14:26 DEBUG  TaskList: New task download
05-24 14:26 DEBUG  TaskList: ### Running download...
05-24 14:26 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > F:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
05-24 14:26 DEBUG  downloader: Download start filename=F:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
05-24 14:33 DEBUG  downloader: download finished (read 549663688 bytes)
05-24 14:33 DEBUG  TaskList: ### Finished download
05-24 14:33 DEBUG  TaskList: ## Finished get_diskimage
05-24 14:33 DEBUG  TaskList: ## Running extract_diskimage...
05-24 14:33 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
05-24 14:33 DEBUG  TaskList: # Cancelling tasklist
05-24 14:33 DEBUG  TaskList: # Finished tasklist
05-24 14:33 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
05-24 14:34 INFO   root: === wubi 12.04 rev272 ===
05-24 14:34 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 14:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\ubuntu\\uninstall-wubi.exe"']
05-24 14:34 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\data
05-24 14:34 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\bin\7z.exe
05-24 14:34 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 14:34 DEBUG  CommonBackend: Fetching basic info...
05-24 14:34 DEBUG  CommonBackend: original_exe=F:\ubuntu\uninstall-wubi.exe
05-24 14:34 DEBUG  CommonBackend: platform=win32
05-24 14:34 DEBUG  CommonBackend: osname=nt
05-24 14:34 DEBUG  CommonBackend: language=en_US
05-24 14:34 DEBUG  CommonBackend: encoding=cp1252
05-24 14:34 DEBUG  WindowsBackend: arch=amd64
05-24 14:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\data\isolist.ini
05-24 14:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 14:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 14:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 14:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 14:34 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 14:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 14:34 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 14:34 DEBUG  WindowsBackend: Fetching host info...
05-24 14:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 14:34 DEBUG  WindowsBackend: windows version=vista
05-24 14:34 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 14:34 DEBUG  WindowsBackend: windows_sp=None
05-24 14:34 DEBUG  WindowsBackend: windows_build=9200
05-24 14:34 DEBUG  WindowsBackend: gmt=-5
05-24 14:34 DEBUG  WindowsBackend: country=US
05-24 14:34 DEBUG  WindowsBackend: timezone=America/New_York
05-24 14:34 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 14:34 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 14:34 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 14:34 DEBUG  WindowsBackend: windows_language_code=1033
05-24 14:34 DEBUG  WindowsBackend: windows_language=English
05-24 14:34 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 14:34 DEBUG  WindowsBackend: bootloader=vista
05-24 14:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 45593.578125 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: drive=Drive(C: hd 45593.578125 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: drive=Drive(F: hd 267102.015625 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
05-24 14:34 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
05-24 14:34 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-24 14:34 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 14:34 DEBUG  WindowsBackend: keyboard_layout=us
05-24 14:34 DEBUG  WindowsBackend: keyboard_variant=
05-24 14:34 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 14:34 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 14:34 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 14:34 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 14:34 DEBUG  CommonBackend: Searching for local CDs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:34 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:34 INFO   root: Running the uninstaller...
05-24 14:34 INFO   CommonBackend: This is the uninstaller running
05-24 14:34 DEBUG  WindowsFrontend: __init__...
05-24 14:34 DEBUG  WindowsFrontend: on_init...
05-24 14:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\translations, languages=['en_US', 'en']
05-24 14:34 INFO   root: Received settings
05-24 14:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\translations, languages=['en_US', 'en']
05-24 14:34 DEBUG  TaskList: # Running tasklist...
05-24 14:34 DEBUG  TaskList: ## Running Remove bootloader entry...
05-24 14:34 DEBUG  WindowsBackend: Could not find bcd id
05-24 14:34 DEBUG  WindowsBackend: undo_bootini C:
05-24 14:34 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 45593.578125 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: undo_bootini D:
05-24 14:34 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:34 DEBUG  WindowsBackend: undo_bootini F:
05-24 14:34 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 267102.015625 mb free ntfs)
05-24 14:34 DEBUG  TaskList: ## Finished Remove bootloader entry
05-24 14:34 DEBUG  TaskList: ## Running Remove target dir...
05-24 14:34 DEBUG  CommonBackend: Deleting F:\ubuntu
05-24 14:34 DEBUG  TaskList: ## Finished Remove target dir
05-24 14:34 DEBUG  TaskList: ## Running Remove registry key...
05-24 14:34 DEBUG  TaskList: ## Finished Remove registry key
05-24 14:34 DEBUG  TaskList: # Finished tasklist
05-24 14:34 INFO   root: Almost finished uninstalling
05-24 14:34 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylAACF.tmp\translations, languages=['en_US', 'en']
05-24 14:34 INFO   root: Finished uninstallation
05-24 14:34 DEBUG  root: application.quit
05-24 14:34 DEBUG  WindowsFrontend: frontend.quit
05-24 14:34 DEBUG  WindowsFrontend: frontend.on_quit
05-24 14:34 DEBUG  root: application.on_quit
05-24 14:34 INFO   root: sys.exit
05-24 14:36 INFO   root: === wubi 12.04 rev272 ===
05-24 14:36 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 14:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Downloads\\wubi.exe"']
05-24 14:36 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\data
05-24 14:36 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\bin\7z.exe
05-24 14:36 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 14:36 DEBUG  CommonBackend: Fetching basic info...
05-24 14:36 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Downloads\wubi.exe
05-24 14:36 DEBUG  CommonBackend: platform=win32
05-24 14:36 DEBUG  CommonBackend: osname=nt
05-24 14:36 DEBUG  CommonBackend: language=en_US
05-24 14:36 DEBUG  CommonBackend: encoding=cp1252
05-24 14:36 DEBUG  WindowsBackend: arch=amd64
05-24 14:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\data\isolist.ini
05-24 14:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 14:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 14:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 14:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 14:36 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 14:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 14:36 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 14:36 DEBUG  WindowsBackend: Fetching host info...
05-24 14:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 14:36 DEBUG  WindowsBackend: windows version=vista
05-24 14:36 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 14:36 DEBUG  WindowsBackend: windows_sp=None
05-24 14:36 DEBUG  WindowsBackend: windows_build=9200
05-24 14:36 DEBUG  WindowsBackend: gmt=-5
05-24 14:36 DEBUG  WindowsBackend: country=US
05-24 14:36 DEBUG  WindowsBackend: timezone=America/New_York
05-24 14:36 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 14:36 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 14:36 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 14:36 DEBUG  WindowsBackend: windows_language_code=1033
05-24 14:36 DEBUG  WindowsBackend: windows_language=English
05-24 14:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 14:36 DEBUG  WindowsBackend: bootloader=vista
05-24 14:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46289.7773438 mb free ntfs)
05-24 14:36 DEBUG  WindowsBackend: drive=Drive(C: hd 46289.7773438 mb free ntfs)
05-24 14:36 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:36 DEBUG  WindowsBackend: drive=Drive(F: hd 268134.824219 mb free ntfs)
05-24 14:36 DEBUG  WindowsBackend: uninstaller_path=None
05-24 14:36 DEBUG  WindowsBackend: previous_target_dir=None
05-24 14:36 DEBUG  WindowsBackend: previous_distro_name=None
05-24 14:36 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 14:36 DEBUG  WindowsBackend: keyboard_layout=us
05-24 14:36 DEBUG  WindowsBackend: keyboard_variant=
05-24 14:36 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 14:36 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 14:36 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 14:36 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 14:36 DEBUG  CommonBackend: Searching for local CDs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 INFO   root: Running the installer...
05-24 14:36 DEBUG  WindowsFrontend: __init__...
05-24 14:36 DEBUG  WindowsFrontend: on_init...
05-24 14:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\translations, languages=['en_US', 'en']
05-24 14:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\translations, languages=['en_US', 'en']
05-24 14:36 DEBUG  WinuiInstallationPage: target_drive=F:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-24 14:36 INFO   root: Received settings
05-24 14:36 DEBUG  CommonBackend: Searching for local CD
05-24 14:36 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:36 DEBUG  CommonBackend: Searching for local ISO
05-24 14:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pylBD63.tmp\translations, languages=['en_US', 'en']
05-24 14:36 DEBUG  TaskList: # Running tasklist...
05-24 14:36 DEBUG  TaskList: ## Running select_target_dir...
05-24 14:36 INFO   WindowsBackend: Installing into F:\ubuntu
05-24 14:36 DEBUG  TaskList: ## Finished select_target_dir
05-24 14:36 DEBUG  TaskList: ## Running create_dir_structure...
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\install
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\disks\boot\grub
05-24 14:36 DEBUG  CommonBackend: Creating dir F:\ubuntu\install\boot\grub
05-24 14:36 DEBUG  TaskList: ## Finished create_dir_structure
05-24 14:36 DEBUG  TaskList: ## Running create_uninstaller...
05-24 14:36 DEBUG  WindowsBackend: Copying uninstaller C:\Users\jbyeu_000\Downloads\wubi.exe -> F:\ubuntu\uninstall-wubi.exe
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString F:\ubuntu\uninstall-wubi.exe
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir F:\ubuntu
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon F:\ubuntu\Ubuntu.ico
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-24 14:36 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-24 14:36 DEBUG  TaskList: ## Finished create_uninstaller
05-24 14:36 DEBUG  TaskList: ## Running create_preseed_diskimage...
05-24 14:36 DEBUG  TaskList: ## Finished create_preseed_diskimage
05-24 14:36 DEBUG  TaskList: ## Running get_diskimage...
05-24 14:36 DEBUG  TaskList: New task download
05-24 14:36 DEBUG  TaskList: ### Running download...
05-24 14:36 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > F:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
05-24 14:36 DEBUG  downloader: Download start filename=F:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
05-24 14:44 DEBUG  TaskList: ### Finished download
05-24 14:44 DEBUG  downloader: download finished (read 549666608 bytes)
05-24 14:44 DEBUG  TaskList: ## Finished get_diskimage
05-24 14:44 DEBUG  TaskList: ## Running extract_diskimage...
05-24 14:46 DEBUG  TaskList: ## Finished extract_diskimage
05-24 14:46 DEBUG  TaskList: ## Running choose_disk_sizes...
05-24 14:46 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
05-24 14:46 DEBUG  TaskList: ## Finished choose_disk_sizes
05-24 14:46 DEBUG  TaskList: ## Running expand_diskimage...
05-24 14:47 DEBUG  TaskList: ## Finished expand_diskimage
05-24 14:47 DEBUG  TaskList: ## Running create_swap_diskimage...
05-24 14:47 DEBUG  TaskList: ## Finished create_swap_diskimage
05-24 14:47 DEBUG  TaskList: ## Running modify_bootloader...
05-24 14:47 DEBUG  TaskList: New task modify_bcd
05-24 14:47 DEBUG  TaskList: ### Running modify_bcd...
05-24 14:47 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 46289.7773438 mb free ntfs)
05-24 14:47 ERROR  TaskList: Error executing command
>>command=C:\WINDOWS\sysnative\bcdedit.exe /set {2b974d97-c491-11e2-bf0b-d8bee5f1f329} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 697, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\WINDOWS\sysnative\bcdedit.exe /set {2b974d97-c491-11e2-bf0b-d8bee5f1f329} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
05-24 14:47 DEBUG  TaskList: # Cancelling tasklist
05-24 14:47 DEBUG  TaskList: New task modify_bcd
05-24 14:47 ERROR  root: Error executing command
>>command=C:\WINDOWS\sysnative\bcdedit.exe /set {2b974d97-c491-11e2-bf0b-d8bee5f1f329} device partition=F:
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
>>command=C:\WINDOWS\sysnative\bcdedit.exe /set {2b974d97-c491-11e2-bf0b-d8bee5f1f329} device partition=F:
>>retval=1
>>stderr=An error has occurred setting the element data.


The request is not supported.




>>stdout=
05-24 14:47 DEBUG  TaskList: New task modify_bcd
05-24 14:47 DEBUG  TaskList: ## Finished modify_bootloader
05-24 14:47 DEBUG  TaskList: # Finished tasklist
05-24 14:53 INFO   root: === wubi 12.04 rev272 ===
05-24 14:53 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 14:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\ubuntu\\uninstall-wubi.exe"']
05-24 14:53 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\data
05-24 14:53 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\bin\7z.exe
05-24 14:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 14:53 DEBUG  CommonBackend: Fetching basic info...
05-24 14:53 DEBUG  CommonBackend: original_exe=F:\ubuntu\uninstall-wubi.exe
05-24 14:53 DEBUG  CommonBackend: platform=win32
05-24 14:53 DEBUG  CommonBackend: osname=nt
05-24 14:53 DEBUG  CommonBackend: language=en_US
05-24 14:53 DEBUG  CommonBackend: encoding=cp1252
05-24 14:53 DEBUG  WindowsBackend: arch=amd64
05-24 14:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\data\isolist.ini
05-24 14:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 14:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 14:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 14:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 14:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 14:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 14:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 14:53 DEBUG  WindowsBackend: Fetching host info...
05-24 14:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 14:53 DEBUG  WindowsBackend: windows version=vista
05-24 14:53 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 14:53 DEBUG  WindowsBackend: windows_sp=None
05-24 14:53 DEBUG  WindowsBackend: windows_build=9200
05-24 14:53 DEBUG  WindowsBackend: gmt=-5
05-24 14:53 DEBUG  WindowsBackend: country=US
05-24 14:53 DEBUG  WindowsBackend: timezone=America/New_York
05-24 14:53 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 14:53 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 14:53 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 14:53 DEBUG  WindowsBackend: windows_language_code=1033
05-24 14:53 DEBUG  WindowsBackend: windows_language=English
05-24 14:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 14:53 DEBUG  WindowsBackend: bootloader=vista
05-24 14:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46289.7226563 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: drive=Drive(C: hd 46289.7226563 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: drive=Drive(F: hd 264479.546875 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: uninstaller_path=F:\ubuntu\uninstall-wubi.exe
05-24 14:53 DEBUG  WindowsBackend: previous_target_dir=F:\ubuntu
05-24 14:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-24 14:53 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 14:53 DEBUG  WindowsBackend: keyboard_layout=us
05-24 14:53 DEBUG  WindowsBackend: keyboard_variant=
05-24 14:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 14:53 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 14:53 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 14:53 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 14:53 DEBUG  CommonBackend: Searching for local CDs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 14:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 14:53 INFO   root: Running the uninstaller...
05-24 14:53 INFO   CommonBackend: This is the uninstaller running
05-24 14:53 DEBUG  WindowsFrontend: __init__...
05-24 14:53 DEBUG  WindowsFrontend: on_init...
05-24 14:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\translations, languages=['en_US', 'en']
05-24 14:53 INFO   root: Received settings
05-24 14:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\translations, languages=['en_US', 'en']
05-24 14:53 DEBUG  TaskList: # Running tasklist...
05-24 14:53 DEBUG  TaskList: ## Running Remove bootloader entry...
05-24 14:53 DEBUG  WindowsBackend: Could not find bcd id
05-24 14:53 DEBUG  WindowsBackend: undo_bootini C:
05-24 14:53 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 46289.7226563 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: undo_bootini D:
05-24 14:53 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 67.2421875 mb free ntfs)
05-24 14:53 DEBUG  WindowsBackend: undo_bootini F:
05-24 14:53 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 264479.546875 mb free ntfs)
05-24 14:53 DEBUG  TaskList: ## Finished Remove bootloader entry
05-24 14:53 DEBUG  TaskList: ## Running Remove target dir...
05-24 14:53 DEBUG  CommonBackend: Deleting F:\ubuntu
05-24 14:53 DEBUG  TaskList: ## Finished Remove target dir
05-24 14:53 DEBUG  TaskList: ## Running Remove registry key...
05-24 14:53 DEBUG  TaskList: ## Finished Remove registry key
05-24 14:53 DEBUG  TaskList: # Finished tasklist
05-24 14:53 INFO   root: Almost finished uninstalling
05-24 14:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl7495.tmp\translations, languages=['en_US', 'en']
05-24 14:53 INFO   root: Finished uninstallation
05-24 14:53 DEBUG  root: application.quit
05-24 14:53 DEBUG  WindowsFrontend: frontend.quit
05-24 14:53 DEBUG  WindowsFrontend: frontend.on_quit
05-24 14:53 DEBUG  root: application.on_quit
05-24 14:53 INFO   root: sys.exit
05-24 16:07 INFO   root: === wubi 12.04 rev272 ===
05-24 16:07 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 16:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\jbyeu_000\\Downloads\\ubuntu-12.04.2-desktop-amd64\\wubi.exe"']
05-24 16:07 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\data
05-24 16:07 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\bin\7z.exe
05-24 16:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 16:07 DEBUG  CommonBackend: Fetching basic info...
05-24 16:07 DEBUG  CommonBackend: original_exe=C:\Users\jbyeu_000\Downloads\ubuntu-12.04.2-desktop-amd64\wubi.exe
05-24 16:07 DEBUG  CommonBackend: platform=win32
05-24 16:07 DEBUG  CommonBackend: osname=nt
05-24 16:07 DEBUG  CommonBackend: language=en_US
05-24 16:07 DEBUG  CommonBackend: encoding=cp1252
05-24 16:07 DEBUG  WindowsBackend: arch=amd64
05-24 16:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\data\isolist.ini
05-24 16:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 16:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 16:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 16:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 16:07 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 16:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 16:07 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 16:07 DEBUG  WindowsBackend: Fetching host info...
05-24 16:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 16:07 DEBUG  WindowsBackend: windows version=vista
05-24 16:07 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 16:07 DEBUG  WindowsBackend: windows_sp=None
05-24 16:07 DEBUG  WindowsBackend: windows_build=9200
05-24 16:07 DEBUG  WindowsBackend: gmt=-5
05-24 16:07 DEBUG  WindowsBackend: country=US
05-24 16:07 DEBUG  WindowsBackend: timezone=America/New_York
05-24 16:07 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 16:07 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 16:07 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 16:07 DEBUG  WindowsBackend: windows_language_code=1033
05-24 16:07 DEBUG  WindowsBackend: windows_language=English
05-24 16:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 16:07 DEBUG  WindowsBackend: bootloader=vista
05-24 16:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 44782.0 mb free ntfs)
05-24 16:07 DEBUG  WindowsBackend: drive=Drive(C: hd 44781.9960938 mb free ntfs)
05-24 16:07 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 16:07 DEBUG  WindowsBackend: drive=Drive(F: hd 460512.652344 mb free ntfs)
05-24 16:07 DEBUG  WindowsBackend: uninstaller_path=None
05-24 16:07 DEBUG  WindowsBackend: previous_target_dir=None
05-24 16:07 DEBUG  WindowsBackend: previous_distro_name=None
05-24 16:07 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 16:07 DEBUG  WindowsBackend: keyboard_layout=us
05-24 16:07 DEBUG  WindowsBackend: keyboard_variant=
05-24 16:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 16:07 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 16:07 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 16:07 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 16:07 DEBUG  CommonBackend: Searching for local CDs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 INFO   root: Running the installer...
05-24 16:07 DEBUG  WindowsFrontend: __init__...
05-24 16:07 DEBUG  WindowsFrontend: on_init...
05-24 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\translations, languages=['en_US', 'en']
05-24 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\translations, languages=['en_US', 'en']
05-24 16:07 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jeffrey
05-24 16:07 INFO   root: Received settings
05-24 16:07 DEBUG  CommonBackend: Searching for local CD
05-24 16:07 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 16:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:07 DEBUG  CommonBackend: Searching for local ISO
05-24 16:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl79C3.tmp\translations, languages=['en_US', 'en']
05-24 16:07 DEBUG  TaskList: # Running tasklist...
05-24 16:07 DEBUG  TaskList: ## Running select_target_dir...
05-24 16:07 INFO   WindowsBackend: Installing into C:\ubuntu
05-24 16:07 DEBUG  TaskList: ## Finished select_target_dir
05-24 16:07 DEBUG  TaskList: ## Running create_dir_structure...
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
05-24 16:07 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
05-24 16:07 DEBUG  TaskList: ## Finished create_dir_structure
05-24 16:07 DEBUG  TaskList: ## Running create_uninstaller...
05-24 16:07 DEBUG  WindowsBackend: Copying uninstaller C:\Users\jbyeu_000\Downloads\ubuntu-12.04.2-desktop-amd64\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev272
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
05-24 16:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
05-24 16:07 DEBUG  TaskList: ## Finished create_uninstaller
05-24 16:07 DEBUG  TaskList: ## Running create_preseed_diskimage...
05-24 16:07 DEBUG  TaskList: ## Finished create_preseed_diskimage
05-24 16:07 DEBUG  TaskList: ## Running get_diskimage...
05-24 16:07 DEBUG  TaskList: New task download
05-24 16:07 DEBUG  TaskList: ### Running download...
05-24 16:07 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz
05-24 16:07 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.04.2-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.04.2/ubuntu-12.04.2-wubi-amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
05-24 16:16 DEBUG  downloader: download finished (read 549663688 bytes)
05-24 16:16 DEBUG  TaskList: ### Finished download
05-24 16:16 DEBUG  TaskList: ## Finished get_diskimage
05-24 16:16 DEBUG  TaskList: ## Running extract_diskimage...
05-24 16:17 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
05-24 16:17 DEBUG  TaskList: # Cancelling tasklist
05-24 16:17 DEBUG  TaskList: # Finished tasklist
05-24 16:17 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
05-24 16:18 INFO   root: === wubi 12.04 rev272 ===
05-24 16:18 DEBUG  root: Logfile is c:\users\jbyeu_~1\appdata\local\temp\wubi-12.04-rev272.log
05-24 16:18 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
05-24 16:18 DEBUG  CommonBackend: data_dir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\data
05-24 16:18 DEBUG  WindowsBackend: 7z=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\bin\7z.exe
05-24 16:18 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
05-24 16:18 DEBUG  CommonBackend: Fetching basic info...
05-24 16:18 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
05-24 16:18 DEBUG  CommonBackend: platform=win32
05-24 16:18 DEBUG  CommonBackend: osname=nt
05-24 16:18 DEBUG  CommonBackend: language=en_US
05-24 16:18 DEBUG  CommonBackend: encoding=cp1252
05-24 16:18 DEBUG  WindowsBackend: arch=amd64
05-24 16:18 DEBUG  CommonBackend: Parsing isolist=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\data\isolist.ini
05-24 16:18 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
05-24 16:18 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
05-24 16:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
05-24 16:18 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
05-24 16:18 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
05-24 16:18 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
05-24 16:18 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
05-24 16:18 DEBUG  WindowsBackend: Fetching host info...
05-24 16:18 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
05-24 16:18 DEBUG  WindowsBackend: windows version=vista
05-24 16:18 DEBUG  WindowsBackend: windows_version2=Windows 8 Pro
05-24 16:18 DEBUG  WindowsBackend: windows_sp=None
05-24 16:18 DEBUG  WindowsBackend: windows_build=9200
05-24 16:18 DEBUG  WindowsBackend: gmt=-5
05-24 16:18 DEBUG  WindowsBackend: country=US
05-24 16:18 DEBUG  WindowsBackend: timezone=America/New_York
05-24 16:18 DEBUG  WindowsBackend: windows_username=Jeffrey
05-24 16:18 DEBUG  WindowsBackend: user_full_name=Jeffrey
05-24 16:18 DEBUG  WindowsBackend: user_directory=C:\Users\jbyeu_000
05-24 16:18 DEBUG  WindowsBackend: windows_language_code=1033
05-24 16:18 DEBUG  WindowsBackend: windows_language=English
05-24 16:18 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2520M CPU @ 2.50GHz
05-24 16:18 DEBUG  WindowsBackend: bootloader=vista
05-24 16:18 DEBUG  WindowsBackend: system_drive=Drive(C: hd 43034.125 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: drive=Drive(C: hd 43034.125 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: drive=Drive(D: hd 67.2421875 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: drive=Drive(F: hd 460512.652344 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
05-24 16:18 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
05-24 16:18 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
05-24 16:18 DEBUG  WindowsBackend: keyboard_id=67699721
05-24 16:18 DEBUG  WindowsBackend: keyboard_layout=us
05-24 16:18 DEBUG  WindowsBackend: keyboard_variant=
05-24 16:18 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
05-24 16:18 DEBUG  CommonBackend: locale=en_US.UTF-8
05-24 16:18 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
05-24 16:18 DEBUG  CommonBackend: Searching ISOs on USB devices
05-24 16:18 DEBUG  CommonBackend: Searching for local CDs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
05-24 16:18 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
05-24 16:18 INFO   root: Running the uninstaller...
05-24 16:18 INFO   CommonBackend: This is the uninstaller running
05-24 16:18 DEBUG  WindowsFrontend: __init__...
05-24 16:18 DEBUG  WindowsFrontend: on_init...
05-24 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\translations, languages=['en_US', 'en']
05-24 16:18 INFO   root: Received settings
05-24 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\translations, languages=['en_US', 'en']
05-24 16:18 DEBUG  TaskList: # Running tasklist...
05-24 16:18 DEBUG  TaskList: ## Running Remove bootloader entry...
05-24 16:18 DEBUG  WindowsBackend: Could not find bcd id
05-24 16:18 DEBUG  WindowsBackend: undo_bootini C:
05-24 16:18 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 43034.125 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: undo_bootini D:
05-24 16:18 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 67.2421875 mb free ntfs)
05-24 16:18 DEBUG  WindowsBackend: undo_bootini F:
05-24 16:18 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 460512.652344 mb free ntfs)
05-24 16:18 DEBUG  TaskList: ## Finished Remove bootloader entry
05-24 16:18 DEBUG  TaskList: ## Running Remove target dir...
05-24 16:18 DEBUG  CommonBackend: Deleting C:\ubuntu
05-24 16:18 DEBUG  TaskList: ## Finished Remove target dir
05-24 16:18 DEBUG  TaskList: ## Running Remove registry key...
05-24 16:18 DEBUG  TaskList: ## Finished Remove registry key
05-24 16:18 DEBUG  TaskList: # Finished tasklist
05-24 16:18 INFO   root: Almost finished uninstalling
05-24 16:18 INFO   WinuiPage: appname=wubi, localedir=C:\Users\JBYEU_~1\AppData\Local\Temp\pyl30B3.tmp\translations, languages=['en_US', 'en']
05-24 16:19 INFO   root: Finished uninstallation
05-24 16:19 DEBUG  root: application.quit
05-24 16:19 DEBUG  WindowsFrontend: frontend.quit
05-24 16:19 DEBUG  WindowsFrontend: frontend.on_quit
05-24 16:19 DEBUG  root: application.on_quit
05-24 16:19 INFO   root: sys.exit

---

### Post by Mark Phelps on 2013-05-25
Wubi doesn't work with Windows 8 -- and Wubi is being phased out as it doesn't work with Ubuntu 13.04.

---

### Post by bcbc on 2013-05-25
It didn't download the full disk image: 
[COLOR=#000000]
```
... 
amd64.tar.xz, basename=ubuntu-12.04.2-wubi-amd64.tar.xz, length=549666608, text=None
[/COLOR][COLOR=#000000]05-24 16:16 DEBUG downloader: download finished (read 549663688 bytes)
[/COLOR]
```

---

