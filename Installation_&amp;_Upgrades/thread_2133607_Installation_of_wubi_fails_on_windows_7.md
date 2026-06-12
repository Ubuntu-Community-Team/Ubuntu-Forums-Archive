---
title: "Installation of wubi fails on windows 7"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by Calvinista on 2013-04-08
I'm trying to install ubuntu using wubi under Windows 7.  I was successful on another computer which runs XP, but this one fails.

Here is the log file beginning with the first error message.

Thanks!


04-08 15:23 ERROR  TaskList: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


04-08 15:23 DEBUG  TaskList: # Cancelling tasklist
04-08 15:23 ERROR  root: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


04-08 15:23 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2013-04-08
Look before that in the log. Check the number of bytes in the diskimage tar.xz file being downloaded, and check the number of bytes that were actually downloaded. Ensure they're the same.

---

### Post by Calvinista on 2013-04-09
Thanks for responding.
They are the same.
Here is the whole log file:

04-08 15:15 INFO   root: === wubi 12.10 rev273 ===
04-08 15:15 DEBUG  root: Logfile is c:\users\phil's~1\appdata\local\temp\wubi-12.10-rev273.log
04-08 15:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Phil\'s Computer\\Downloads\\wubi(1).exe"']
04-08 15:15 DEBUG  CommonBackend: data_dir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\data
04-08 15:15 DEBUG  WindowsBackend: 7z=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\7z.exe
04-08 15:15 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
04-08 15:15 DEBUG  CommonBackend: Fetching basic info...
04-08 15:15 DEBUG  CommonBackend: original_exe=C:\Users\Phil's Computer\Downloads\wubi(1).exe
04-08 15:15 DEBUG  CommonBackend: platform=win32
04-08 15:15 DEBUG  CommonBackend: osname=nt
04-08 15:15 DEBUG  CommonBackend: language=en_US
04-08 15:15 DEBUG  CommonBackend: encoding=cp1252
04-08 15:15 DEBUG  WindowsBackend: arch=amd64
04-08 15:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\data\isolist.ini
04-08 15:15 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-08 15:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 15:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 15:15 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-08 15:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 15:15 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-08 15:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 15:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 15:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 15:15 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-08 15:15 DEBUG  WindowsBackend: Fetching host info...
04-08 15:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 15:15 DEBUG  WindowsBackend: windows version=vista
04-08 15:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-08 15:15 DEBUG  WindowsBackend: windows_sp=None
04-08 15:15 DEBUG  WindowsBackend: windows_build=7601
04-08 15:15 DEBUG  WindowsBackend: gmt=-6
04-08 15:15 DEBUG  WindowsBackend: country=US
04-08 15:15 DEBUG  WindowsBackend: timezone=America/Chicago
04-08 15:15 DEBUG  WindowsBackend: windows_username=Phil's Computer
04-08 15:15 DEBUG  WindowsBackend: user_full_name=Phil's Computer
04-08 15:15 DEBUG  WindowsBackend: user_directory=C:\Users\Phil's Computer
04-08 15:15 DEBUG  WindowsBackend: windows_language_code=1033
04-08 15:15 DEBUG  WindowsBackend: windows_language=English
04-08 15:15 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) 145 Processor
04-08 15:15 DEBUG  WindowsBackend: bootloader=vista
04-08 15:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 402666.777344 mb free ntfs)
04-08 15:15 DEBUG  WindowsBackend: drive=Drive(C: hd 402666.777344 mb free ntfs)
04-08 15:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-08 15:15 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
04-08 15:15 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-08 15:15 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-08 15:15 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-08 15:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
04-08 15:15 DEBUG  WindowsBackend: keyboard_id=67699721
04-08 15:15 DEBUG  WindowsBackend: keyboard_layout=us
04-08 15:15 DEBUG  WindowsBackend: keyboard_variant=
04-08 15:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
04-08 15:15 DEBUG  CommonBackend: locale=en_US.UTF-8
04-08 15:15 DEBUG  WindowsBackend: total_memory_mb=1791.3671875
04-08 15:15 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 15:15 DEBUG  CommonBackend: Searching for local CDs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:15 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-08 15:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 INFO   root: Already installed, running the uninstaller...
04-08 15:16 INFO   root: Running the uninstaller...
04-08 15:16 INFO   CommonBackend: This is the uninstaller running
04-08 15:16 DEBUG  WindowsFrontend: __init__...
04-08 15:16 DEBUG  WindowsFrontend: on_init...
04-08 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\translations, languages=['en_US', 'en']
04-08 15:16 INFO   root: Received settings
04-08 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\translations, languages=['en_US', 'en']
04-08 15:16 DEBUG  TaskList: # Running tasklist...
04-08 15:16 DEBUG  TaskList: ## Running Remove bootloader entry...
04-08 15:16 DEBUG  WindowsBackend: Could not find bcd id
04-08 15:16 DEBUG  WindowsBackend: undo_bootini C:
04-08 15:16 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 402666.777344 mb free ntfs)
04-08 15:16 DEBUG  WindowsBackend: undo_bootini E:
04-08 15:16 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 0.0 mb free )
04-08 15:16 DEBUG  WindowsBackend: undo_bootini F:
04-08 15:16 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
04-08 15:16 DEBUG  TaskList: ## Finished Remove bootloader entry
04-08 15:16 DEBUG  TaskList: ## Running Remove target dir...
04-08 15:16 DEBUG  CommonBackend: Deleting C:\ubuntu
04-08 15:16 DEBUG  TaskList: ## Finished Remove target dir
04-08 15:16 DEBUG  TaskList: ## Running Remove registry key...
04-08 15:16 DEBUG  TaskList: ## Finished Remove registry key
04-08 15:16 DEBUG  TaskList: # Finished tasklist
04-08 15:16 INFO   root: Almost finished uninstalling
04-08 15:16 INFO   root: Finished uninstallation
04-08 15:16 DEBUG  CommonBackend: Fetching basic info...
04-08 15:16 DEBUG  CommonBackend: original_exe=C:\Users\Phil's Computer\Downloads\wubi(1).exe
04-08 15:16 DEBUG  CommonBackend: platform=win32
04-08 15:16 DEBUG  CommonBackend: osname=nt
04-08 15:16 DEBUG  WindowsBackend: arch=amd64
04-08 15:16 DEBUG  CommonBackend: Parsing isolist=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\data\isolist.ini
04-08 15:16 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
04-08 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-08 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-08 15:16 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
04-08 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-08 15:16 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
04-08 15:16 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-08 15:16 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-08 15:16 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-08 15:16 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
04-08 15:16 DEBUG  WindowsBackend: Fetching host info...
04-08 15:16 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-08 15:16 DEBUG  WindowsBackend: windows version=vista
04-08 15:16 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
04-08 15:16 DEBUG  WindowsBackend: windows_sp=None
04-08 15:16 DEBUG  WindowsBackend: windows_build=7601
04-08 15:16 DEBUG  WindowsBackend: gmt=-6
04-08 15:16 DEBUG  WindowsBackend: country=US
04-08 15:16 DEBUG  WindowsBackend: timezone=America/Chicago
04-08 15:16 DEBUG  WindowsBackend: windows_username=Phil's Computer
04-08 15:16 DEBUG  WindowsBackend: user_full_name=Phil's Computer
04-08 15:16 DEBUG  WindowsBackend: user_directory=C:\Users\Phil's Computer
04-08 15:16 DEBUG  WindowsBackend: windows_language_code=1033
04-08 15:16 DEBUG  WindowsBackend: windows_language=English
04-08 15:16 DEBUG  WindowsBackend: processor_name=AMD Sempron(tm) 145 Processor
04-08 15:16 DEBUG  WindowsBackend: bootloader=vista
04-08 15:16 DEBUG  WindowsBackend: system_drive=Drive(C: hd 405162.257813 mb free ntfs)
04-08 15:16 DEBUG  WindowsBackend: drive=Drive(C: hd 405162.257813 mb free ntfs)
04-08 15:16 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-08 15:16 DEBUG  WindowsBackend: drive=Drive(E: removable 0.0 mb free )
04-08 15:16 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
04-08 15:16 DEBUG  WindowsBackend: uninstaller_path=None
04-08 15:16 DEBUG  WindowsBackend: previous_target_dir=None
04-08 15:16 DEBUG  WindowsBackend: previous_distro_name=None
04-08 15:16 DEBUG  WindowsBackend: keyboard_id=67699721
04-08 15:16 DEBUG  WindowsBackend: keyboard_layout=us
04-08 15:16 DEBUG  WindowsBackend: keyboard_variant=
04-08 15:16 DEBUG  WindowsBackend: total_memory_mb=1791.3671875
04-08 15:16 DEBUG  CommonBackend: Searching ISOs on USB devices
04-08 15:16 DEBUG  CommonBackend: Searching for local CDs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 INFO   root: Running the installer...
04-08 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\translations, languages=['en_US', 'en']
04-08 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\translations, languages=['en_US', 'en']
04-08 15:16 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=18000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=philscomputer
04-08 15:16 INFO   root: Received settings
04-08 15:16 DEBUG  CommonBackend: Searching for local CD
04-08 15:16 DEBUG  Distro:   checking whether C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
04-08 15:16 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
04-08 15:16 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
04-08 15:16 DEBUG  CommonBackend: Searching for local ISO
04-08 15:16 INFO   WinuiPage: appname=wubi, localedir=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\translations, languages=['en_US', 'en']
04-08 15:16 DEBUG  TaskList: # Running tasklist...
04-08 15:16 DEBUG  TaskList: ## Running select_target_dir...
04-08 15:16 INFO   WindowsBackend: Installing into C:\ubuntu
04-08 15:16 DEBUG  TaskList: ## Finished select_target_dir
04-08 15:16 DEBUG  TaskList: ## Running create_dir_structure...
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-08 15:16 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-08 15:16 DEBUG  TaskList: ## Finished create_dir_structure
04-08 15:16 DEBUG  TaskList: ## Running create_uninstaller...
04-08 15:16 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Phil's Computer\Downloads\wubi(1).exe -> C:\ubuntu\uninstall-wubi.exe
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.10-rev273
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-08 15:16 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-08 15:16 DEBUG  TaskList: ## Finished create_uninstaller
04-08 15:16 DEBUG  TaskList: ## Running create_preseed_diskimage...
04-08 15:16 DEBUG  TaskList: ## Finished create_preseed_diskimage
04-08 15:16 DEBUG  TaskList: ## Running get_diskimage...
04-08 15:16 DEBUG  TaskList: New task download
04-08 15:16 DEBUG  TaskList: ### Running download...
04-08 15:16 DEBUG  downloader: downloading [http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz) > C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz
04-08 15:16 DEBUG  downloader: Download start filename=C:\ubuntu\disks\ubuntu-12.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/12.10/ubuntu-12.10-wubi-amd64.tar.xz, basename=ubuntu-12.10-wubi-amd64.tar.xz, length=562061340, text=None
04-08 15:22 DEBUG  TaskList: ### Finished download
04-08 15:22 DEBUG  downloader: download finished (read 562061340 bytes)
04-08 15:22 DEBUG  TaskList: ## Finished get_diskimage
04-08 15:22 DEBUG  TaskList: ## Running extract_diskimage...
04-08 15:23 DEBUG  TaskList: ## Finished extract_diskimage
04-08 15:23 DEBUG  TaskList: ## Running choose_disk_sizes...
04-08 15:23 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
04-08 15:23 DEBUG  TaskList: ## Finished choose_disk_sizes
04-08 15:23 DEBUG  TaskList: ## Running expand_diskimage...
04-08 15:23 ERROR  TaskList: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


