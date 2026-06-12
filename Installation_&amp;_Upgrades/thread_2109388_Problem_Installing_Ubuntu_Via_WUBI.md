---
title: "Problem Installing Ubuntu Via WUBI"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by tusharg1993 on 2013-01-27
Hello
I was having my previous wubi installation of ubuntu 12.10. So I unistalled it. but it gave me problems. I just deleted the directory of C: drive where ubuntu is located.
But now when i want to install it , it is giving problem
with extraction failed with error message 2.

```
01-27 14:44 INFO   root: === wubi 12.10 rev273 ===
01-27 14:44 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 14:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
01-27 14:44 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\data
01-27 14:44 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\bin\7z.exe
01-27 14:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 14:44 DEBUG  CommonBackend: Fetching basic info...
01-27 14:44 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-27 14:44 DEBUG  CommonBackend: platform=win32
01-27 14:44 DEBUG  CommonBackend: osname=nt
01-27 14:44 DEBUG  CommonBackend: language=en_IN
01-27 14:44 DEBUG  CommonBackend: encoding=cp1252
01-27 14:44 DEBUG  WindowsBackend: arch=amd64
01-27 14:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\data\isolist.ini
01-27 14:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 14:44 DEBUG  WindowsBackend: Fetching host info...
01-27 14:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 14:44 DEBUG  WindowsBackend: windows version=vista
01-27 14:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 14:44 DEBUG  WindowsBackend: windows_sp=None
01-27 14:44 DEBUG  WindowsBackend: windows_build=7601
01-27 14:44 DEBUG  WindowsBackend: gmt=5
01-27 14:44 DEBUG  WindowsBackend: country=IN
01-27 14:44 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 14:44 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 14:44 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 14:44 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 14:44 DEBUG  WindowsBackend: windows_language_code=1033
01-27 14:44 DEBUG  WindowsBackend: windows_language=English
01-27 14:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 14:44 DEBUG  WindowsBackend: bootloader=vista
01-27 14:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145342.613281 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(C: hd 145342.613281 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 14:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 14:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 14:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 14:44 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 14:44 DEBUG  WindowsBackend: keyboard_layout=us
01-27 14:44 DEBUG  WindowsBackend: keyboard_variant=
01-27 14:44 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 14:44 DEBUG  CommonBackend: locale=en_IN
01-27 14:44 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 14:44 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 14:44 DEBUG  CommonBackend: Searching for local CDs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 INFO   root: Running the uninstaller...
01-27 14:44 INFO   CommonBackend: This is the uninstaller running
01-27 14:44 DEBUG  WindowsFrontend: __init__...
01-27 14:44 DEBUG  WindowsFrontend: on_init...
01-27 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\translations, languages=['en_IN', 'en']
01-27 14:44 INFO   root: Received settings
01-27 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl3F6F.tmp\translations, languages=['en_IN', 'en']
01-27 14:44 DEBUG  TaskList: # Running tasklist...
01-27 14:44 DEBUG  TaskList: ## Running Remove bootloader entry...
01-27 14:44 DEBUG  WindowsBackend: Could not find bcd id
01-27 14:44 DEBUG  WindowsBackend: undo_bootini C:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145342.613281 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: undo_bootini D:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: undo_bootini E:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:44 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 14:44 DEBUG  TaskList: # Cancelling tasklist
01-27 14:44 DEBUG  TaskList: # Finished tasklist
01-27 14:44 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 14:44 INFO   root: === wubi 12.10 rev273 ===
01-27 14:44 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 14:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
01-27 14:44 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\data
01-27 14:44 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\bin\7z.exe
01-27 14:44 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 14:44 DEBUG  CommonBackend: Fetching basic info...
01-27 14:44 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-27 14:44 DEBUG  CommonBackend: platform=win32
01-27 14:44 DEBUG  CommonBackend: osname=nt
01-27 14:44 DEBUG  CommonBackend: language=en_IN
01-27 14:44 DEBUG  CommonBackend: encoding=cp1252
01-27 14:44 DEBUG  WindowsBackend: arch=amd64
01-27 14:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\data\isolist.ini
01-27 14:44 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 14:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 14:44 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 14:44 DEBUG  WindowsBackend: Fetching host info...
01-27 14:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 14:44 DEBUG  WindowsBackend: windows version=vista
01-27 14:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 14:44 DEBUG  WindowsBackend: windows_sp=None
01-27 14:44 DEBUG  WindowsBackend: windows_build=7601
01-27 14:44 DEBUG  WindowsBackend: gmt=5
01-27 14:44 DEBUG  WindowsBackend: country=IN
01-27 14:44 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 14:44 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 14:44 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 14:44 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 14:44 DEBUG  WindowsBackend: windows_language_code=1033
01-27 14:44 DEBUG  WindowsBackend: windows_language=English
01-27 14:44 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 14:44 DEBUG  WindowsBackend: bootloader=vista
01-27 14:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145342.539063 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(C: hd 145342.539063 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 14:44 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 14:44 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 14:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 14:44 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 14:44 DEBUG  WindowsBackend: keyboard_layout=us
01-27 14:44 DEBUG  WindowsBackend: keyboard_variant=
01-27 14:44 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 14:44 DEBUG  CommonBackend: locale=en_IN
01-27 14:44 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 14:44 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 14:44 DEBUG  CommonBackend: Searching for local CDs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:44 INFO   root: Running the uninstaller...
01-27 14:44 INFO   CommonBackend: This is the uninstaller running
01-27 14:44 DEBUG  WindowsFrontend: __init__...
01-27 14:44 DEBUG  WindowsFrontend: on_init...
01-27 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\translations, languages=['en_IN', 'en']
01-27 14:44 INFO   root: Received settings
01-27 14:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl6A37.tmp\translations, languages=['en_IN', 'en']
01-27 14:44 DEBUG  TaskList: # Running tasklist...
01-27 14:44 DEBUG  TaskList: ## Running Remove bootloader entry...
01-27 14:44 DEBUG  WindowsBackend: Could not find bcd id
01-27 14:44 DEBUG  WindowsBackend: undo_bootini C:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145342.539063 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: undo_bootini D:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:44 DEBUG  WindowsBackend: undo_bootini E:
01-27 14:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:44 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 14:44 DEBUG  TaskList: # Cancelling tasklist
01-27 14:44 DEBUG  TaskList: # Finished tasklist
01-27 14:44 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 14:45 INFO   root: === wubi 12.10 rev273 ===
01-27 14:45 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 14:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
01-27 14:45 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\data
01-27 14:45 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\bin\7z.exe
01-27 14:45 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 14:45 DEBUG  CommonBackend: Fetching basic info...
01-27 14:45 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
01-27 14:45 DEBUG  CommonBackend: platform=win32
01-27 14:45 DEBUG  CommonBackend: osname=nt
01-27 14:45 DEBUG  CommonBackend: language=en_IN
01-27 14:45 DEBUG  CommonBackend: encoding=cp1252
01-27 14:45 DEBUG  WindowsBackend: arch=amd64
01-27 14:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\data\isolist.ini
01-27 14:45 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 14:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 14:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 14:45 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 14:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 14:45 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 14:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 14:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 14:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 14:45 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 14:45 DEBUG  WindowsBackend: Fetching host info...
01-27 14:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 14:45 DEBUG  WindowsBackend: windows version=vista
01-27 14:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 14:45 DEBUG  WindowsBackend: windows_sp=None
01-27 14:45 DEBUG  WindowsBackend: windows_build=7601
01-27 14:45 DEBUG  WindowsBackend: gmt=5
01-27 14:45 DEBUG  WindowsBackend: country=IN
01-27 14:45 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 14:45 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 14:45 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 14:45 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 14:45 DEBUG  WindowsBackend: windows_language_code=1033
01-27 14:45 DEBUG  WindowsBackend: windows_language=English
01-27 14:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 14:45 DEBUG  WindowsBackend: bootloader=vista
01-27 14:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145345.230469 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: drive=Drive(C: hd 145345.230469 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: drive=Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 14:45 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 14:45 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 14:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 14:45 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 14:45 DEBUG  WindowsBackend: keyboard_layout=us
01-27 14:45 DEBUG  WindowsBackend: keyboard_variant=
01-27 14:45 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 14:45 DEBUG  CommonBackend: locale=en_IN
01-27 14:45 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 14:45 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 14:45 DEBUG  CommonBackend: Searching for local CDs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 14:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 14:45 INFO   root: Running the uninstaller...
01-27 14:45 INFO   CommonBackend: This is the uninstaller running
01-27 14:45 DEBUG  WindowsFrontend: __init__...
01-27 14:45 DEBUG  WindowsFrontend: on_init...
01-27 14:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\translations, languages=['en_IN', 'en']
01-27 14:45 INFO   root: Received settings
01-27 14:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylF4B.tmp\translations, languages=['en_IN', 'en']
01-27 14:45 DEBUG  TaskList: # Running tasklist...
01-27 14:45 DEBUG  TaskList: ## Running Remove bootloader entry...
01-27 14:45 DEBUG  WindowsBackend: Could not find bcd id
01-27 14:45 DEBUG  WindowsBackend: undo_bootini C:
01-27 14:45 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 145345.230469 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: undo_bootini D:
01-27 14:45 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60474.8320313 mb free ntfs)
01-27 14:45 DEBUG  WindowsBackend: undo_bootini E:
01-27 14:45 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1533.2265625 mb free ntfs)
01-27 14:45 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 14:45 DEBUG  TaskList: # Cancelling tasklist
01-27 14:45 DEBUG  TaskList: # Finished tasklist
01-27 14:45 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 124, in select_task
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 22:47 INFO   root: === wubi 12.10 rev273 ===
01-27 22:47 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 22:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\TUSHAR\\Downloads\\Programs\\wubi.exe"']
01-27 22:47 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\data
01-27 22:47 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\bin\7z.exe
01-27 22:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 22:47 DEBUG  CommonBackend: Fetching basic info...
01-27 22:47 DEBUG  CommonBackend: original_exe=C:\Users\TUSHAR\Downloads\Programs\wubi.exe
01-27 22:47 DEBUG  CommonBackend: platform=win32
01-27 22:47 DEBUG  CommonBackend: osname=nt
01-27 22:47 DEBUG  CommonBackend: language=en_IN
01-27 22:47 DEBUG  CommonBackend: encoding=cp1252
01-27 22:47 DEBUG  WindowsBackend: arch=amd64
01-27 22:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\data\isolist.ini
01-27 22:47 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 22:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 22:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 22:47 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 22:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 22:47 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 22:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 22:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 22:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 22:47 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 22:47 DEBUG  WindowsBackend: Fetching host info...
01-27 22:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 22:47 DEBUG  WindowsBackend: windows version=vista
01-27 22:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 22:47 DEBUG  WindowsBackend: windows_sp=None
01-27 22:47 DEBUG  WindowsBackend: windows_build=7601
01-27 22:47 DEBUG  WindowsBackend: gmt=5
01-27 22:47 DEBUG  WindowsBackend: country=IN
01-27 22:47 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 22:47 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 22:47 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 22:47 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 22:47 DEBUG  WindowsBackend: windows_language_code=1033
01-27 22:47 DEBUG  WindowsBackend: windows_language=English
01-27 22:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 22:47 DEBUG  WindowsBackend: bootloader=vista
01-27 22:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 144866.945313 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: drive=Drive(C: hd 144866.945313 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: drive=Drive(E: hd 1533.2265625 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 22:47 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 22:47 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 22:47 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 22:47 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 22:47 DEBUG  WindowsBackend: keyboard_layout=us
01-27 22:47 DEBUG  WindowsBackend: keyboard_variant=
01-27 22:47 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 22:47 DEBUG  CommonBackend: locale=en_IN
01-27 22:47 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 22:47 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 22:47 DEBUG  CommonBackend: Searching for local CDs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:47 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:47 INFO   root: Already installed, running the uninstaller...
01-27 22:47 INFO   root: Running the uninstaller...
01-27 22:47 INFO   CommonBackend: This is the uninstaller running
01-27 22:47 DEBUG  WindowsFrontend: __init__...
01-27 22:47 DEBUG  WindowsFrontend: on_init...
01-27 22:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\translations, languages=['en_IN', 'en']
01-27 22:47 INFO   root: Received settings
01-27 22:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylE81E.tmp\translations, languages=['en_IN', 'en']
01-27 22:47 DEBUG  TaskList: # Running tasklist...
01-27 22:47 DEBUG  TaskList: ## Running Remove bootloader entry...
01-27 22:47 DEBUG  WindowsBackend: Could not find bcd id
01-27 22:47 DEBUG  WindowsBackend: undo_bootini C:
01-27 22:47 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 144866.945313 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: undo_bootini D:
01-27 22:47 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60474.8320313 mb free ntfs)
01-27 22:47 DEBUG  WindowsBackend: undo_bootini E:
01-27 22:47 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1533.2265625 mb free ntfs)
01-27 22:47 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 22:47 DEBUG  TaskList: # Cancelling tasklist
01-27 22:47 DEBUG  TaskList: # Finished tasklist
01-27 22:47 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 145, in run_installer
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 22:51 INFO   root: === wubi 12.10 rev273 ===
01-27 22:51 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 22:51 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-27 22:51 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\data
01-27 22:51 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\bin\7z.exe
01-27 22:51 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 22:51 DEBUG  CommonBackend: Fetching basic info...
01-27 22:51 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-27 22:51 DEBUG  CommonBackend: platform=win32
01-27 22:51 DEBUG  CommonBackend: osname=nt
01-27 22:51 DEBUG  CommonBackend: language=en_IN
01-27 22:51 DEBUG  CommonBackend: encoding=cp1252
01-27 22:51 DEBUG  WindowsBackend: arch=amd64
01-27 22:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\data\isolist.ini
01-27 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 22:51 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 22:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 22:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 22:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 22:51 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 22:51 DEBUG  WindowsBackend: Fetching host info...
01-27 22:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 22:51 DEBUG  WindowsBackend: windows version=vista
01-27 22:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 22:51 DEBUG  WindowsBackend: windows_sp=None
01-27 22:51 DEBUG  WindowsBackend: windows_build=7601
01-27 22:51 DEBUG  WindowsBackend: gmt=5
01-27 22:51 DEBUG  WindowsBackend: country=IN
01-27 22:51 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 22:51 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 22:51 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 22:51 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 22:51 DEBUG  WindowsBackend: windows_language_code=1033
01-27 22:51 DEBUG  WindowsBackend: windows_language=English
01-27 22:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 22:51 DEBUG  WindowsBackend: bootloader=vista
01-27 22:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 144910.292969 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: drive=Drive(C: hd 144910.292969 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: drive=Drive(E: hd 1530.83984375 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 22:51 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 22:51 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 22:51 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 22:51 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 22:51 DEBUG  WindowsBackend: keyboard_layout=us
01-27 22:51 DEBUG  WindowsBackend: keyboard_variant=
01-27 22:51 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 22:51 DEBUG  CommonBackend: locale=en_IN
01-27 22:51 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 22:51 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 22:51 DEBUG  CommonBackend: Searching for local CDs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:51 INFO   root: Already installed, running the uninstaller...
01-27 22:51 INFO   root: Running the uninstaller...
01-27 22:51 INFO   CommonBackend: This is the uninstaller running
01-27 22:51 DEBUG  WindowsFrontend: __init__...
01-27 22:51 DEBUG  WindowsFrontend: on_init...
01-27 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\translations, languages=['en_IN', 'en']
01-27 22:51 INFO   root: Received settings
01-27 22:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pylDFB5.tmp\translations, languages=['en_IN', 'en']
01-27 22:51 DEBUG  TaskList: # Running tasklist...
01-27 22:51 DEBUG  TaskList: ## Running Remove bootloader entry...
01-27 22:51 DEBUG  WindowsBackend: Could not find bcd id
01-27 22:51 DEBUG  WindowsBackend: undo_bootini C:
01-27 22:51 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 144910.292969 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: undo_bootini D:
01-27 22:51 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 60474.8320313 mb free ntfs)
01-27 22:51 DEBUG  WindowsBackend: undo_bootini E:
01-27 22:51 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 1530.83984375 mb free ntfs)
01-27 22:51 ERROR  TaskList: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 22:51 DEBUG  TaskList: # Cancelling tasklist
01-27 22:51 DEBUG  TaskList: # Finished tasklist
01-27 22:51 ERROR  root: [Errno 13] Permission denied: 'E:\\wubildr'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 145, in run_installer
  File "\lib\wubi\application.py", line 181, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 576, in undo_bootloader
OSError: [Errno 13] Permission denied: 'E:\\wubildr'
01-27 22:53 INFO   root: === wubi 12.10 rev273 ===
01-27 22:53 DEBUG  root: Logfile is c:\users\tushar\appdata\local\temp\wubi-12.10-rev273.log
01-27 22:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
01-27 22:53 DEBUG  CommonBackend: data_dir=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\data
01-27 22:53 DEBUG  WindowsBackend: 7z=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\bin\7z.exe
01-27 22:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
01-27 22:53 DEBUG  CommonBackend: Fetching basic info...
01-27 22:53 DEBUG  CommonBackend: original_exe=E:\wubi.exe
01-27 22:53 DEBUG  CommonBackend: platform=win32
01-27 22:53 DEBUG  CommonBackend: osname=nt
01-27 22:53 DEBUG  CommonBackend: language=en_IN
01-27 22:53 DEBUG  CommonBackend: encoding=cp1252
01-27 22:53 DEBUG  WindowsBackend: arch=amd64
01-27 22:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\data\isolist.ini
01-27 22:53 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
01-27 22:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-27 22:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-27 22:53 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
01-27 22:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-27 22:53 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
01-27 22:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-27 22:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-27 22:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-27 22:53 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
01-27 22:53 DEBUG  WindowsBackend: Fetching host info...
01-27 22:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-27 22:53 DEBUG  WindowsBackend: windows version=vista
01-27 22:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Basic
01-27 22:53 DEBUG  WindowsBackend: windows_sp=None
01-27 22:53 DEBUG  WindowsBackend: windows_build=7601
01-27 22:53 DEBUG  WindowsBackend: gmt=5
01-27 22:53 DEBUG  WindowsBackend: country=IN
01-27 22:53 DEBUG  WindowsBackend: timezone=Asia/Calcutta
01-27 22:53 DEBUG  WindowsBackend: windows_username=TUSHAR
01-27 22:53 DEBUG  WindowsBackend: user_full_name=TUSHAR
01-27 22:53 DEBUG  WindowsBackend: user_directory=C:\Users\TUSHAR
01-27 22:53 DEBUG  WindowsBackend: windows_language_code=1033
01-27 22:53 DEBUG  WindowsBackend: windows_language=English
01-27 22:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
01-27 22:53 DEBUG  WindowsBackend: bootloader=vista
01-27 22:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 145489.488281 mb free ntfs)
01-27 22:53 DEBUG  WindowsBackend: drive=Drive(C: hd 145489.488281 mb free ntfs)
01-27 22:53 DEBUG  WindowsBackend: drive=Drive(D: hd 60474.8320313 mb free ntfs)
01-27 22:53 DEBUG  WindowsBackend: drive=Drive(E: hd 1530.83984375 mb free ntfs)
01-27 22:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
01-27 22:53 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
01-27 22:53 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
01-27 22:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
01-27 22:53 DEBUG  WindowsBackend: keyboard_id=67699721
01-27 22:53 DEBUG  WindowsBackend: keyboard_layout=us
01-27 22:53 DEBUG  WindowsBackend: keyboard_variant=
01-27 22:53 DEBUG  CommonBackend: python locale=('en_IN', 'cp1252')
01-27 22:53 DEBUG  CommonBackend: locale=en_IN
01-27 22:53 DEBUG  WindowsBackend: total_memory_mb=4043.859375
01-27 22:53 DEBUG  CommonBackend: Searching ISOs on USB devices
01-27 22:53 DEBUG  CommonBackend: Searching for local CDs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 INFO   root: Running the installer...
01-27 22:53 DEBUG  WindowsFrontend: __init__...
01-27 22:53 DEBUG  WindowsFrontend: on_init...
01-27 22:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\translations, languages=['en_IN', 'en']
01-27 22:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\translations, languages=['en_IN', 'en']
01-27 22:53 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tushar
01-27 22:53 INFO   root: Received settings
01-27 22:53 DEBUG  CommonBackend: Searching for local CD
01-27 22:53 DEBUG  Distro:   checking whether C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-27 22:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-27 22:53 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-27 22:53 DEBUG  CommonBackend: Searching for local ISO
01-27 22:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUSHAR\AppData\Local\Temp\pyl68F1.tmp\translations, languages=['en_US', 'en']
01-27 22:53 DEBUG  TaskList: # Running tasklist...
01-27 22:53 DEBUG  TaskList: ## Running select_target_dir...
01-27 22:53 INFO   WindowsBackend: Installing into C:\ubuntu
01-27 22:53 DEBUG  TaskList: ## Finished select_target_dir
01-27 22:53 DEBUG  TaskList: ## Running create_dir_structure...
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
01-27 22:53 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
01-27 22:53 DEBUG  TaskList: ## Finished create_dir_structure
01-27 22:53 DEBUG  TaskList: ## Running create_uninstaller...
01-27 22:53 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
01-27 22:53 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
01-27 22:53 DEBUG  TaskList: ## Finished create_uninstaller
01-27 22:53 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-27 22:53 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-27 22:53 DEBUG  TaskList: ## Running get_diskimage...
01-27 22:53 DEBUG  TaskList: New task download
01-27 22:53 DEBUG  TaskList: ### Running download...
01-27 22:53 DEBUG  downloader: downloading http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
01-27 22:53 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
01-27 22:58 DEBUG  downloader: download finished (read 39463545 bytes)
01-27 22:58 DEBUG  TaskList: ### Finished download
01-27 22:58 DEBUG  TaskList: ## Finished get_diskimage
01-27 22:58 DEBUG  TaskList: ## Running extract_diskimage...
01-27 22:58 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
01-27 22:58 DEBUG  TaskList: # Cancelling tasklist
01-27 22:58 DEBUG  TaskList: # Finished tasklist
01-27 22:58 ERROR  root: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2

```

