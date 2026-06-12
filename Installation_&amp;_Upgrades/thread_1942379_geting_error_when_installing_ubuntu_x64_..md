---
title: "geting error when installing ubuntu x64 ."
date: 2012-03-17
forum: Installation &amp; Upgrades
---

### Post by sysWOW64 on 2012-03-17
hi ! today i just downloaded ubuntu's x64 version to install on my windows 7 pc but i am getting error. when ever i try to install ubuntu from boot . it says some kind of hardware or CD fault so i checked my hard disk but it won't show any erro neither CD. also i burned ubuntu on other dvd but again i am getting same error any help guys?

my system
dell 3010
windows 7 ultimate x64
intel i5 2.8Ghz
4Gb ram
1Gb ati graphic card.

name of installation pack = ubuntu-11.10-desktop-amd64.iso

---

### Post by 2F4U on 2012-03-17
Does this happen when you boot the liveCD or when you start the installation? It would be helpful if you could provide the exact error message.

---

### Post by sysWOW64 on 2012-03-17
when i got throw boot menu and select install then disk partition and when it prompt me to select my time zone then. and sorry i won't able to find log file . did you know where it be ? or can i boot again to note that message ?

---

### Post by 2F4U on 2012-03-17
I didn't say anything about a log file, I wanted to know the exact error message and yes, you can boot the liveCD as often as you like.

---

### Post by sysWOW64 on 2012-03-17
here's the messages which it show's after insulation failure  .
and a log file which i found in temp folder.

[IMG]https://lh3.googleusercontent.com/-Xg-DXmxaftE/T2TBokzshpI/AAAAAAAAPFM/vk40bL7tcAw/s640/21102011133.jpg[/IMG]

[IMG]https://lh3.googleusercontent.com/-Er7RnuB76zk/T2S7gbaRgCI/AAAAAAAAPFE/_Lc_mmgiWwo/s640/Photo0199.jpg[/IMG]

(sorry for crappy image thanks to my gf.)

and lol       GOKU -->:lolflag:


```
hard disk info =500GB total, 451GB available 13%used by windows.
Western Digital WDC WD5000BEKT-75KA9T0 ATA Device (SATA), 7200RPM , runtime 194days 12 hours.
```

i made 109GB partition for ubuntu.