04-08 15:23 DEBUG  TaskList: # Cancelling tasklist
04-08 15:23 ERROR  root: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 463, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\PHIL'S~1\AppData\Local\Temp\pylC84B.tmp\bin\resize2fs.exe -f C:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/PHILS~1/AppData/Local/Temp/pylC84B.tmp/bin/resize2fs.exe -f C:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


04-08 15:23 DEBUG  TaskList: # Finished tasklist

---

### Post by darkod on 2013-04-09
If you have win7 with uefi boot that means gpt table on the disk. I have heard wubi doesn't work on gpt.

Almost all windows machines these days come with gpt. Older win7 machines might still have msdos table.

---

### Post by bcbc on 2013-04-09
I've seen this problem before. It's the apostrophe (') in your user name. For whatever reason the command isn't escaped correctly and resize2fs fails. I don't know if this bug has been reported already. Feel free to file one:  [http://bugs.launchpad.net/wubi/+filebug](http://bugs.launchpad.net/wubi/+filebug) (although dev has stopped on Wubi so not sure what will happen with it).

The only other way to install it would be to save the 12.10 desktop ISO in the same folder as wubi.exe before running (and in this case it doesn't use the diskimage install, so resize2fs isn't involved).

Also see what darkod said.

---

### Post by Calvinista on 2013-04-09
OK that's the problem.  I created a new admin account without the apostrophe and everything worked.
Thanks for all the help!

---

### Post by bcbc on 2013-04-09
Cool, thanks for your feedback. I created the bug report for you. [https://bugs.launchpad.net/wubi/+bug/1166919](https://bugs.launchpad.net/wubi/+bug/1166919)

---