---

### Post by bcbc on 2013-01-27
The file is 562061340 bytes, but it only downloaded 39463545 bytes. Probably due to some connection issue. 
It fails extraction due to it being invalid.

What can you do? 

You could try again, and hope it completes.

You could download the disk image yourself but then you have to tell wubi where it is. See here for how: [http://askubuntu.com/a/143478/14916](http://askubuntu.com/a/143478/14916)

You could download the ISO instead and place it in the same folder as Wubi before running (and finds the ISO automatically). The benefit of this is that you can also burn the ISO to a CD or create a bootable USB and then you can do a normal dual boot instead of Wubi (which is mainly to try out Ubuntu).

```
01-27 22:53 DEBUG  TaskList: ### Running download...
01-27 22:53 DEBUG  downloader: downloading http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
01-27 22:53 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
01-27 22:58 DEBUG  downloader: download finished (read 39463545 bytes)
01-27 22:58 DEBUG  TaskList: ### Finished download
01-27 22:58 DEBUG  TaskList: ## Finished get_diskimage
01-27 22:58 DEBUG  TaskList: ## Running extract_diskimage...
01-27 22:58 ERROR  TaskList: Extraction failed with code: 2
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 450, in extract_diskimage
Exception: Extraction failed with code: 2
```

---

### Post by tusharg1993 on 2013-01-27
thank you sir, my problem has been solved.
your solution was apt and i downloaded the .tar.xz file separately and installed it.

---

