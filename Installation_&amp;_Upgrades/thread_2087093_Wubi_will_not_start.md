---
title: "Wubi will not start"
date: 2012-11-22
forum: Installation &amp; Upgrades
---

### Post by chewyboy000 on 2012-11-22
Ok so I launch wubi.exe but it doesn't do anything. Here is a log: 11-22 19:03 INFO   root: === wubi 12.10 rev273 ===
11-22 19:03 DEBUG  root: Logfile is c:\users\jasonh~1\appdata\local\temp\wubi-12.10-rev273.log
11-22 19:03 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Jason Howard\\Downloads\\wubi.exe"']
11-22 19:03 DEBUG  CommonBackend: data_dir=C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\data
11-22 19:03 DEBUG  WindowsBackend: 7z=C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\bin\7z.exe
11-22 19:03 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
11-22 19:03 DEBUG  CommonBackend: Fetching basic info...
11-22 19:03 DEBUG  CommonBackend: original_exe=C:\Users\Jason Howard\Downloads\wubi.exe
11-22 19:03 DEBUG  CommonBackend: platform=win32
11-22 19:03 DEBUG  CommonBackend: osname=nt
11-22 19:03 DEBUG  CommonBackend: language=en_US
11-22 19:03 DEBUG  CommonBackend: encoding=cp1252
11-22 19:03 DEBUG  WindowsBackend: arch=amd64
11-22 19:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\data\isolist.ini
11-22 19:03 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
11-22 19:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
11-22 19:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
11-22 19:03 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
11-22 19:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
11-22 19:03 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
11-22 19:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
11-22 19:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
11-22 19:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
11-22 19:03 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
11-22 19:03 DEBUG  WindowsBackend: Fetching host info...
11-22 19:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
11-22 19:03 DEBUG  WindowsBackend: windows version=vista
11-22 19:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
11-22 19:03 DEBUG  WindowsBackend: windows_sp=None
11-22 19:03 DEBUG  WindowsBackend: windows_build=7601
11-22 19:03 DEBUG  WindowsBackend: gmt=-5
11-22 19:03 DEBUG  WindowsBackend: country=US
11-22 19:03 DEBUG  WindowsBackend: timezone=America/New_York
11-22 19:03 DEBUG  WindowsBackend: windows_username=Jason Howard
11-22 19:03 DEBUG  WindowsBackend: user_full_name=Jason Howard
11-22 19:03 DEBUG  WindowsBackend: user_directory=C:\Users\Jason Howard
11-22 19:03 DEBUG  WindowsBackend: windows_language_code=1033
11-22 19:03 DEBUG  WindowsBackend: windows_language=English
11-22 19:03 DEBUG  WindowsBackend: processor_name=Intel(R) Celeron(R) CPU          900  @ 2.20GHz
11-22 19:03 DEBUG  WindowsBackend: bootloader=vista
11-22 19:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 45527.8710938 mb free ntfs)
11-22 19:03 DEBUG  WindowsBackend: drive=Drive(C: hd 45527.8710938 mb free ntfs)
11-22 19:03 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
11-22 19:03 DEBUG  WindowsBackend: drive=Drive(Q: hd 0.0 mb free )
11-22 19:03 DEBUG  WindowsBackend: uninstaller_path=None
11-22 19:03 DEBUG  WindowsBackend: previous_target_dir=None
11-22 19:03 DEBUG  WindowsBackend: previous_distro_name=None
11-22 19:03 DEBUG  WindowsBackend: keyboard_id=67699721
11-22 19:03 DEBUG  WindowsBackend: keyboard_layout=us
11-22 19:03 DEBUG  WindowsBackend: keyboard_variant=
11-22 19:03 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
11-22 19:03 DEBUG  CommonBackend: locale=en_US.UTF-8
11-22 19:03 DEBUG  WindowsBackend: total_memory_mb=1915.984375
11-22 19:03 DEBUG  CommonBackend: Searching ISOs on USB devices
11-22 19:03 DEBUG  Distro:   checking Ubuntu ISO C:\Windows 3.1.ISO
11-22 19:03 ERROR  WindowsBackend: Error executing command
>>command=C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\bin\7z.exe l C:\Windows 3.1.ISO
>>retval=2
>>stderr=

7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18



Error: C:\Windows 3.1.ISO: Can not open file as archive



Errors: 1
>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\win32\backend.py", line 519, in get_iso_file_names
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\bin\7z.exe l C:\Windows 3.1.ISO
>>retval=2
>>stderr=

7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18



Error: C:\Windows 3.1.ISO: Can not open file as archive



Errors: 1
>>stdout=
11-22 19:03 DEBUG  WindowsBackend: command >>C:\Users\JASONH~1\AppData\Local\Temp\pylF4CA.tmp\bin\7z.exe l C:\Windows 3.1.ISO
11-22 19:03 DEBUG  Distro:     does not contain casper\filesystem.squashfs
11-22 19:03 DEBUG  Distro:   checking Ubuntu ISO C:\Windows 3.1.ISO
11-22 19:03 ERROR  root: iteration over non-sequence
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 57, in run
  File "\lib\wubi\backends\common\backend.py", line 190, in fetch_basic_info
  File "\lib\wubi\backends\common\backend.py", line 803, in find_any_iso
  File "\lib\wubi\backends\common\distro.py", line 113, in is_valid_iso
TypeError: iteration over non-sequence

---

### Post by chewyboy000 on 2012-11-22
Okay I read the log file and I saw that Windows 3.1.iso was conflicting with it and then I renamed the file to Windows 3.1.iso.wubiconflict... Wubi works now.

---