log file 
```
03-17 18:04 INFO   root: === wubi 11.10 rev241 ===
03-17 18:04 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:04 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\data
03-17 18:04 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\bin\7z.exe
03-17 18:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:04 DEBUG  CommonBackend: Fetching basic info...
03-17 18:04 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:04 DEBUG  CommonBackend: platform=win32
03-17 18:04 DEBUG  CommonBackend: osname=nt
03-17 18:04 DEBUG  CommonBackend: language=en_US
03-17 18:04 DEBUG  CommonBackend: encoding=cp1252
03-17 18:04 DEBUG  WindowsBackend: arch=amd64
03-17 18:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\data\isolist.ini
03-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:04 DEBUG  WindowsBackend: Fetching host info...
03-17 18:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:04 DEBUG  WindowsBackend: windows version=vista
03-17 18:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:04 DEBUG  WindowsBackend: windows_sp=None
03-17 18:04 DEBUG  WindowsBackend: windows_build=7601
03-17 18:04 DEBUG  WindowsBackend: gmt=5
03-17 18:04 DEBUG  WindowsBackend: country=US
03-17 18:04 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:04 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:04 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:04 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:04 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:04 DEBUG  WindowsBackend: windows_language=English
03-17 18:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:04 DEBUG  WindowsBackend: bootloader=vista
03-17 18:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401635.65625 mb free ntfs)
03-17 18:04 DEBUG  WindowsBackend: drive=Drive(C: hd 401635.65625 mb free ntfs)
03-17 18:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:04 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:04 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:04 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:04 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:04 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:04 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:04 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:04 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:04 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:04 DEBUG  CommonBackend: Searching for local CDs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Kubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Kubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Xubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Xubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Mythbuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp is a valid Mythbuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:04 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:04 INFO   root: Running the CD menu...
03-17 18:04 DEBUG  WindowsFrontend: __init__...
03-17 18:04 DEBUG  WindowsFrontend: on_init...
03-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\translations, languages=['en_US', 'en']
03-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6C2A.tmp\translations, languages=['en_US', 'en']
03-17 18:04 INFO   root: CD menu finished
03-17 18:04 DEBUG  CommonBackend: Showing info
03-17 18:04 DEBUG  root: application.quit
03-17 18:04 DEBUG  WindowsFrontend: frontend.quit
03-17 18:04 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:04 DEBUG  root: application.on_quit
03-17 18:04 INFO   root: sys.exit
03-17 18:04 INFO   root: === wubi 11.10 rev241 ===
03-17 18:04 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:04 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\data
03-17 18:04 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\bin\7z.exe
03-17 18:04 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:04 DEBUG  CommonBackend: Fetching basic info...
03-17 18:04 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:04 DEBUG  CommonBackend: platform=win32
03-17 18:04 DEBUG  CommonBackend: osname=nt
03-17 18:04 DEBUG  CommonBackend: language=en_US
03-17 18:04 DEBUG  CommonBackend: encoding=cp1252
03-17 18:04 DEBUG  WindowsBackend: arch=amd64
03-17 18:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\data\isolist.ini
03-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:04 DEBUG  WindowsBackend: Fetching host info...
03-17 18:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:04 DEBUG  WindowsBackend: windows version=vista
03-17 18:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:04 DEBUG  WindowsBackend: windows_sp=None
03-17 18:04 DEBUG  WindowsBackend: windows_build=7601
03-17 18:04 DEBUG  WindowsBackend: gmt=5
03-17 18:04 DEBUG  WindowsBackend: country=US
03-17 18:04 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:04 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:04 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:04 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:04 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:04 DEBUG  WindowsBackend: windows_language=English
03-17 18:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:04 DEBUG  WindowsBackend: bootloader=vista
03-17 18:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401635.136719 mb free ntfs)
03-17 18:04 DEBUG  WindowsBackend: drive=Drive(C: hd 401635.136719 mb free ntfs)
03-17 18:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:04 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:04 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:04 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:04 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:04 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:04 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:04 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:04 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:04 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:04 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:04 DEBUG  CommonBackend: Searching for local CDs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Kubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Kubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Xubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Xubuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Mythbuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE790.tmp is a valid Mythbuntu CD
03-17 18:04 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\casper\filesystem.squashfs
03-17 18:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:04 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:04 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:04 INFO   root: Running the CD menu...
03-17 18:04 DEBUG  WindowsFrontend: __init__...
03-17 18:04 DEBUG  WindowsFrontend: on_init...
03-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\translations, languages=['en_US', 'en']
03-17 18:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylE790.tmp\translations, languages=['en_US', 'en']
03-17 18:05 INFO   root: CD menu finished
03-17 18:05 INFO   root: Rebooting
03-17 18:05 DEBUG  TaskList: # Running tasklist...
03-17 18:05 DEBUG  TaskList: ## Running reboot...
03-17 18:05 DEBUG  TaskList: ## Finished reboot
03-17 18:05 DEBUG  TaskList: # Finished tasklist
03-17 18:05 DEBUG  root: application.quit
03-17 18:05 DEBUG  WindowsFrontend: frontend.quit
03-17 18:05 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:05 DEBUG  root: application.on_quit
03-17 18:05 INFO   root: sys.exit
03-17 18:07 INFO   root: === wubi 11.10 rev241 ===
03-17 18:07 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:07 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\data
03-17 18:07 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\bin\7z.exe
03-17 18:07 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:07 DEBUG  CommonBackend: Fetching basic info...
03-17 18:07 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:07 DEBUG  CommonBackend: platform=win32
03-17 18:07 DEBUG  CommonBackend: osname=nt
03-17 18:07 DEBUG  CommonBackend: language=en_US
03-17 18:07 DEBUG  CommonBackend: encoding=cp1252
03-17 18:07 DEBUG  WindowsBackend: arch=amd64
03-17 18:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\data\isolist.ini
03-17 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:07 DEBUG  WindowsBackend: Fetching host info...
03-17 18:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:07 DEBUG  WindowsBackend: windows version=vista
03-17 18:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:07 DEBUG  WindowsBackend: windows_sp=None
03-17 18:07 DEBUG  WindowsBackend: windows_build=7601
03-17 18:07 DEBUG  WindowsBackend: gmt=5
03-17 18:07 DEBUG  WindowsBackend: country=US
03-17 18:07 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:07 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:07 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:07 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:07 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:07 DEBUG  WindowsBackend: windows_language=English
03-17 18:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:07 DEBUG  WindowsBackend: bootloader=vista
03-17 18:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401678.796875 mb free ntfs)
03-17 18:07 DEBUG  WindowsBackend: drive=Drive(C: hd 401678.796875 mb free ntfs)
03-17 18:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:07 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:07 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:07 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:07 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:07 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:07 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:07 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:07 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:07 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:07 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:07 DEBUG  CommonBackend: Searching for local CDs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Ubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Ubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Kubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Kubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Xubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Xubuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Mythbuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp is a valid Mythbuntu CD
03-17 18:07 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\casper\filesystem.squashfs
03-17 18:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:07 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:07 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:07 INFO   root: Running the CD menu...
03-17 18:07 DEBUG  WindowsFrontend: __init__...
03-17 18:07 DEBUG  WindowsFrontend: on_init...
03-17 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\translations, languages=['en_US', 'en']
03-17 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\translations, languages=['en_US', 'en']
03-17 18:07 INFO   root: CD menu finished
03-17 18:07 INFO   root: Running the CD boot helper...
03-17 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\translations, languages=['en_US', 'en']
03-17 18:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl4D83.tmp\translations, languages=['en_US', 'en']
03-17 18:07 INFO   WindowsFrontend: Operation cancelled
03-17 18:07 DEBUG  WindowsFrontend: frontend.quit
03-17 18:07 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:07 DEBUG  root: application.on_quit
03-17 18:07 INFO   root: sys.exit
03-17 18:39 INFO   root: === wubi 11.10 rev241 ===
03-17 18:39 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:39 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\data
03-17 18:39 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\bin\7z.exe
03-17 18:39 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:39 DEBUG  CommonBackend: Fetching basic info...
03-17 18:39 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:39 DEBUG  CommonBackend: platform=win32
03-17 18:39 DEBUG  CommonBackend: osname=nt
03-17 18:39 DEBUG  CommonBackend: language=en_US
03-17 18:39 DEBUG  CommonBackend: encoding=cp1252
03-17 18:39 DEBUG  WindowsBackend: arch=amd64
03-17 18:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\data\isolist.ini
03-17 18:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:39 DEBUG  WindowsBackend: Fetching host info...
03-17 18:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:39 DEBUG  WindowsBackend: windows version=vista
03-17 18:39 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:39 DEBUG  WindowsBackend: windows_sp=None
03-17 18:39 DEBUG  WindowsBackend: windows_build=7601
03-17 18:39 DEBUG  WindowsBackend: gmt=5
03-17 18:39 DEBUG  WindowsBackend: country=US
03-17 18:39 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:39 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:39 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:39 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:39 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:39 DEBUG  WindowsBackend: windows_language=English
03-17 18:39 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:39 DEBUG  WindowsBackend: bootloader=vista
03-17 18:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401672.050781 mb free ntfs)
03-17 18:39 DEBUG  WindowsBackend: drive=Drive(C: hd 401672.050781 mb free ntfs)
03-17 18:39 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:39 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:39 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:39 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:39 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:39 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:39 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:39 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:39 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:39 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:39 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:39 DEBUG  CommonBackend: Searching for local CDs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Ubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Ubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Kubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Kubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Xubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Xubuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Mythbuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp is a valid Mythbuntu CD
03-17 18:39 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\casper\filesystem.squashfs
03-17 18:39 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:39 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:39 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:39 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:39 INFO   root: Running the CD menu...
03-17 18:39 DEBUG  WindowsFrontend: __init__...
03-17 18:39 DEBUG  WindowsFrontend: on_init...
03-17 18:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\translations, languages=['en_US', 'en']
03-17 18:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\translations, languages=['en_US', 'en']
03-17 18:39 INFO   root: CD menu finished
03-17 18:39 INFO   root: Running the CD boot helper...
03-17 18:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\translations, languages=['en_US', 'en']
03-17 18:39 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl8B1F.tmp\translations, languages=['en_US', 'en']
03-17 18:39 INFO   WindowsFrontend: Operation cancelled
03-17 18:39 DEBUG  WindowsFrontend: frontend.quit
03-17 18:39 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:39 DEBUG  root: application.on_quit
03-17 18:39 INFO   root: sys.exit
03-17 18:46 INFO   root: === wubi 11.10 rev241 ===
03-17 18:46 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-17 18:46 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\data
03-17 18:46 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\bin\7z.exe
03-17 18:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:46 DEBUG  CommonBackend: Fetching basic info...
03-17 18:46 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-17 18:46 DEBUG  CommonBackend: platform=win32
03-17 18:46 DEBUG  CommonBackend: osname=nt
03-17 18:46 DEBUG  CommonBackend: language=en_US
03-17 18:46 DEBUG  CommonBackend: encoding=cp1252
03-17 18:46 DEBUG  WindowsBackend: arch=amd64
03-17 18:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\data\isolist.ini
03-17 18:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:46 DEBUG  WindowsBackend: Fetching host info...
03-17 18:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:46 DEBUG  WindowsBackend: windows version=vista
03-17 18:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:46 DEBUG  WindowsBackend: windows_sp=None
03-17 18:46 DEBUG  WindowsBackend: windows_build=7601
03-17 18:46 DEBUG  WindowsBackend: gmt=5
03-17 18:46 DEBUG  WindowsBackend: country=US
03-17 18:46 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:46 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:46 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:46 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:46 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:46 DEBUG  WindowsBackend: windows_language=English
03-17 18:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:46 DEBUG  WindowsBackend: bootloader=vista
03-17 18:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401671.074219 mb free ntfs)
03-17 18:46 DEBUG  WindowsBackend: drive=Drive(C: hd 401671.074219 mb free ntfs)
03-17 18:46 DEBUG  WindowsBackend: drive=Drive(E: removable 1185.171875 mb free fat32)
03-17 18:46 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
03-17 18:46 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:46 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:46 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:46 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:46 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:46 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:46 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:46 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:46 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:46 DEBUG  CommonBackend: Searching for local CDs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Ubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Ubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Kubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Kubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Xubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Xubuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Mythbuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp is a valid Mythbuntu CD
03-17 18:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\casper\filesystem.squashfs
03-17 18:46 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 18:46 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:46 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-17 18:46 INFO   root: Running the CD menu...
03-17 18:46 DEBUG  WindowsFrontend: __init__...
03-17 18:46 DEBUG  WindowsFrontend: on_init...
03-17 18:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\translations, languages=['en_US', 'en']
03-17 18:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylF4BA.tmp\translations, languages=['en_US', 'en']
03-17 18:46 INFO   WindowsFrontend: Operation cancelled
03-17 18:46 DEBUG  WindowsFrontend: frontend.quit
03-17 18:46 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:46 DEBUG  root: application.on_quit
03-17 18:46 INFO   root: sys.exit
03-17 18:47 INFO   root: === wubi 11.10 rev241 ===
03-17 18:47 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:47 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-17 18:47 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\data
03-17 18:47 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\bin\7z.exe
03-17 18:47 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:47 DEBUG  CommonBackend: Fetching basic info...
03-17 18:47 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-17 18:47 DEBUG  CommonBackend: platform=win32
03-17 18:47 DEBUG  CommonBackend: osname=nt
03-17 18:47 DEBUG  CommonBackend: language=en_US
03-17 18:47 DEBUG  CommonBackend: encoding=cp1252
03-17 18:47 DEBUG  WindowsBackend: arch=amd64
03-17 18:47 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\data\isolist.ini
03-17 18:47 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:47 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:47 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:47 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:47 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:47 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:47 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:47 DEBUG  WindowsBackend: Fetching host info...
03-17 18:47 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:47 DEBUG  WindowsBackend: windows version=vista
03-17 18:47 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:47 DEBUG  WindowsBackend: windows_sp=None
03-17 18:47 DEBUG  WindowsBackend: windows_build=7601
03-17 18:47 DEBUG  WindowsBackend: gmt=5
03-17 18:47 DEBUG  WindowsBackend: country=US
03-17 18:47 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:47 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:47 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:47 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:47 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:47 DEBUG  WindowsBackend: windows_language=English
03-17 18:47 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:47 DEBUG  WindowsBackend: bootloader=vista
03-17 18:47 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401667.140625 mb free ntfs)
03-17 18:47 DEBUG  WindowsBackend: drive=Drive(C: hd 401667.140625 mb free ntfs)
03-17 18:47 DEBUG  WindowsBackend: drive=Drive(E: removable 1185.171875 mb free fat32)
03-17 18:47 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:47 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:47 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:47 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:47 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:47 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:47 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:47 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:47 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:47 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:47 DEBUG  CommonBackend: Searching for local CDs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Ubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Ubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Kubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Kubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Xubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Xubuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Mythbuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA488.tmp is a valid Mythbuntu CD
03-17 18:47 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\casper\filesystem.squashfs
03-17 18:47 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 18:47 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:47 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:47 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-17 18:47 INFO   root: Running the CD menu...
03-17 18:47 DEBUG  WindowsFrontend: __init__...
03-17 18:47 DEBUG  WindowsFrontend: on_init...
03-17 18:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\translations, languages=['en_US', 'en']
03-17 18:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\translations, languages=['en_US', 'en']
03-17 18:47 INFO   root: CD menu finished
03-17 18:47 INFO   root: Running the CD boot helper...
03-17 18:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\translations, languages=['en_US', 'en']
03-17 18:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\translations, languages=['en_US', 'en']
03-17 18:47 INFO   root: CD boot helper confirmed
03-17 18:47 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\translations, languages=['en_US', 'en']
03-17 18:47 DEBUG  TaskList: # Running tasklist...
03-17 18:47 DEBUG  TaskList: ## Running select_target_dir...
03-17 18:47 INFO   WindowsBackend: Installing into C:\ubuntu
03-17 18:47 DEBUG  TaskList: ## Finished select_target_dir
03-17 18:47 DEBUG  TaskList: ## Running create_dir_structure...
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-17 18:47 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-17 18:47 DEBUG  TaskList: ## Finished create_dir_structure
03-17 18:47 DEBUG  TaskList: ## Running uncompress_target_dir...
03-17 18:47 DEBUG  TaskList: ## Finished uncompress_target_dir
03-17 18:47 DEBUG  TaskList: ## Running create_uninstaller...
03-17 18:47 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-17 18:47 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-17 18:47 DEBUG  TaskList: ## Finished create_uninstaller
03-17 18:47 DEBUG  TaskList: ## Running copy_installation_files...
03-17 18:47 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-17 18:47 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\winboot -> C:\ubuntu\winboot
03-17 18:47 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA488.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-17 18:47 DEBUG  TaskList: ## Finished copy_installation_files
03-17 18:47 DEBUG  TaskList: ## Running use_cd...
03-17 18:47 ERROR  TaskList: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:47 DEBUG  TaskList: # Cancelling tasklist
03-17 18:47 DEBUG  TaskList: # Finished tasklist
03-17 18:47 ERROR  root: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:48 INFO   root: === wubi 11.10 rev241 ===
03-17 18:48 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-17 18:48 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\data
03-17 18:48 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\bin\7z.exe
03-17 18:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:48 DEBUG  CommonBackend: Fetching basic info...
03-17 18:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-17 18:48 DEBUG  CommonBackend: platform=win32
03-17 18:48 DEBUG  CommonBackend: osname=nt
03-17 18:48 DEBUG  CommonBackend: language=en_US
03-17 18:48 DEBUG  CommonBackend: encoding=cp1252
03-17 18:48 DEBUG  WindowsBackend: arch=amd64
03-17 18:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\data\isolist.ini
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:48 DEBUG  WindowsBackend: Fetching host info...
03-17 18:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:48 DEBUG  WindowsBackend: windows version=vista
03-17 18:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:48 DEBUG  WindowsBackend: windows_sp=None
03-17 18:48 DEBUG  WindowsBackend: windows_build=7601
03-17 18:48 DEBUG  WindowsBackend: gmt=5
03-17 18:48 DEBUG  WindowsBackend: country=US
03-17 18:48 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:48 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:48 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:48 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:48 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:48 DEBUG  WindowsBackend: windows_language=English
03-17 18:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:48 DEBUG  WindowsBackend: bootloader=vista
03-17 18:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401664.980469 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(C: hd 401664.980469 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(E: removable 1185.171875 mb free fat32)
03-17 18:48 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-17 18:48 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-17 18:48 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-17 18:48 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:48 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:48 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:48 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:48 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:48 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:48 DEBUG  CommonBackend: Searching for local CDs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:48 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-17 18:48 INFO   root: Running the CD menu...
03-17 18:48 DEBUG  WindowsFrontend: __init__...
03-17 18:48 DEBUG  WindowsFrontend: on_init...
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   root: CD menu finished
03-17 18:48 INFO   root: Already installed, running the uninstaller...
03-17 18:48 INFO   root: Running the uninstaller...
03-17 18:48 INFO   CommonBackend: This is the uninstaller running
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   root: Received settings
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 DEBUG  TaskList: # Running tasklist...
03-17 18:48 DEBUG  TaskList: ## Running Remove bootloader entry...
03-17 18:48 DEBUG  WindowsBackend: Could not find bcd id
03-17 18:48 DEBUG  WindowsBackend: undo_bootini C:
03-17 18:48 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 401664.980469 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: undo_bootini E:
03-17 18:48 DEBUG  WindowsBackend: undo_configsys Drive(E: removable 1185.171875 mb free fat32)
03-17 18:48 DEBUG  TaskList: ## Finished Remove bootloader entry
03-17 18:48 DEBUG  TaskList: ## Running Remove target dir...
03-17 18:48 DEBUG  CommonBackend: Deleting C:\ubuntu
03-17 18:48 DEBUG  TaskList: ## Finished Remove target dir
03-17 18:48 DEBUG  TaskList: ## Running Remove registry key...
03-17 18:48 DEBUG  TaskList: ## Finished Remove registry key
03-17 18:48 DEBUG  TaskList: # Finished tasklist
03-17 18:48 INFO   root: Almost finished uninstalling
03-17 18:48 INFO   root: Finished uninstallation
03-17 18:48 DEBUG  CommonBackend: Fetching basic info...
03-17 18:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-17 18:48 DEBUG  CommonBackend: platform=win32
03-17 18:48 DEBUG  CommonBackend: osname=nt
03-17 18:48 DEBUG  WindowsBackend: arch=amd64
03-17 18:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\data\isolist.ini
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:48 DEBUG  WindowsBackend: Fetching host info...
03-17 18:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:48 DEBUG  WindowsBackend: windows version=vista
03-17 18:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:48 DEBUG  WindowsBackend: windows_sp=None
03-17 18:48 DEBUG  WindowsBackend: windows_build=7601
03-17 18:48 DEBUG  WindowsBackend: gmt=5
03-17 18:48 DEBUG  WindowsBackend: country=US
03-17 18:48 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:48 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:48 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:48 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:48 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:48 DEBUG  WindowsBackend: windows_language=English
03-17 18:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:48 DEBUG  WindowsBackend: bootloader=vista
03-17 18:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401666.867188 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(C: hd 401666.867188 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(E: removable 1185.171875 mb free fat32)
03-17 18:48 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:48 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:48 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:48 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:48 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:48 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:48 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:48 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:48 DEBUG  CommonBackend: Searching for local CDs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 18:48 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-17 18:48 INFO   root: Running the CD boot helper...
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl6325.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   WindowsFrontend: Operation cancelled
03-17 18:48 DEBUG  WindowsFrontend: frontend.quit
03-17 18:48 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:48 DEBUG  root: application.on_quit
03-17 18:48 INFO   root: sys.exit
03-17 18:48 INFO   root: === wubi 11.10 rev241 ===
03-17 18:48 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:48 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
03-17 18:48 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\data
03-17 18:48 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\bin\7z.exe
03-17 18:48 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:48 DEBUG  CommonBackend: Fetching basic info...
03-17 18:48 DEBUG  CommonBackend: original_exe=E:\wubi.exe
03-17 18:48 DEBUG  CommonBackend: platform=win32
03-17 18:48 DEBUG  CommonBackend: osname=nt
03-17 18:48 DEBUG  CommonBackend: language=en_US
03-17 18:48 DEBUG  CommonBackend: encoding=cp1252
03-17 18:48 DEBUG  WindowsBackend: arch=amd64
03-17 18:48 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\data\isolist.ini
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:48 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:48 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:48 DEBUG  WindowsBackend: Fetching host info...
03-17 18:48 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:48 DEBUG  WindowsBackend: windows version=vista
03-17 18:48 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:48 DEBUG  WindowsBackend: windows_sp=None
03-17 18:48 DEBUG  WindowsBackend: windows_build=7601
03-17 18:48 DEBUG  WindowsBackend: gmt=5
03-17 18:48 DEBUG  WindowsBackend: country=US
03-17 18:48 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:48 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:48 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:48 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:48 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:48 DEBUG  WindowsBackend: windows_language=English
03-17 18:48 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:48 DEBUG  WindowsBackend: bootloader=vista
03-17 18:48 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401666.882813 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(C: hd 401666.882813 mb free ntfs)
03-17 18:48 DEBUG  WindowsBackend: drive=Drive(E: removable 1185.171875 mb free fat32)
03-17 18:48 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:48 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:48 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:48 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:48 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:48 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:48 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:48 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:48 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:48 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:48 DEBUG  CommonBackend: Searching for local CDs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Kubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Xubuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp is a valid Mythbuntu CD
03-17 18:48 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\casper\filesystem.squashfs
03-17 18:48 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
03-17 18:48 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:48 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:48 INFO   Distro: Found a valid CD for Ubuntu: E:\
03-17 18:48 INFO   root: Running the CD menu...
03-17 18:48 DEBUG  WindowsFrontend: __init__...
03-17 18:48 DEBUG  WindowsFrontend: on_init...
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   root: CD menu finished
03-17 18:48 INFO   root: Running the CD boot helper...
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\translations, languages=['en_US', 'en']
03-17 18:48 INFO   root: CD boot helper confirmed
03-17 18:48 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\translations, languages=['en_US', 'en']
03-17 18:48 DEBUG  TaskList: # Running tasklist...
03-17 18:48 DEBUG  TaskList: ## Running select_target_dir...
03-17 18:48 INFO   WindowsBackend: Installing into C:\ubuntu
03-17 18:48 DEBUG  TaskList: ## Finished select_target_dir
03-17 18:48 DEBUG  TaskList: ## Running create_dir_structure...
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-17 18:48 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-17 18:48 DEBUG  TaskList: ## Finished create_dir_structure
03-17 18:48 DEBUG  TaskList: ## Running uncompress_target_dir...
03-17 18:48 DEBUG  TaskList: ## Finished uncompress_target_dir
03-17 18:48 DEBUG  TaskList: ## Running create_uninstaller...
03-17 18:48 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-17 18:48 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-17 18:48 DEBUG  TaskList: ## Finished create_uninstaller
03-17 18:48 DEBUG  TaskList: ## Running copy_installation_files...
03-17 18:48 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-17 18:48 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\winboot -> C:\ubuntu\winboot
03-17 18:48 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylA0E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-17 18:48 DEBUG  TaskList: ## Finished copy_installation_files
03-17 18:48 DEBUG  TaskList: ## Running use_cd...
03-17 18:48 ERROR  TaskList: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:48 DEBUG  TaskList: # Cancelling tasklist
03-17 18:48 DEBUG  TaskList: # Finished tasklist
03-17 18:48 ERROR  root: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:53 INFO   root: === wubi 11.10 rev241 ===
03-17 18:53 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:53 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:53 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\data
03-17 18:53 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\bin\7z.exe
03-17 18:53 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:53 DEBUG  CommonBackend: Fetching basic info...
03-17 18:53 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:53 DEBUG  CommonBackend: platform=win32
03-17 18:53 DEBUG  CommonBackend: osname=nt
03-17 18:53 DEBUG  CommonBackend: language=en_US
03-17 18:53 DEBUG  CommonBackend: encoding=cp1252
03-17 18:53 DEBUG  WindowsBackend: arch=amd64
03-17 18:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\data\isolist.ini
03-17 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:53 DEBUG  WindowsBackend: Fetching host info...
03-17 18:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:53 DEBUG  WindowsBackend: windows version=vista
03-17 18:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:53 DEBUG  WindowsBackend: windows_sp=None
03-17 18:53 DEBUG  WindowsBackend: windows_build=7601
03-17 18:53 DEBUG  WindowsBackend: gmt=5
03-17 18:53 DEBUG  WindowsBackend: country=US
03-17 18:53 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:53 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:53 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:53 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:53 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:53 DEBUG  WindowsBackend: windows_language=English
03-17 18:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:53 DEBUG  WindowsBackend: bootloader=vista
03-17 18:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401667.601563 mb free ntfs)
03-17 18:53 DEBUG  WindowsBackend: drive=Drive(C: hd 401667.601563 mb free ntfs)
03-17 18:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:53 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-17 18:53 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-17 18:53 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-17 18:53 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:53 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:53 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:53 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:53 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:53 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:53 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:53 DEBUG  CommonBackend: Searching for local CDs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Ubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Ubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Kubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Kubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Xubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Xubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Mythbuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Mythbuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:53 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:53 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:53 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:53 INFO   root: Running the CD menu...
03-17 18:53 DEBUG  WindowsFrontend: __init__...
03-17 18:53 DEBUG  WindowsFrontend: on_init...
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:53 INFO   root: CD menu finished
03-17 18:53 INFO   root: Already installed, running the uninstaller...
03-17 18:53 INFO   root: Running the uninstaller...
03-17 18:53 INFO   CommonBackend: This is the uninstaller running
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:53 INFO   root: Received settings
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:53 DEBUG  TaskList: # Running tasklist...
03-17 18:53 DEBUG  TaskList: ## Running Remove bootloader entry...
03-17 18:53 DEBUG  WindowsBackend: Could not find bcd id
03-17 18:53 DEBUG  WindowsBackend: undo_bootini C:
03-17 18:53 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 401667.601563 mb free ntfs)
03-17 18:53 DEBUG  TaskList: ## Finished Remove bootloader entry
03-17 18:53 DEBUG  TaskList: ## Running Remove target dir...
03-17 18:53 DEBUG  CommonBackend: Deleting C:\ubuntu
03-17 18:53 DEBUG  TaskList: ## Finished Remove target dir
03-17 18:53 DEBUG  TaskList: ## Running Remove registry key...
03-17 18:53 DEBUG  TaskList: ## Finished Remove registry key
03-17 18:53 DEBUG  TaskList: # Finished tasklist
03-17 18:53 INFO   root: Almost finished uninstalling
03-17 18:53 INFO   root: Finished uninstallation
03-17 18:53 DEBUG  CommonBackend: Fetching basic info...
03-17 18:53 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:53 DEBUG  CommonBackend: platform=win32
03-17 18:53 DEBUG  CommonBackend: osname=nt
03-17 18:53 DEBUG  WindowsBackend: arch=amd64
03-17 18:53 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\data\isolist.ini
03-17 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:53 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:53 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:53 DEBUG  WindowsBackend: Fetching host info...
03-17 18:53 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:53 DEBUG  WindowsBackend: windows version=vista
03-17 18:53 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:53 DEBUG  WindowsBackend: windows_sp=None
03-17 18:53 DEBUG  WindowsBackend: windows_build=7601
03-17 18:53 DEBUG  WindowsBackend: gmt=5
03-17 18:53 DEBUG  WindowsBackend: country=US
03-17 18:53 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:53 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:53 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:53 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:53 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:53 DEBUG  WindowsBackend: windows_language=English
03-17 18:53 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:53 DEBUG  WindowsBackend: bootloader=vista
03-17 18:53 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401670.050781 mb free ntfs)
03-17 18:53 DEBUG  WindowsBackend: drive=Drive(C: hd 401670.050781 mb free ntfs)
03-17 18:53 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:53 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:53 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:53 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:53 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:53 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:53 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:53 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:53 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:53 DEBUG  CommonBackend: Searching for local CDs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Ubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Ubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Kubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Kubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Xubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Xubuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Mythbuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp is a valid Mythbuntu CD
03-17 18:53 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\casper\filesystem.squashfs
03-17 18:53 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:53 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:53 INFO   root: Running the CD boot helper...
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:53 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   root: CD boot helper confirmed
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 DEBUG  TaskList: # Running tasklist...
03-17 18:54 DEBUG  TaskList: ## Running select_target_dir...
03-17 18:54 INFO   WindowsBackend: Installing into C:\ubuntu
03-17 18:54 DEBUG  TaskList: ## Finished select_target_dir
03-17 18:54 DEBUG  TaskList: ## Running create_dir_structure...
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
03-17 18:54 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
03-17 18:54 DEBUG  TaskList: ## Finished create_dir_structure
03-17 18:54 DEBUG  TaskList: ## Running uncompress_target_dir...
03-17 18:54 DEBUG  TaskList: ## Finished uncompress_target_dir
03-17 18:54 DEBUG  TaskList: ## Running create_uninstaller...
03-17 18:54 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev241
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
03-17 18:54 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
03-17 18:54 DEBUG  TaskList: ## Finished create_uninstaller
03-17 18:54 DEBUG  TaskList: ## Running copy_installation_files...
03-17 18:54 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
03-17 18:54 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\winboot -> C:\ubuntu\winboot
03-17 18:54 DEBUG  WindowsBackend: Copying C:\Users\DELL\AppData\Local\Temp\pylCD3D.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
03-17 18:54 DEBUG  TaskList: ## Finished copy_installation_files
03-17 18:54 DEBUG  TaskList: ## Running use_cd...
03-17 18:54 ERROR  TaskList: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:54 DEBUG  TaskList: # Cancelling tasklist
03-17 18:54 DEBUG  TaskList: # Finished tasklist
03-17 18:54 ERROR  root: 'WindowsBackend' object has no attribute 'cd_path'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 205, in run_cd_menu
  File "\lib\wubi\application.py", line 122, in select_task
  File "\lib\wubi\application.py", line 228, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 537, in use_cd
AttributeError: 'WindowsBackend' object has no attribute 'cd_path'
03-17 18:54 INFO   root: === wubi 11.10 rev241 ===
03-17 18:54 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 18:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 18:54 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\data
03-17 18:54 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\bin\7z.exe
03-17 18:54 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 18:54 DEBUG  CommonBackend: Fetching basic info...
03-17 18:54 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:54 DEBUG  CommonBackend: platform=win32
03-17 18:54 DEBUG  CommonBackend: osname=nt
03-17 18:54 DEBUG  CommonBackend: language=en_US
03-17 18:54 DEBUG  CommonBackend: encoding=cp1252
03-17 18:54 DEBUG  WindowsBackend: arch=amd64
03-17 18:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\data\isolist.ini
03-17 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:54 DEBUG  WindowsBackend: Fetching host info...
03-17 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:54 DEBUG  WindowsBackend: windows version=vista
03-17 18:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:54 DEBUG  WindowsBackend: windows_sp=None
03-17 18:54 DEBUG  WindowsBackend: windows_build=7601
03-17 18:54 DEBUG  WindowsBackend: gmt=5
03-17 18:54 DEBUG  WindowsBackend: country=US
03-17 18:54 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:54 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:54 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:54 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:54 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:54 DEBUG  WindowsBackend: windows_language=English
03-17 18:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:54 DEBUG  WindowsBackend: bootloader=vista
03-17 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401667.457031 mb free ntfs)
03-17 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 401667.457031 mb free ntfs)
03-17 18:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:54 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
03-17 18:54 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
03-17 18:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
03-17 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:54 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:54 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 18:54 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 18:54 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:54 DEBUG  CommonBackend: Searching for local CDs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Xubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Xubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:54 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 18:54 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 18:54 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:54 INFO   root: Running the CD menu...
03-17 18:54 DEBUG  WindowsFrontend: __init__...
03-17 18:54 DEBUG  WindowsFrontend: on_init...
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   root: CD menu finished
03-17 18:54 INFO   root: Already installed, running the uninstaller...
03-17 18:54 INFO   root: Running the uninstaller...
03-17 18:54 INFO   CommonBackend: This is the uninstaller running
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   root: Received settings
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 DEBUG  TaskList: # Running tasklist...
03-17 18:54 DEBUG  TaskList: ## Running Remove bootloader entry...
03-17 18:54 DEBUG  WindowsBackend: Could not find bcd id
03-17 18:54 DEBUG  WindowsBackend: undo_bootini C:
03-17 18:54 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 401667.457031 mb free ntfs)
03-17 18:54 DEBUG  TaskList: ## Finished Remove bootloader entry
03-17 18:54 DEBUG  TaskList: ## Running Remove target dir...
03-17 18:54 DEBUG  CommonBackend: Deleting C:\ubuntu
03-17 18:54 DEBUG  TaskList: ## Finished Remove target dir
03-17 18:54 DEBUG  TaskList: ## Running Remove registry key...
03-17 18:54 DEBUG  TaskList: ## Finished Remove registry key
03-17 18:54 DEBUG  TaskList: # Finished tasklist
03-17 18:54 INFO   root: Almost finished uninstalling
03-17 18:54 INFO   root: Finished uninstallation
03-17 18:54 DEBUG  CommonBackend: Fetching basic info...
03-17 18:54 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 18:54 DEBUG  CommonBackend: platform=win32
03-17 18:54 DEBUG  CommonBackend: osname=nt
03-17 18:54 DEBUG  WindowsBackend: arch=amd64
03-17 18:54 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\data\isolist.ini
03-17 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 18:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 18:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 18:54 DEBUG  WindowsBackend: Fetching host info...
03-17 18:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 18:54 DEBUG  WindowsBackend: windows version=vista
03-17 18:54 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 18:54 DEBUG  WindowsBackend: windows_sp=None
03-17 18:54 DEBUG  WindowsBackend: windows_build=7601
03-17 18:54 DEBUG  WindowsBackend: gmt=5
03-17 18:54 DEBUG  WindowsBackend: country=US
03-17 18:54 DEBUG  WindowsBackend: timezone=America/New_York
03-17 18:54 DEBUG  WindowsBackend: windows_username=DELL
03-17 18:54 DEBUG  WindowsBackend: user_full_name=DELL
03-17 18:54 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 18:54 DEBUG  WindowsBackend: windows_language_code=1033
03-17 18:54 DEBUG  WindowsBackend: windows_language=English
03-17 18:54 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 18:54 DEBUG  WindowsBackend: bootloader=vista
03-17 18:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 401669.882813 mb free ntfs)
03-17 18:54 DEBUG  WindowsBackend: drive=Drive(C: hd 401669.882813 mb free ntfs)
03-17 18:54 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 18:54 DEBUG  WindowsBackend: uninstaller_path=None
03-17 18:54 DEBUG  WindowsBackend: previous_target_dir=None
03-17 18:54 DEBUG  WindowsBackend: previous_distro_name=None
03-17 18:54 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 18:54 DEBUG  WindowsBackend: keyboard_layout=us
03-17 18:54 DEBUG  WindowsBackend: keyboard_variant=
03-17 18:54 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 18:54 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 18:54 DEBUG  CommonBackend: Searching for local CDs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Ubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Kubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Xubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Xubuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp is a valid Mythbuntu CD
03-17 18:54 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\casper\filesystem.squashfs
03-17 18:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 18:54 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 18:54 INFO   root: Running the CD boot helper...
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl841D.tmp\translations, languages=['en_US', 'en']
03-17 18:54 INFO   WindowsFrontend: Operation cancelled
03-17 18:54 DEBUG  WindowsFrontend: frontend.quit
03-17 18:54 DEBUG  WindowsFrontend: frontend.on_quit
03-17 18:54 DEBUG  root: application.on_quit
03-17 18:54 INFO   root: sys.exit
03-17 19:23 INFO   root: === wubi 11.10 rev241 ===
03-17 19:23 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 19:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\wubi.exe"']
03-17 19:23 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\data
03-17 19:23 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\bin\7z.exe
03-17 19:23 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 19:23 DEBUG  CommonBackend: Fetching basic info...
03-17 19:23 DEBUG  CommonBackend: original_exe=D:\wubi.exe
03-17 19:23 DEBUG  CommonBackend: platform=win32
03-17 19:23 DEBUG  CommonBackend: osname=nt
03-17 19:23 DEBUG  CommonBackend: language=en_US
03-17 19:23 DEBUG  CommonBackend: encoding=cp1252
03-17 19:23 DEBUG  WindowsBackend: arch=amd64
03-17 19:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\data\isolist.ini
03-17 19:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 19:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 19:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 19:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 19:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 19:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 19:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 19:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 19:23 DEBUG  WindowsBackend: Fetching host info...
03-17 19:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 19:23 DEBUG  WindowsBackend: windows version=vista
03-17 19:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 19:23 DEBUG  WindowsBackend: windows_sp=None
03-17 19:23 DEBUG  WindowsBackend: windows_build=7601
03-17 19:23 DEBUG  WindowsBackend: gmt=5
03-17 19:23 DEBUG  WindowsBackend: country=US
03-17 19:23 DEBUG  WindowsBackend: timezone=America/New_York
03-17 19:23 DEBUG  WindowsBackend: windows_username=DELL
03-17 19:23 DEBUG  WindowsBackend: user_full_name=DELL
03-17 19:23 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 19:23 DEBUG  WindowsBackend: windows_language_code=1033
03-17 19:23 DEBUG  WindowsBackend: windows_language=English
03-17 19:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 19:23 DEBUG  WindowsBackend: bootloader=vista
03-17 19:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 297003.71875 mb free ntfs)
03-17 19:23 DEBUG  WindowsBackend: drive=Drive(C: hd 297003.71875 mb free ntfs)
03-17 19:23 DEBUG  WindowsBackend: drive=Drive(D: removable 1185.12109375 mb free fat32)
03-17 19:23 DEBUG  WindowsBackend: uninstaller_path=None
03-17 19:23 DEBUG  WindowsBackend: previous_target_dir=None
03-17 19:23 DEBUG  WindowsBackend: previous_distro_name=None
03-17 19:23 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 19:23 DEBUG  WindowsBackend: keyboard_layout=us
03-17 19:23 DEBUG  WindowsBackend: keyboard_variant=
03-17 19:23 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 19:23 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 19:23 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 19:23 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 19:23 DEBUG  CommonBackend: Searching for local CDs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Ubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Ubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Kubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Kubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Xubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Xubuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Mythbuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp is a valid Mythbuntu CD
03-17 19:23 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\casper\filesystem.squashfs
03-17 19:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
03-17 19:23 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 19:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 19:23 INFO   Distro: Found a valid CD for Ubuntu: D:\
03-17 19:23 INFO   root: Running the CD menu...
03-17 19:23 DEBUG  WindowsFrontend: __init__...
03-17 19:23 DEBUG  WindowsFrontend: on_init...
03-17 19:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\translations, languages=['en_US', 'en']
03-17 19:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl203C.tmp\translations, languages=['en_US', 'en']
03-17 19:24 INFO   WindowsFrontend: Operation cancelled
03-17 19:24 DEBUG  WindowsFrontend: frontend.quit
03-17 19:24 DEBUG  WindowsFrontend: frontend.on_quit
03-17 19:24 DEBUG  root: application.on_quit
03-17 19:24 INFO   root: sys.exit
03-17 19:57 INFO   root: === wubi 11.10 rev241 ===
03-17 19:57 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 19:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 19:57 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\data
03-17 19:57 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\bin\7z.exe
03-17 19:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 19:57 DEBUG  CommonBackend: Fetching basic info...
03-17 19:57 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 19:57 DEBUG  CommonBackend: platform=win32
03-17 19:57 DEBUG  CommonBackend: osname=nt
03-17 19:57 DEBUG  CommonBackend: language=en_US
03-17 19:57 DEBUG  CommonBackend: encoding=cp1252
03-17 19:57 DEBUG  WindowsBackend: arch=amd64
03-17 19:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\data\isolist.ini
03-17 19:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 19:57 DEBUG  WindowsBackend: Fetching host info...
03-17 19:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 19:57 DEBUG  WindowsBackend: windows version=vista
03-17 19:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 19:57 DEBUG  WindowsBackend: windows_sp=None
03-17 19:57 DEBUG  WindowsBackend: windows_build=7601
03-17 19:57 DEBUG  WindowsBackend: gmt=5
03-17 19:57 DEBUG  WindowsBackend: country=US
03-17 19:57 DEBUG  WindowsBackend: timezone=America/New_York
03-17 19:57 DEBUG  WindowsBackend: windows_username=DELL
03-17 19:57 DEBUG  WindowsBackend: user_full_name=DELL
03-17 19:57 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 19:57 DEBUG  WindowsBackend: windows_language_code=1033
03-17 19:57 DEBUG  WindowsBackend: windows_language=English
03-17 19:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 19:57 DEBUG  WindowsBackend: bootloader=vista
03-17 19:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 403129.84375 mb free ntfs)
03-17 19:57 DEBUG  WindowsBackend: drive=Drive(C: hd 403129.84375 mb free ntfs)
03-17 19:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 19:57 DEBUG  WindowsBackend: uninstaller_path=None
03-17 19:57 DEBUG  WindowsBackend: previous_target_dir=None
03-17 19:57 DEBUG  WindowsBackend: previous_distro_name=None
03-17 19:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 19:57 DEBUG  WindowsBackend: keyboard_layout=us
03-17 19:57 DEBUG  WindowsBackend: keyboard_variant=
03-17 19:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 19:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 19:57 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 19:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 19:57 DEBUG  CommonBackend: Searching for local CDs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Kubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Kubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Xubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Xubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Mythbuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp is a valid Mythbuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 19:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 19:57 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 19:57 INFO   root: Running the CD menu...
03-17 19:57 DEBUG  WindowsFrontend: __init__...
03-17 19:57 DEBUG  WindowsFrontend: on_init...
03-17 19:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\translations, languages=['en_US', 'en']
03-17 19:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylDAE4.tmp\translations, languages=['en_US', 'en']
03-17 19:57 DEBUG  root: application.quit
03-17 19:57 DEBUG  WindowsFrontend: frontend.quit
03-17 19:57 DEBUG  WindowsFrontend: frontend.on_quit
03-17 19:57 DEBUG  root: application.on_quit
03-17 19:57 INFO   root: sys.exit
03-17 19:57 INFO   root: === wubi 11.10 rev241 ===
03-17 19:57 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 19:57 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 19:57 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\data
03-17 19:57 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\bin\7z.exe
03-17 19:57 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 19:57 DEBUG  CommonBackend: Fetching basic info...
03-17 19:57 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 19:57 DEBUG  CommonBackend: platform=win32
03-17 19:57 DEBUG  CommonBackend: osname=nt
03-17 19:57 DEBUG  CommonBackend: language=en_US
03-17 19:57 DEBUG  CommonBackend: encoding=cp1252
03-17 19:57 DEBUG  WindowsBackend: arch=amd64
03-17 19:57 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\data\isolist.ini
03-17 19:57 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 19:57 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 19:57 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 19:57 DEBUG  WindowsBackend: Fetching host info...
03-17 19:57 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 19:57 DEBUG  WindowsBackend: windows version=vista
03-17 19:57 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 19:57 DEBUG  WindowsBackend: windows_sp=None
03-17 19:57 DEBUG  WindowsBackend: windows_build=7601
03-17 19:57 DEBUG  WindowsBackend: gmt=5
03-17 19:57 DEBUG  WindowsBackend: country=US
03-17 19:57 DEBUG  WindowsBackend: timezone=America/New_York
03-17 19:57 DEBUG  WindowsBackend: windows_username=DELL
03-17 19:57 DEBUG  WindowsBackend: user_full_name=DELL
03-17 19:57 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 19:57 DEBUG  WindowsBackend: windows_language_code=1033
03-17 19:57 DEBUG  WindowsBackend: windows_language=English
03-17 19:57 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 19:57 DEBUG  WindowsBackend: bootloader=vista
03-17 19:57 DEBUG  WindowsBackend: system_drive=Drive(C: hd 403129.882813 mb free ntfs)
03-17 19:57 DEBUG  WindowsBackend: drive=Drive(C: hd 403129.882813 mb free ntfs)
03-17 19:57 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 19:57 DEBUG  WindowsBackend: uninstaller_path=None
03-17 19:57 DEBUG  WindowsBackend: previous_target_dir=None
03-17 19:57 DEBUG  WindowsBackend: previous_distro_name=None
03-17 19:57 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 19:57 DEBUG  WindowsBackend: keyboard_layout=us
03-17 19:57 DEBUG  WindowsBackend: keyboard_variant=
03-17 19:57 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 19:57 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 19:57 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 19:57 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 19:57 DEBUG  CommonBackend: Searching for local CDs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Kubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Kubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Xubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Xubuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Mythbuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp is a valid Mythbuntu CD
03-17 19:57 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\casper\filesystem.squashfs
03-17 19:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 19:57 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 19:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 19:57 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 19:57 INFO   root: Running the CD menu...
03-17 19:57 DEBUG  WindowsFrontend: __init__...
03-17 19:57 DEBUG  WindowsFrontend: on_init...
03-17 19:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\translations, languages=['en_US', 'en']
03-17 19:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pyl423D.tmp\translations, languages=['en_US', 'en']
03-17 19:58 INFO   root: CD menu finished
03-17 19:58 INFO   root: Rebooting
03-17 19:58 DEBUG  TaskList: # Running tasklist...
03-17 19:58 DEBUG  TaskList: ## Running reboot...
03-17 19:58 DEBUG  TaskList: ## Finished reboot
03-17 19:58 DEBUG  TaskList: # Finished tasklist
03-17 19:58 DEBUG  root: application.quit
03-17 19:58 DEBUG  WindowsFrontend: frontend.quit
03-17 19:58 DEBUG  WindowsFrontend: frontend.on_quit
03-17 19:58 DEBUG  root: application.on_quit
03-17 19:58 INFO   root: sys.exit
03-17 20:38 INFO   root: === wubi 11.10 rev241 ===
03-17 20:38 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 20:38 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 20:38 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\data
03-17 20:38 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\bin\7z.exe
03-17 20:38 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 20:38 DEBUG  CommonBackend: Fetching basic info...
03-17 20:38 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 20:38 DEBUG  CommonBackend: platform=win32
03-17 20:38 DEBUG  CommonBackend: osname=nt
03-17 20:38 DEBUG  CommonBackend: language=en_US
03-17 20:38 DEBUG  CommonBackend: encoding=cp1252
03-17 20:38 DEBUG  WindowsBackend: arch=amd64
03-17 20:38 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\data\isolist.ini
03-17 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 20:38 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 20:38 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 20:38 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 20:38 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 20:38 DEBUG  WindowsBackend: Fetching host info...
03-17 20:38 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 20:38 DEBUG  WindowsBackend: windows version=vista
03-17 20:38 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 20:38 DEBUG  WindowsBackend: windows_sp=None
03-17 20:38 DEBUG  WindowsBackend: windows_build=7601
03-17 20:38 DEBUG  WindowsBackend: gmt=5
03-17 20:38 DEBUG  WindowsBackend: country=US
03-17 20:38 DEBUG  WindowsBackend: timezone=America/New_York
03-17 20:38 DEBUG  WindowsBackend: windows_username=DELL
03-17 20:38 DEBUG  WindowsBackend: user_full_name=DELL
03-17 20:38 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 20:38 DEBUG  WindowsBackend: windows_language_code=1033
03-17 20:38 DEBUG  WindowsBackend: windows_language=English
03-17 20:38 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 20:38 DEBUG  WindowsBackend: bootloader=vista
03-17 20:38 DEBUG  WindowsBackend: system_drive=Drive(C: hd 298460.878906 mb free ntfs)
03-17 20:38 DEBUG  WindowsBackend: drive=Drive(C: hd 298460.878906 mb free ntfs)
03-17 20:38 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 20:38 DEBUG  WindowsBackend: uninstaller_path=None
03-17 20:38 DEBUG  WindowsBackend: previous_target_dir=None
03-17 20:38 DEBUG  WindowsBackend: previous_distro_name=None
03-17 20:38 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 20:38 DEBUG  WindowsBackend: keyboard_layout=us
03-17 20:38 DEBUG  WindowsBackend: keyboard_variant=
03-17 20:38 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 20:38 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 20:38 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 20:38 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 20:38 DEBUG  CommonBackend: Searching for local CDs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Ubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Ubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Kubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Kubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Xubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Xubuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Mythbuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp is a valid Mythbuntu CD
03-17 20:38 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\casper\filesystem.squashfs
03-17 20:38 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 20:38 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 20:38 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 20:38 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 20:38 INFO   root: Running the CD menu...
03-17 20:38 DEBUG  WindowsFrontend: __init__...
03-17 20:38 DEBUG  WindowsFrontend: on_init...
03-17 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\translations, languages=['en_US', 'en']
03-17 20:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylB54A.tmp\translations, languages=['en_US', 'en']
03-17 20:39 INFO   root: CD menu finished
03-17 20:39 DEBUG  CommonBackend: Showing info
03-17 20:39 DEBUG  root: application.quit
03-17 20:39 DEBUG  WindowsFrontend: frontend.quit
03-17 20:39 DEBUG  WindowsFrontend: frontend.on_quit
03-17 20:39 DEBUG  root: application.on_quit
03-17 20:39 INFO   root: sys.exit
03-17 20:46 INFO   root: === wubi 11.10 rev241 ===
03-17 20:46 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 20:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 20:46 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\data
03-17 20:46 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\bin\7z.exe
03-17 20:46 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 20:46 DEBUG  CommonBackend: Fetching basic info...
03-17 20:46 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 20:46 DEBUG  CommonBackend: platform=win32
03-17 20:46 DEBUG  CommonBackend: osname=nt
03-17 20:46 DEBUG  CommonBackend: language=en_US
03-17 20:46 DEBUG  CommonBackend: encoding=cp1252
03-17 20:46 DEBUG  WindowsBackend: arch=amd64
03-17 20:46 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\data\isolist.ini
03-17 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 20:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 20:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 20:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 20:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 20:46 DEBUG  WindowsBackend: Fetching host info...
03-17 20:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 20:46 DEBUG  WindowsBackend: windows version=vista
03-17 20:46 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 20:46 DEBUG  WindowsBackend: windows_sp=None
03-17 20:46 DEBUG  WindowsBackend: windows_build=7601
03-17 20:46 DEBUG  WindowsBackend: gmt=5
03-17 20:46 DEBUG  WindowsBackend: country=US
03-17 20:46 DEBUG  WindowsBackend: timezone=America/New_York
03-17 20:46 DEBUG  WindowsBackend: windows_username=DELL
03-17 20:46 DEBUG  WindowsBackend: user_full_name=DELL
03-17 20:46 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 20:46 DEBUG  WindowsBackend: windows_language_code=1033
03-17 20:46 DEBUG  WindowsBackend: windows_language=English
03-17 20:46 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 20:46 DEBUG  WindowsBackend: bootloader=vista
03-17 20:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 298352.601563 mb free ntfs)
03-17 20:46 DEBUG  WindowsBackend: drive=Drive(C: hd 298352.601563 mb free ntfs)
03-17 20:46 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 20:46 DEBUG  WindowsBackend: uninstaller_path=None
03-17 20:46 DEBUG  WindowsBackend: previous_target_dir=None
03-17 20:46 DEBUG  WindowsBackend: previous_distro_name=None
03-17 20:46 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 20:46 DEBUG  WindowsBackend: keyboard_layout=us
03-17 20:46 DEBUG  WindowsBackend: keyboard_variant=
03-17 20:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 20:46 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 20:46 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 20:46 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 20:46 DEBUG  CommonBackend: Searching for local CDs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Ubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Ubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Kubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Kubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Xubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Xubuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Mythbuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylE752.tmp is a valid Mythbuntu CD
03-17 20:46 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\casper\filesystem.squashfs
03-17 20:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 20:46 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 20:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 20:46 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 20:46 INFO   root: Running the CD menu...
03-17 20:46 DEBUG  WindowsFrontend: __init__...
03-17 20:46 DEBUG  WindowsFrontend: on_init...
03-17 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\translations, languages=['en_US', 'en']
03-17 20:46 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylE752.tmp\translations, languages=['en_US', 'en']
03-17 20:54 INFO   WindowsFrontend: Operation cancelled
03-17 20:54 DEBUG  WindowsFrontend: frontend.quit
03-17 20:54 DEBUG  WindowsFrontend: frontend.on_quit
03-17 20:54 DEBUG  root: application.on_quit
03-17 20:54 INFO   root: sys.exit
03-17 21:00 INFO   root: === wubi 11.10 rev241 ===
03-17 21:00 DEBUG  root: Logfile is c:\users\dell\appdata\local\temp\wubi-11.10-rev241.log
03-17 21:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
03-17 21:00 DEBUG  CommonBackend: data_dir=C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\data
03-17 21:00 DEBUG  WindowsBackend: 7z=C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\bin\7z.exe
03-17 21:00 DEBUG  WindowsBackend: startup_folder=C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup
03-17 21:00 DEBUG  CommonBackend: Fetching basic info...
03-17 21:00 DEBUG  CommonBackend: original_exe=F:\wubi.exe
03-17 21:00 DEBUG  CommonBackend: platform=win32
03-17 21:00 DEBUG  CommonBackend: osname=nt
03-17 21:00 DEBUG  CommonBackend: language=en_US
03-17 21:00 DEBUG  CommonBackend: encoding=cp1252
03-17 21:00 DEBUG  WindowsBackend: arch=amd64
03-17 21:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\data\isolist.ini
03-17 21:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
03-17 21:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
03-17 21:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
03-17 21:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
03-17 21:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
03-17 21:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
03-17 21:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
03-17 21:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
03-17 21:00 DEBUG  WindowsBackend: Fetching host info...
03-17 21:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
03-17 21:00 DEBUG  WindowsBackend: windows version=vista
03-17 21:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
03-17 21:00 DEBUG  WindowsBackend: windows_sp=None
03-17 21:00 DEBUG  WindowsBackend: windows_build=7601
03-17 21:00 DEBUG  WindowsBackend: gmt=5
03-17 21:00 DEBUG  WindowsBackend: country=US
03-17 21:00 DEBUG  WindowsBackend: timezone=America/New_York
03-17 21:00 DEBUG  WindowsBackend: windows_username=DELL
03-17 21:00 DEBUG  WindowsBackend: user_full_name=DELL
03-17 21:00 DEBUG  WindowsBackend: user_directory=C:\Users\DELL
03-17 21:00 DEBUG  WindowsBackend: windows_language_code=1033
03-17 21:00 DEBUG  WindowsBackend: windows_language=English
03-17 21:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i5 CPU       M 460  @ 2.53GHz
03-17 21:00 DEBUG  WindowsBackend: bootloader=vista
03-17 21:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 298352.714844 mb free ntfs)
03-17 21:00 DEBUG  WindowsBackend: drive=Drive(C: hd 298352.714844 mb free ntfs)
03-17 21:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
03-17 21:00 DEBUG  WindowsBackend: uninstaller_path=None
03-17 21:00 DEBUG  WindowsBackend: previous_target_dir=None
03-17 21:00 DEBUG  WindowsBackend: previous_distro_name=None
03-17 21:00 DEBUG  WindowsBackend: keyboard_id=67699721
03-17 21:00 DEBUG  WindowsBackend: keyboard_layout=us
03-17 21:00 DEBUG  WindowsBackend: keyboard_variant=
03-17 21:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
03-17 21:00 DEBUG  CommonBackend: locale=en_US.UTF-8
03-17 21:00 DEBUG  WindowsBackend: total_memory_mb=3956.5234375
03-17 21:00 DEBUG  CommonBackend: Searching ISOs on USB devices
03-17 21:00 DEBUG  CommonBackend: Searching for local CDs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Ubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Ubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Kubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Kubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Xubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Xubuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Mythbuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp is a valid Mythbuntu CD
03-17 21:00 DEBUG  Distro:     does not contain C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\casper\filesystem.squashfs
03-17 21:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
03-17 21:00 DEBUG  Distro:   parsing info from str=Ubuntu 11.10 "Oneiric Ocelot" - Release amd64 (20111012)
03-17 21:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '11.10', 'build': '20111012', 'codename': 'Oneiric Ocelot', 'arch': 'amd64'}
03-17 21:00 INFO   Distro: Found a valid CD for Ubuntu: F:\
03-17 21:00 INFO   root: Running the CD menu...
03-17 21:00 DEBUG  WindowsFrontend: __init__...
03-17 21:00 DEBUG  WindowsFrontend: on_init...
03-17 21:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\translations, languages=['en_US', 'en']
03-17 21:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\DELL\AppData\Local\Temp\pylCC72.tmp\translations, languages=['en_US', 'en']
03-17 21:00 INFO   WindowsFrontend: Operation cancelled
03-17 21:00 DEBUG  WindowsFrontend: frontend.quit
03-17 21:00 DEBUG  WindowsFrontend: frontend.on_quit
03-17 21:00 DEBUG  root: application.on_quit
03-17 21:00 INFO   root: sys.exit

```

---

### Post by linuxmatt7 on 2012-05-06
This happens to some people all the time. Their is a easy fix. Just reburn the CD/DVD, and it should fix things. If not it might be your laptop. Check the Laptop Compatibly Thread to see if someone has managed to install Ubuntu on your laptop model.

---

