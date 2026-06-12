---
title: "Can't install Ubuntu 10.04 inside Window 7 Ultimate"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by LonelySEason on 2010-09-19
Hi all, this is my first thread here, hope everyone can help.

While I install Ubuntu10.04 inside my Widnwo 7 using WUBI, I got this error message, anyone got any idea? if u need more information, just ask and I'll post it for u. thx

[[IMG]http://img685.imageshack.us/img685/6849/ubuntuerrormessage.th.png[/IMG]](http://img685.imageshack.us/i/ubuntuerrormessage.png/)  Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]

---

### Post by 3dgard on 2010-09-19
What was the error message?

---

### Post by LonelySEason on 2010-09-19
> **3dgard said:**
> What was the error message?

yeah... sorry for my late upload, now... did u see it?

---

### Post by garvinrick4 on 2010-09-19
> **LonelySEason said:**
> Hi all, this is my first thread here, hope everyone can help.

While I install Ubuntu10.04 inside my Widnwo 7 using WUBI, I got this error message, anyone got any idea? if u need more information, just ask and I'll post it for u. thx

[[IMG]http://img685.imageshack.us/img685/6849/ubuntuerrormessage.th.png[/IMG]]("http://img685.imageshack.us/i/ubuntuerrormessage.png/")  Uploaded with [ImageShack.us]("http://imageshack.us")[/IMG] 
bcdedit is the bootmanager in Windows and WUBI was trying to put a entry in and
its identifier #. It will say wubildr in the entry if you look for it. But for some reason
it was not allowed. 
 I would go into add and delete programs in Windows and Delete any entry for WUBI.
If not there look next to USERS in C: drive in Windows for UBUNTU and open and uninstall there. Then try to install again. If you get same problem look for any bug reports on WUBI in 10.04 in launchpad. Good luck but 10.04 should work, I do not know about the Ultimate Windows 7. Not to many people in these forums spend that much money on a software program unless it is the Mac and Ubuntu guys.

---

### Post by 3dgard on 2010-09-19
Interesting... from what I suspect, its a problem with adding ubuntu to the bootloader list... 

Boot Configuration Data (BCD) is giving you the error. If its too much to ask, could you post the log file?

---

### Post by LonelySEason on 2010-09-19
> **garvinrick4 said:**
> bcdedit is the bootmanager in Windows and WUBI was trying to put a entry in and
its identifier #. It will say wubildr in the entry if you look for it. But for some reason
it was not allowed. 
 I would go into add and delete programs in Windows and Delete any entry for WUBI.
If not there look next to USERS in C: drive in Windows for UBUNTU and open and uninstall there. Then try to install again. If you get same problem look for any bug reports on WUBI in 10.04 in launchpad. Good luck but 10.04 should work, I do not know about the Ultimate Windows 7. Not to many people in these forums spend that much money on a software program unless it is the Mac and Ubuntu guys.

Yeah.. I already tried to uninstall and reinstall for several time but the error just keep showing up. I did also clean the registry.

---

### Post by LonelySEason on 2010-09-19
> **3dgard said:**
> Interesting... from what I suspect, its a problem with adding ubuntu to the bootloader list... 

Boot Configuration Data (BCD) is giving you the error. If its too much to ask, could you post the log file?

YEAH! U got the point! that's it, the BCD, I also tried easyBCD but instead I just mess up my Win7. I already tried to post the log file but everytime, when I just copy and paste it here, my firefox got no respond.

Maybe u could tell me which part u wanna know and I'll tried to post it here.

thx for ur interesting:popcorn:

---

### Post by LonelySEason on 2010-09-19
> **LonelySEason said:**
> YEAH! U got the point! that's it, the BCD, I also tried easyBCD but instead I just mess up my Win7. I already tried to post the log file but everytime, when I just copy and paste it here, my firefox got no respond.

Maybe u could tell me which part u wanna know and I'll tried to post it here.

thx for ur interesting:popcorn:


The log file:
```
09-19 04:00 INFO   root: === wubi 10.04 rev189 ===
09-19 04:00 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:00 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\data
09-19 04:00 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\bin\7z.exe
09-19 04:00 DEBUG  CommonBackend: Fetching basic info...
09-19 04:00 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:00 DEBUG  CommonBackend: platform=win32
09-19 04:00 DEBUG  CommonBackend: osname=nt
09-19 04:00 DEBUG  CommonBackend: language=en_US
09-19 04:00 DEBUG  CommonBackend: encoding=cp936
09-19 04:00 DEBUG  WindowsBackend: arch=amd64
09-19 04:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\data\isolist.ini
09-19 04:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:00 DEBUG  WindowsBackend: Fetching host info...
09-19 04:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:00 DEBUG  WindowsBackend: windows version=vista
09-19 04:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:00 DEBUG  WindowsBackend: windows_sp=None
09-19 04:00 DEBUG  WindowsBackend: windows_build=7600
09-19 04:00 DEBUG  WindowsBackend: gmt=6
09-19 04:00 DEBUG  WindowsBackend: country=US
09-19 04:00 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:00 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:00 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:00 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:00 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:00 DEBUG  WindowsBackend: windows_language=English
09-19 04:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:00 DEBUG  WindowsBackend: bootloader=vista
09-19 04:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29422.328125 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(C: hd 29422.328125 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.8476563 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:00 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:00 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:00 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:00 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:00 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:00 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:00 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:00 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:00 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:00 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:00 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:00 DEBUG  CommonBackend: Searching for local CDs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:00 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:00 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:00 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:00 INFO   root: Running the CD menu...
09-19 04:00 DEBUG  WindowsFrontend: __init__...
09-19 04:00 DEBUG  WindowsFrontend: on_init...
09-19 04:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\translations, languages=['en_US', 'en']
09-19 04:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\translations, languages=['en_US', 'en']
09-19 04:00 INFO   root: CD menu finished
09-19 04:00 INFO   root: Running the installer...
09-19 04:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\translations, languages=['en_US', 'en']
09-19 04:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\translations, languages=['en_US', 'en']
09-19 04:01 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:01 INFO   root: Received settings
09-19 04:01 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\translations, languages=['en_US', 'en']
09-19 04:01 DEBUG  TaskList: # Running tasklist...
09-19 04:01 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:01 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:01 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:01 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:01 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:01 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:01 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:01 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:01 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:01 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:01 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:01 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\winboot -> G:\ubuntu\winboot
09-19 04:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylF90D.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:01 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:01 DEBUG  TaskList: ## Running get_iso...
09-19 04:01 DEBUG  TaskList: New task copy_file
09-19 04:01 DEBUG  TaskList: ### Running copy_file...
09-19 04:02 DEBUG  TaskList: ### Finished copy_file
09-19 04:02 DEBUG  TaskList: New task check_iso
09-19 04:02 DEBUG  TaskList: ### Running check_iso...
09-19 04:02 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:02 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:02 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:02 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:02 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:02 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:02 DEBUG  TaskList: New task get_metalink
09-19 04:02 DEBUG  TaskList: #### Running get_metalink...
09-19 04:02 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:02 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:02 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:02 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:02 DEBUG  TaskList: #### Finished get_metalink
09-19 04:02 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 04:02 DEBUG  TaskList: ### Finished check_iso
09-19 04:02 DEBUG  TaskList: ## Finished get_iso
09-19 04:02 DEBUG  TaskList: ## Running extract_kernel...
09-19 04:02 DEBUG  CommonBackend: Copying files from CD J:\
09-19 04:02 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 04:02 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 04:02 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 04:02 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 04:02 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 04:02 DEBUG  TaskList: ## Finished extract_kernel
09-19 04:02 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 04:02 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 04:02 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 04:02 DEBUG  TaskList: ## Running create_preseed...
09-19 04:02 DEBUG  TaskList: ## Finished create_preseed
09-19 04:02 DEBUG  TaskList: ## Running modify_bootloader...
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 DEBUG  TaskList: ### Running modify_bcd...
09-19 04:02 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29422.328125 mb free ntfs)
09-19 04:02 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4435-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4435-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:02 DEBUG  TaskList: # Cancelling tasklist
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4435-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4435-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 DEBUG  TaskList: New task modify_bcd
09-19 04:02 DEBUG  TaskList: ## Finished modify_bootloader
09-19 04:02 DEBUG  TaskList: # Finished tasklist
09-19 04:02 INFO   root: === wubi 10.04 rev189 ===
09-19 04:02 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:02 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:02 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\data
09-19 04:02 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\bin\7z.exe
09-19 04:02 DEBUG  CommonBackend: Fetching basic info...
09-19 04:02 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:02 DEBUG  CommonBackend: platform=win32
09-19 04:02 DEBUG  CommonBackend: osname=nt
09-19 04:02 DEBUG  CommonBackend: language=en_US
09-19 04:02 DEBUG  CommonBackend: encoding=cp936
09-19 04:02 DEBUG  WindowsBackend: arch=amd64
09-19 04:02 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\data\isolist.ini
09-19 04:02 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:02 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:02 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:02 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:02 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:02 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:02 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:02 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:02 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:02 DEBUG  WindowsBackend: Fetching host info...
09-19 04:02 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:02 DEBUG  WindowsBackend: windows version=vista
09-19 04:02 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:02 DEBUG  WindowsBackend: windows_sp=None
09-19 04:02 DEBUG  WindowsBackend: windows_build=7600
09-19 04:02 DEBUG  WindowsBackend: gmt=6
09-19 04:02 DEBUG  WindowsBackend: country=US
09-19 04:02 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:02 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:02 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:02 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:02 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:02 DEBUG  WindowsBackend: windows_language=English
09-19 04:02 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:02 DEBUG  WindowsBackend: bootloader=vista
09-19 04:02 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29421.8554688 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(C: hd 29421.8554688 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:02 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:02 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:02 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:02 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:02 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:02 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:02 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:02 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:02 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:02 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:02 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:02 DEBUG  CommonBackend: Searching for local CDs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:02 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:02 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:02 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:02 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:02 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:02 INFO   root: Running the CD menu...
09-19 04:02 DEBUG  WindowsFrontend: __init__...
09-19 04:02 DEBUG  WindowsFrontend: on_init...
09-19 04:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:02 INFO   root: CD menu finished
09-19 04:02 INFO   root: Already installed, running the uninstaller...
09-19 04:02 INFO   root: Running the uninstaller...
09-19 04:02 INFO   CommonBackend: This is the uninstaller running
09-19 04:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:02 INFO   root: Received settings
09-19 04:02 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:02 DEBUG  TaskList: # Running tasklist...
09-19 04:02 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:02 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:02 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:02 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:02 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29421.8554688 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:02 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:02 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:02 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:02 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:02 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:03 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:03 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:03 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:03 DEBUG  TaskList: # Finished tasklist
09-19 04:03 INFO   root: Almost finished uninstalling
09-19 04:03 INFO   root: Finished uninstallation
09-19 04:03 DEBUG  CommonBackend: Fetching basic info...
09-19 04:03 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:03 DEBUG  CommonBackend: platform=win32
09-19 04:03 DEBUG  CommonBackend: osname=nt
09-19 04:03 DEBUG  WindowsBackend: arch=amd64
09-19 04:03 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\data\isolist.ini
09-19 04:03 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:03 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:03 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:03 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:03 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:03 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:03 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:03 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:03 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:03 DEBUG  WindowsBackend: Fetching host info...
09-19 04:03 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:03 DEBUG  WindowsBackend: windows version=vista
09-19 04:03 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:03 DEBUG  WindowsBackend: windows_sp=None
09-19 04:03 DEBUG  WindowsBackend: windows_build=7600
09-19 04:03 DEBUG  WindowsBackend: gmt=6
09-19 04:03 DEBUG  WindowsBackend: country=US
09-19 04:03 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:03 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:03 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:03 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:03 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:03 DEBUG  WindowsBackend: windows_language=English
09-19 04:03 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:03 DEBUG  WindowsBackend: bootloader=vista
09-19 04:03 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29421.90625 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(C: hd 29421.90625 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:03 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:03 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:03 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:03 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:03 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:03 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:03 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:03 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:03 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:03 DEBUG  CommonBackend: Searching for local CDs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:03 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:03 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:03 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:03 INFO   root: Running the installer...
09-19 04:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:03 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:03 INFO   root: Received settings
09-19 04:03 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\translations, languages=['en_US', 'en']
09-19 04:03 DEBUG  TaskList: # Running tasklist...
09-19 04:03 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:03 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:03 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:03 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:03 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:03 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:03 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:03 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:03 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:03 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:03 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:03 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:03 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:03 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:03 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\winboot -> G:\ubuntu\winboot
09-19 04:03 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylFA16.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:03 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:03 DEBUG  TaskList: ## Running get_iso...
09-19 04:03 DEBUG  TaskList: New task copy_file
09-19 04:03 DEBUG  TaskList: ### Running copy_file...
09-19 04:04 DEBUG  TaskList: ### Finished copy_file
09-19 04:04 DEBUG  TaskList: New task check_iso
09-19 04:04 DEBUG  TaskList: ### Running check_iso...
09-19 04:04 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:04 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:04 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:04 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:04 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:04 DEBUG  TaskList: New task get_metalink
09-19 04:04 DEBUG  TaskList: #### Running get_metalink...
09-19 04:04 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:04 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:04 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:04 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:04 DEBUG  TaskList: #### Finished get_metalink
09-19 04:04 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 04:04 DEBUG  TaskList: ### Finished check_iso
09-19 04:04 DEBUG  TaskList: ## Finished get_iso
09-19 04:04 DEBUG  TaskList: ## Running extract_kernel...
09-19 04:04 DEBUG  CommonBackend: Copying files from CD J:\
09-19 04:04 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 04:04 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 04:04 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 04:04 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 04:04 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 04:04 DEBUG  TaskList: ## Finished extract_kernel
09-19 04:04 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 04:04 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 04:04 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 04:04 DEBUG  TaskList: ## Running create_preseed...
09-19 04:04 DEBUG  TaskList: ## Finished create_preseed
09-19 04:04 DEBUG  TaskList: ## Running modify_bootloader...
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 DEBUG  TaskList: ### Running modify_bcd...
09-19 04:04 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29421.90625 mb free ntfs)
09-19 04:04 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4436-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4436-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:04 DEBUG  TaskList: # Cancelling tasklist
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4436-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4436-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 DEBUG  TaskList: New task modify_bcd
09-19 04:04 DEBUG  TaskList: ## Finished modify_bootloader
09-19 04:04 DEBUG  TaskList: # Finished tasklist
09-19 04:04 INFO   root: === wubi 10.04 rev189 ===
09-19 04:04 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:04 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 04:04 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\data
09-19 04:04 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\bin\7z.exe
09-19 04:04 DEBUG  CommonBackend: Fetching basic info...
09-19 04:04 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 04:04 DEBUG  CommonBackend: platform=win32
09-19 04:04 DEBUG  CommonBackend: osname=nt
09-19 04:04 DEBUG  CommonBackend: language=en_US
09-19 04:04 DEBUG  CommonBackend: encoding=cp936
09-19 04:04 DEBUG  WindowsBackend: arch=amd64
09-19 04:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\data\isolist.ini
09-19 04:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:04 DEBUG  WindowsBackend: Fetching host info...
09-19 04:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:04 DEBUG  WindowsBackend: windows version=vista
09-19 04:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:04 DEBUG  WindowsBackend: windows_sp=None
09-19 04:04 DEBUG  WindowsBackend: windows_build=7600
09-19 04:04 DEBUG  WindowsBackend: gmt=6
09-19 04:04 DEBUG  WindowsBackend: country=US
09-19 04:04 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:04 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:04 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:04 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:04 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:04 DEBUG  WindowsBackend: windows_language=English
09-19 04:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:04 DEBUG  WindowsBackend: bootloader=vista
09-19 04:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29419.1210938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(C: hd 29419.1210938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:04 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:04 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:04 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:04 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:04 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:04 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:04 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:04 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:04 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:04 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:04 DEBUG  CommonBackend: Searching for local CDs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:04 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:04 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:04 INFO   root: Running the CD menu...
09-19 04:04 DEBUG  WindowsFrontend: __init__...
09-19 04:04 DEBUG  WindowsFrontend: on_init...
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 INFO   root: CD menu finished
09-19 04:04 INFO   root: Already installed, running the uninstaller...
09-19 04:04 INFO   root: Running the uninstaller...
09-19 04:04 INFO   CommonBackend: This is the uninstaller running
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 INFO   root: Received settings
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 DEBUG  TaskList: # Running tasklist...
09-19 04:04 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:04 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:04 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:04 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:04 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29419.1210938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:04 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:04 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:04 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:04 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:04 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:04 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:04 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:04 DEBUG  TaskList: # Finished tasklist
09-19 04:04 INFO   root: Almost finished uninstalling
09-19 04:04 INFO   root: Finished uninstallation
09-19 04:04 DEBUG  CommonBackend: Fetching basic info...
09-19 04:04 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 04:04 DEBUG  CommonBackend: platform=win32
09-19 04:04 DEBUG  CommonBackend: osname=nt
09-19 04:04 DEBUG  WindowsBackend: arch=amd64
09-19 04:04 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\data\isolist.ini
09-19 04:04 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:04 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:04 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:04 DEBUG  WindowsBackend: Fetching host info...
09-19 04:04 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:04 DEBUG  WindowsBackend: windows version=vista
09-19 04:04 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:04 DEBUG  WindowsBackend: windows_sp=None
09-19 04:04 DEBUG  WindowsBackend: windows_build=7600
09-19 04:04 DEBUG  WindowsBackend: gmt=6
09-19 04:04 DEBUG  WindowsBackend: country=US
09-19 04:04 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:04 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:04 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:04 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:04 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:04 DEBUG  WindowsBackend: windows_language=English
09-19 04:04 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:04 DEBUG  WindowsBackend: bootloader=vista
09-19 04:04 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29420.0703125 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(C: hd 29420.0703125 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:04 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:04 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:04 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:04 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:04 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:04 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:04 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:04 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:04 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:04 DEBUG  CommonBackend: Searching for local CDs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:04 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:04 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:04 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:04 INFO   root: Running the installer...
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:04 INFO   root: Received settings
09-19 04:04 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\translations, languages=['en_US', 'en']
09-19 04:04 DEBUG  TaskList: # Running tasklist...
09-19 04:04 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:04 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:04 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:04 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:04 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:04 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:04 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:04 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:04 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:04 DEBUG  WindowsBackend: Copying uninstaller H:\Drive D\Download\Ubuntu 10.04\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:04 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:04 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:04 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:04 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:04 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\winboot -> G:\ubuntu\winboot
09-19 04:04 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl63F0.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:04 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:04 DEBUG  TaskList: ## Running get_iso...
09-19 04:04 DEBUG  TaskList: New task copy_file
09-19 04:04 DEBUG  TaskList: ### Running copy_file...
09-19 04:05 DEBUG  TaskList: ### Finished copy_file
09-19 04:05 DEBUG  TaskList: New task check_iso
09-19 04:05 DEBUG  TaskList: ### Running check_iso...
09-19 04:05 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:05 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:05 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:05 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:05 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:05 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:05 DEBUG  TaskList: New task get_metalink
09-19 04:05 DEBUG  TaskList: #### Running get_metalink...
09-19 04:05 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:05 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:05 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:05 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:05 DEBUG  TaskList: #### Finished get_metalink
09-19 04:05 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 04:05 DEBUG  TaskList: ### Finished check_iso
09-19 04:05 DEBUG  TaskList: ## Finished get_iso
09-19 04:05 DEBUG  TaskList: ## Running extract_kernel...
09-19 04:05 DEBUG  CommonBackend: Copying files from CD J:\
09-19 04:05 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 04:05 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 04:05 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 04:05 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 04:05 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 04:05 DEBUG  TaskList: ## Finished extract_kernel
09-19 04:05 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 04:05 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 04:05 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 04:05 DEBUG  TaskList: ## Running create_preseed...
09-19 04:05 DEBUG  TaskList: ## Finished create_preseed
09-19 04:05 DEBUG  TaskList: ## Running modify_bootloader...
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 DEBUG  TaskList: ### Running modify_bcd...
09-19 04:05 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29420.0703125 mb free ntfs)
09-19 04:05 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4437-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4437-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:05 DEBUG  TaskList: # Cancelling tasklist
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4437-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {1c8d4437-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 DEBUG  TaskList: New task modify_bcd
09-19 04:05 DEBUG  TaskList: ## Finished modify_bootloader
09-19 04:05 DEBUG  TaskList: # Finished tasklist
09-19 04:07 INFO   root: === wubi 10.04 rev189 ===
09-19 04:07 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:07 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:07 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\data
09-19 04:07 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\bin\7z.exe
09-19 04:07 DEBUG  CommonBackend: Fetching basic info...
09-19 04:07 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:07 DEBUG  CommonBackend: platform=win32
09-19 04:07 DEBUG  CommonBackend: osname=nt
09-19 04:07 DEBUG  CommonBackend: language=en_US
09-19 04:07 DEBUG  CommonBackend: encoding=cp936
09-19 04:07 DEBUG  WindowsBackend: arch=amd64
09-19 04:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\data\isolist.ini
09-19 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:07 DEBUG  WindowsBackend: Fetching host info...
09-19 04:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:07 DEBUG  WindowsBackend: windows version=vista
09-19 04:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:07 DEBUG  WindowsBackend: windows_sp=None
09-19 04:07 DEBUG  WindowsBackend: windows_build=7600
09-19 04:07 DEBUG  WindowsBackend: gmt=6
09-19 04:07 DEBUG  WindowsBackend: country=US
09-19 04:07 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:07 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:07 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:07 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:07 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:07 DEBUG  WindowsBackend: windows_language=English
09-19 04:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:07 DEBUG  WindowsBackend: bootloader=vista
09-19 04:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29225.5898438 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(C: hd 29225.5898438 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:07 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:07 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:07 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:07 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:07 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:07 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:07 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:07 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:07 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:07 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:07 DEBUG  CommonBackend: Searching for local CDs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:07 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:07 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:07 INFO   root: Running the CD menu...
09-19 04:07 DEBUG  WindowsFrontend: __init__...
09-19 04:07 DEBUG  WindowsFrontend: on_init...
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 INFO   root: CD menu finished
09-19 04:07 INFO   root: Already installed, running the uninstaller...
09-19 04:07 INFO   root: Running the uninstaller...
09-19 04:07 INFO   CommonBackend: This is the uninstaller running
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 INFO   root: Received settings
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 DEBUG  TaskList: # Running tasklist...
09-19 04:07 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:07 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:07 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:07 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:07 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29225.5898438 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:07 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:07 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:07 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:07 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:07 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:07 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:07 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:07 DEBUG  TaskList: # Finished tasklist
09-19 04:07 INFO   root: Almost finished uninstalling
09-19 04:07 INFO   root: Finished uninstallation
09-19 04:07 DEBUG  CommonBackend: Fetching basic info...
09-19 04:07 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:07 DEBUG  CommonBackend: platform=win32
09-19 04:07 DEBUG  CommonBackend: osname=nt
09-19 04:07 DEBUG  WindowsBackend: arch=amd64
09-19 04:07 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\data\isolist.ini
09-19 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:07 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:07 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:07 DEBUG  WindowsBackend: Fetching host info...
09-19 04:07 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:07 DEBUG  WindowsBackend: windows version=vista
09-19 04:07 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:07 DEBUG  WindowsBackend: windows_sp=None
09-19 04:07 DEBUG  WindowsBackend: windows_build=7600
09-19 04:07 DEBUG  WindowsBackend: gmt=6
09-19 04:07 DEBUG  WindowsBackend: country=US
09-19 04:07 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:07 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:07 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:07 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:07 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:07 DEBUG  WindowsBackend: windows_language=English
09-19 04:07 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:07 DEBUG  WindowsBackend: bootloader=vista
09-19 04:07 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29225.6328125 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(C: hd 29225.6328125 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(D: hd 32023.84375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:07 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:07 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:07 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:07 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:07 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:07 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:07 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:07 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:07 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:07 DEBUG  CommonBackend: Searching for local CDs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:07 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:07 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:07 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:07 INFO   root: Running the installer...
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=16000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:07 INFO   root: Received settings
09-19 04:07 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\translations, languages=['en_US', 'en']
09-19 04:07 DEBUG  TaskList: # Running tasklist...
09-19 04:07 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:07 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:07 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:07 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:07 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:07 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:07 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:07 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:07 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:07 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:07 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:07 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:07 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:07 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:07 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\winboot -> G:\ubuntu\winboot
09-19 04:07 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2DD3.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:07 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:07 DEBUG  TaskList: ## Running get_iso...
09-19 04:07 DEBUG  TaskList: New task copy_file
09-19 04:07 DEBUG  TaskList: ### Running copy_file...
09-19 04:08 DEBUG  TaskList: ### Finished copy_file
09-19 04:08 DEBUG  TaskList: New task check_iso
09-19 04:08 DEBUG  TaskList: ### Running check_iso...
09-19 04:08 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:08 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:08 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:08 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:08 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:08 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:08 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:08 DEBUG  TaskList: New task get_metalink
09-19 04:08 DEBUG  TaskList: #### Running get_metalink...
09-19 04:08 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:08 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-19 04:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:08 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink, basename=lucid-desktop-i386.metalink, length=1007, text=None
09-19 04:08 DEBUG  downloader: download finished (read 1007 bytes)
09-19 04:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > G:\ubuntu\install
09-19 04:08 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=131, text=None
09-19 04:08 DEBUG  downloader: download finished (read 131 bytes)
09-19 04:08 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > G:\ubuntu\install
09-19 04:08 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
09-19 04:08 DEBUG  downloader: download finished (read 189 bytes)
09-19 04:08 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-19 04:08 INFO   saplog: Checking block bindings..
09-19 04:08 INFO   saplog: Key verified successfully.
09-19 04:08 DEBUG  CommonBackend: metalink md5sums:
4b88f9df6e8ca890e6887186a5755930  maverick-desktop-amd64.metalink
a1dda02202aa3e908de372385d0f7607  maverick-desktop-i386.metalink

09-19 04:08 ERROR  CommonBackend: The md5 of the metalink does match
09-19 04:08 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
09-19 04:08 DEBUG  TaskList: #### Finished get_metalink
09-19 04:08 DEBUG  TaskList: New task get_file_md5
09-19 04:08 DEBUG  TaskList: #### Running get_file_md5...
09-19 04:09 DEBUG  TaskList: #### Finished get_file_md5
09-19 04:09 ERROR  CommonBackend: Invalid md5 for ISO G:\ubuntu\install\installation.iso (9a95ed6f6ec38fb58c446dba1add6a08 != d044a2a0c8103fc3e5b7e18b0f7de1c8)
None
09-19 04:09 DEBUG  TaskList: ### Finished check_iso
09-19 04:09 DEBUG  CommonBackend: Searching for local ISO
09-19 04:09 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-19 04:09 DEBUG  TaskList: New task download
09-19 04:09 DEBUG  TaskList: ### Running download...
09-19 04:09 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:09 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
09-19 04:09 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
09-19 04:09 DEBUG  TaskList: ### Finished download
09-19 04:09 DEBUG  TaskList: New task download
09-19 04:09 DEBUG  TaskList: ### Running download...
09-19 04:09 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:09 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso, basename=lucid-desktop-i386.iso, length=718864384, text=None
09-19 04:14 INFO   WindowsFrontend: Operation cancelled
09-19 04:14 DEBUG  WindowsFrontend: frontend.quit
09-19 04:14 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:14 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-19 04:14 DEBUG  TaskList: # Cancelling tasklist
09-19 04:14 DEBUG  downloader: download finished (read 16523264 bytes)
09-19 04:14 DEBUG  TaskList: ### Finished download
09-19 04:14 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-19 04:14 DEBUG  root: application.on_quit
09-19 04:14 DEBUG  root: Forceful exit
09-19 04:14 INFO   root: sys.exit
09-19 04:15 INFO   root: === wubi 10.04 rev189 ===
09-19 04:15 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
09-19 04:15 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\data
09-19 04:15 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\bin\7z.exe
09-19 04:15 DEBUG  CommonBackend: Fetching basic info...
09-19 04:15 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
09-19 04:15 DEBUG  CommonBackend: platform=win32
09-19 04:15 DEBUG  CommonBackend: osname=nt
09-19 04:15 DEBUG  CommonBackend: language=en_US
09-19 04:15 DEBUG  CommonBackend: encoding=cp936
09-19 04:15 DEBUG  WindowsBackend: arch=amd64
09-19 04:15 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\data\isolist.ini
09-19 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:15 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:15 DEBUG  WindowsBackend: Fetching host info...
09-19 04:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:15 DEBUG  WindowsBackend: windows version=vista
09-19 04:15 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:15 DEBUG  WindowsBackend: windows_sp=None
09-19 04:15 DEBUG  WindowsBackend: windows_build=7600
09-19 04:15 DEBUG  WindowsBackend: gmt=6
09-19 04:15 DEBUG  WindowsBackend: country=US
09-19 04:15 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:15 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:15 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:15 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:15 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:15 DEBUG  WindowsBackend: windows_language=English
09-19 04:15 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:15 DEBUG  WindowsBackend: bootloader=vista
09-19 04:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29219.6679688 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(C: hd 29219.6679688 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(D: hd 32018.2929688 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(G: hd 19672.9023438 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:15 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:15 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:15 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:15 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:15 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:15 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:15 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:15 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:15 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:15 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:15 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:15 DEBUG  CommonBackend: Searching for local CDs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:15 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:15 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:15 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:15 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:15 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:15 INFO   root: Running the uninstaller...
09-19 04:15 INFO   CommonBackend: This is the uninstaller running
09-19 04:15 DEBUG  WindowsFrontend: __init__...
09-19 04:15 DEBUG  WindowsFrontend: on_init...
09-19 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\translations, languages=['en_US', 'en']
09-19 04:15 INFO   root: Received settings
09-19 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\translations, languages=['en_US', 'en']
09-19 04:15 DEBUG  TaskList: # Running tasklist...
09-19 04:15 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:15 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:15 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:15 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:15 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29219.6679688 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32018.2929688 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20072.9882813 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19672.9023438 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:15 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:15 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:15 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:15 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:15 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:15 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:15 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:15 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:15 DEBUG  TaskList: # Finished tasklist
09-19 04:15 INFO   root: Almost finished uninstalling
09-19 04:15 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B54.tmp\translations, languages=['en_US', 'en']
09-19 04:15 INFO   root: Finished uninstallation
09-19 04:15 DEBUG  root: application.quit
09-19 04:15 DEBUG  WindowsFrontend: frontend.quit
09-19 04:15 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:15 DEBUG  root: application.on_quit
09-19 04:15 INFO   root: sys.exit
09-19 04:23 INFO   root: === wubi 10.04 rev189 ===
09-19 04:23 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:23 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:23 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\data
09-19 04:23 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\bin\7z.exe
09-19 04:23 DEBUG  CommonBackend: Fetching basic info...
09-19 04:23 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:23 DEBUG  CommonBackend: platform=win32
09-19 04:23 DEBUG  CommonBackend: osname=nt
09-19 04:23 DEBUG  CommonBackend: language=en_US
09-19 04:23 DEBUG  CommonBackend: encoding=cp936
09-19 04:23 DEBUG  WindowsBackend: arch=amd64
09-19 04:23 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\data\isolist.ini
09-19 04:23 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:23 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:23 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:23 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:23 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:23 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:23 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:23 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:23 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:23 DEBUG  WindowsBackend: Fetching host info...
09-19 04:23 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:23 DEBUG  WindowsBackend: windows version=vista
09-19 04:23 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:23 DEBUG  WindowsBackend: windows_sp=None
09-19 04:23 DEBUG  WindowsBackend: windows_build=7600
09-19 04:23 DEBUG  WindowsBackend: gmt=6
09-19 04:23 DEBUG  WindowsBackend: country=US
09-19 04:23 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:23 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:23 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:23 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:23 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:23 DEBUG  WindowsBackend: windows_language=English
09-19 04:23 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:23 DEBUG  WindowsBackend: bootloader=vista
09-19 04:23 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29245.015625 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(C: hd 29245.015625 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3398438 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:23 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:23 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:23 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:23 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:23 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:23 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:23 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:23 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:23 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:23 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:23 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:23 DEBUG  CommonBackend: Searching for local CDs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:23 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:23 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:23 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:23 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:23 INFO   root: Running the CD menu...
09-19 04:23 DEBUG  WindowsFrontend: __init__...
09-19 04:23 DEBUG  WindowsFrontend: on_init...
09-19 04:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\translations, languages=['en_US', 'en']
09-19 04:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\translations, languages=['en_US', 'en']
09-19 04:23 INFO   root: CD menu finished
09-19 04:23 INFO   root: Running the installer...
09-19 04:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\translations, languages=['en_US', 'en']
09-19 04:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\translations, languages=['en_US', 'en']
09-19 04:23 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:23 INFO   root: Received settings
09-19 04:23 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\translations, languages=['en_US', 'en']
09-19 04:23 DEBUG  TaskList: # Running tasklist...
09-19 04:23 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:23 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:23 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:23 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:23 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:23 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:23 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:23 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:23 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:23 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:23 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:23 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:23 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:23 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:23 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\winboot -> G:\ubuntu\winboot
09-19 04:23 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC58F.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:23 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:23 DEBUG  TaskList: ## Running get_iso...
09-19 04:23 DEBUG  TaskList: New task copy_file
09-19 04:23 DEBUG  TaskList: ### Running copy_file...
09-19 04:24 DEBUG  TaskList: ### Finished copy_file
09-19 04:24 DEBUG  TaskList: New task check_iso
09-19 04:24 DEBUG  TaskList: ### Running check_iso...
09-19 04:24 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:24 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:24 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:24 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:24 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:24 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:24 DEBUG  TaskList: New task get_metalink
09-19 04:24 DEBUG  TaskList: #### Running get_metalink...
09-19 04:24 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:24 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-19 04:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink, basename=lucid-desktop-i386.metalink, length=1007, text=None
09-19 04:24 DEBUG  downloader: download finished (read 1007 bytes)
09-19 04:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > G:\ubuntu\install
09-19 04:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=131, text=None
09-19 04:24 DEBUG  downloader: download finished (read 131 bytes)
09-19 04:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > G:\ubuntu\install
09-19 04:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
09-19 04:24 DEBUG  downloader: download finished (read 189 bytes)
09-19 04:24 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-19 04:24 INFO   saplog: Checking block bindings..
09-19 04:24 INFO   saplog: Key verified successfully.
09-19 04:24 DEBUG  CommonBackend: metalink md5sums:
4b88f9df6e8ca890e6887186a5755930  maverick-desktop-amd64.metalink
a1dda02202aa3e908de372385d0f7607  maverick-desktop-i386.metalink

09-19 04:24 ERROR  CommonBackend: The md5 of the metalink does match
09-19 04:24 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
09-19 04:24 DEBUG  TaskList: #### Finished get_metalink
09-19 04:24 DEBUG  TaskList: New task get_file_md5
09-19 04:24 DEBUG  TaskList: #### Running get_file_md5...
09-19 04:24 DEBUG  TaskList: #### Finished get_file_md5
09-19 04:24 ERROR  CommonBackend: Invalid md5 for ISO G:\ubuntu\install\installation.iso (9a95ed6f6ec38fb58c446dba1add6a08 != d044a2a0c8103fc3e5b7e18b0f7de1c8)
None
09-19 04:24 DEBUG  TaskList: ### Finished check_iso
09-19 04:24 DEBUG  CommonBackend: Searching for local ISO
09-19 04:24 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-19 04:24 DEBUG  TaskList: New task download
09-19 04:24 DEBUG  TaskList: ### Running download...
09-19 04:24 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:24 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
09-19 04:24 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
09-19 04:24 DEBUG  TaskList: ### Finished download
09-19 04:24 DEBUG  TaskList: New task download
09-19 04:24 DEBUG  TaskList: ### Running download...
09-19 04:24 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:24 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso, basename=lucid-desktop-i386.iso, length=718864384, text=None
09-19 04:24 INFO   WindowsFrontend: Operation cancelled
09-19 04:24 DEBUG  WindowsFrontend: frontend.quit
09-19 04:24 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:24 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-19 04:24 DEBUG  TaskList: # Cancelling tasklist
09-19 04:24 DEBUG  downloader: download finished (read 1679360 bytes)
09-19 04:24 DEBUG  TaskList: ### Finished download
09-19 04:25 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-19 04:25 DEBUG  root: application.on_quit
09-19 04:25 DEBUG  root: Forceful exit
09-19 04:25 INFO   root: sys.exit
09-19 04:25 INFO   root: === wubi 10.04 rev189 ===
09-19 04:25 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:25 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
09-19 04:25 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\data
09-19 04:25 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\bin\7z.exe
09-19 04:25 DEBUG  CommonBackend: Fetching basic info...
09-19 04:25 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
09-19 04:25 DEBUG  CommonBackend: platform=win32
09-19 04:25 DEBUG  CommonBackend: osname=nt
09-19 04:25 DEBUG  CommonBackend: language=en_US
09-19 04:25 DEBUG  CommonBackend: encoding=cp936
09-19 04:25 DEBUG  WindowsBackend: arch=amd64
09-19 04:25 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\data\isolist.ini
09-19 04:25 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:25 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:25 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:25 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:25 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:25 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:25 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:25 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:25 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:25 DEBUG  WindowsBackend: Fetching host info...
09-19 04:25 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:25 DEBUG  WindowsBackend: windows version=vista
09-19 04:25 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:25 DEBUG  WindowsBackend: windows_sp=None
09-19 04:25 DEBUG  WindowsBackend: windows_build=7600
09-19 04:25 DEBUG  WindowsBackend: gmt=6
09-19 04:25 DEBUG  WindowsBackend: country=US
09-19 04:25 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:25 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:25 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:25 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:25 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:25 DEBUG  WindowsBackend: windows_language=English
09-19 04:25 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:25 DEBUG  WindowsBackend: bootloader=vista
09-19 04:25 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29297.703125 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(C: hd 29297.703125 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3398438 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(G: hd 19687.0585938 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:25 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:25 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:25 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:25 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:25 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:25 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:25 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:25 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:25 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:25 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:25 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:25 DEBUG  CommonBackend: Searching for local CDs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:25 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:25 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:25 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:25 INFO   root: Running the uninstaller...
09-19 04:25 INFO   CommonBackend: This is the uninstaller running
09-19 04:25 DEBUG  WindowsFrontend: __init__...
09-19 04:25 DEBUG  WindowsFrontend: on_init...
09-19 04:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\translations, languages=['en_US', 'en']
09-19 04:25 INFO   root: Received settings
09-19 04:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\translations, languages=['en_US', 'en']
09-19 04:25 DEBUG  TaskList: # Running tasklist...
09-19 04:25 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:25 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:25 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:25 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:25 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29297.703125 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32011.3398438 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19687.0585938 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:25 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:25 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:25 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:25 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:25 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:25 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:25 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:25 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:25 DEBUG  TaskList: # Finished tasklist
09-19 04:25 INFO   root: Almost finished uninstalling
09-19 04:25 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylB653.tmp\translations, languages=['en_US', 'en']
09-19 04:25 INFO   root: Finished uninstallation
09-19 04:25 DEBUG  root: application.quit
09-19 04:25 DEBUG  WindowsFrontend: frontend.quit
09-19 04:25 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:25 DEBUG  root: application.on_quit
09-19 04:25 INFO   root: sys.exit
09-19 04:27 INFO   root: === wubi 10.04 rev189 ===
09-19 04:27 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:27 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\data
09-19 04:27 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\bin\7z.exe
09-19 04:27 DEBUG  CommonBackend: Fetching basic info...
09-19 04:27 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:27 DEBUG  CommonBackend: platform=win32
09-19 04:27 DEBUG  CommonBackend: osname=nt
09-19 04:27 DEBUG  CommonBackend: language=en_US
09-19 04:27 DEBUG  CommonBackend: encoding=cp936
09-19 04:27 DEBUG  WindowsBackend: arch=amd64
09-19 04:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\data\isolist.ini
09-19 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:27 DEBUG  WindowsBackend: Fetching host info...
09-19 04:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:27 DEBUG  WindowsBackend: windows version=vista
09-19 04:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:27 DEBUG  WindowsBackend: windows_sp=None
09-19 04:27 DEBUG  WindowsBackend: windows_build=7600
09-19 04:27 DEBUG  WindowsBackend: gmt=6
09-19 04:27 DEBUG  WindowsBackend: country=US
09-19 04:27 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:27 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:27 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:27 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:27 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:27 DEBUG  WindowsBackend: windows_language=English
09-19 04:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:27 DEBUG  WindowsBackend: bootloader=vista
09-19 04:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29297.0078125 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(C: hd 29297.0078125 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:27 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:27 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:27 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:27 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:27 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:27 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:27 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:27 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:27 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:27 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:27 DEBUG  CommonBackend: Searching for local CDs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:27 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:27 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:27 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:27 INFO   root: Running the CD menu...
09-19 04:27 DEBUG  WindowsFrontend: __init__...
09-19 04:27 DEBUG  WindowsFrontend: on_init...
09-19 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\translations, languages=['en_US', 'en']
09-19 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\translations, languages=['en_US', 'en']
09-19 04:27 INFO   root: CD menu finished
09-19 04:27 INFO   root: Running the installer...
09-19 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\translations, languages=['en_US', 'en']
09-19 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\translations, languages=['en_US', 'en']
09-19 04:27 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:27 INFO   root: Received settings
09-19 04:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\translations, languages=['en_US', 'en']
09-19 04:27 DEBUG  TaskList: # Running tasklist...
09-19 04:27 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:27 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:27 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:27 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:27 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:27 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:27 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:27 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:27 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:27 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:27 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:27 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:27 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:27 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\winboot -> G:\ubuntu\winboot
09-19 04:27 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3B1C.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:27 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:27 DEBUG  TaskList: ## Running get_iso...
09-19 04:27 DEBUG  TaskList: New task copy_file
09-19 04:27 DEBUG  TaskList: ### Running copy_file...
09-19 04:28 DEBUG  TaskList: ### Finished copy_file
09-19 04:28 DEBUG  TaskList: New task check_iso
09-19 04:28 DEBUG  TaskList: ### Running check_iso...
09-19 04:28 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:28 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:28 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:28 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:28 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:28 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:28 DEBUG  TaskList: New task get_metalink
09-19 04:28 DEBUG  TaskList: #### Running get_metalink...
09-19 04:28 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:28 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-19 04:28 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:28 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink, basename=lucid-desktop-i386.metalink, length=1007, text=None
09-19 04:28 DEBUG  downloader: download finished (read 1007 bytes)
09-19 04:28 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > G:\ubuntu\install
09-19 04:28 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=131, text=None
09-19 04:28 DEBUG  downloader: download finished (read 131 bytes)
09-19 04:28 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > G:\ubuntu\install
09-19 04:28 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
09-19 04:28 DEBUG  downloader: download finished (read 189 bytes)
09-19 04:28 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-19 04:28 INFO   saplog: Checking block bindings..
09-19 04:28 INFO   saplog: Key verified successfully.
09-19 04:28 DEBUG  CommonBackend: metalink md5sums:
4b88f9df6e8ca890e6887186a5755930  maverick-desktop-amd64.metalink
a1dda02202aa3e908de372385d0f7607  maverick-desktop-i386.metalink

09-19 04:28 ERROR  CommonBackend: The md5 of the metalink does match
09-19 04:28 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
09-19 04:28 DEBUG  TaskList: #### Finished get_metalink
09-19 04:28 DEBUG  TaskList: New task get_file_md5
09-19 04:28 DEBUG  TaskList: #### Running get_file_md5...
09-19 04:28 DEBUG  TaskList: #### Finished get_file_md5
09-19 04:28 ERROR  CommonBackend: Invalid md5 for ISO G:\ubuntu\install\installation.iso (9a95ed6f6ec38fb58c446dba1add6a08 != d044a2a0c8103fc3e5b7e18b0f7de1c8)
None
09-19 04:28 DEBUG  TaskList: ### Finished check_iso
09-19 04:28 DEBUG  CommonBackend: Searching for local ISO
09-19 04:28 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-19 04:28 DEBUG  TaskList: New task download
09-19 04:28 DEBUG  TaskList: ### Running download...
09-19 04:28 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:28 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
09-19 04:28 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
09-19 04:28 DEBUG  TaskList: ### Finished download
09-19 04:28 DEBUG  TaskList: New task download
09-19 04:28 DEBUG  TaskList: ### Running download...
09-19 04:28 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 04:28 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso, basename=lucid-desktop-i386.iso, length=718864384, text=None
09-19 04:28 INFO   WindowsFrontend: Operation cancelled
09-19 04:28 DEBUG  WindowsFrontend: frontend.quit
09-19 04:28 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:28 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-19 04:28 DEBUG  TaskList: # Cancelling tasklist
09-19 04:28 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-19 04:28 DEBUG  root: application.on_quit
09-19 04:28 DEBUG  root: Forceful exit
09-19 04:28 INFO   root: sys.exit
09-19 04:29 INFO   root: === wubi 10.04 rev189 ===
09-19 04:29 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:29 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:29 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\data
09-19 04:29 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\bin\7z.exe
09-19 04:29 DEBUG  CommonBackend: Fetching basic info...
09-19 04:29 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:29 DEBUG  CommonBackend: platform=win32
09-19 04:29 DEBUG  CommonBackend: osname=nt
09-19 04:29 DEBUG  CommonBackend: language=en_US
09-19 04:29 DEBUG  CommonBackend: encoding=cp936
09-19 04:29 DEBUG  WindowsBackend: arch=amd64
09-19 04:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\data\isolist.ini
09-19 04:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:29 DEBUG  WindowsBackend: Fetching host info...
09-19 04:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:29 DEBUG  WindowsBackend: windows version=vista
09-19 04:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:29 DEBUG  WindowsBackend: windows_sp=None
09-19 04:29 DEBUG  WindowsBackend: windows_build=7600
09-19 04:29 DEBUG  WindowsBackend: gmt=6
09-19 04:29 DEBUG  WindowsBackend: country=US
09-19 04:29 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:29 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:29 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:29 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:29 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:29 DEBUG  WindowsBackend: windows_language=English
09-19 04:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:29 DEBUG  WindowsBackend: bootloader=vista
09-19 04:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29297.3476563 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(C: hd 29297.3476563 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(G: hd 19687.5585938 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:29 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:29 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:29 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:29 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:29 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:29 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:29 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:29 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:29 DEBUG  CommonBackend: Searching for local CDs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:29 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:29 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:29 INFO   root: Running the CD menu...
09-19 04:29 DEBUG  WindowsFrontend: __init__...
09-19 04:29 DEBUG  WindowsFrontend: on_init...
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 INFO   root: CD menu finished
09-19 04:29 INFO   root: Already installed, running the uninstaller...
09-19 04:29 INFO   root: Running the uninstaller...
09-19 04:29 INFO   CommonBackend: This is the uninstaller running
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 INFO   root: Received settings
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 DEBUG  TaskList: # Running tasklist...
09-19 04:29 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:29 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:29 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:29 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:29 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29297.3476563 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19687.5585938 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:29 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:29 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:29 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:29 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:29 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:29 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:29 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:29 DEBUG  TaskList: # Finished tasklist
09-19 04:29 INFO   root: Almost finished uninstalling
09-19 04:29 INFO   root: Finished uninstallation
09-19 04:29 DEBUG  CommonBackend: Fetching basic info...
09-19 04:29 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:29 DEBUG  CommonBackend: platform=win32
09-19 04:29 DEBUG  CommonBackend: osname=nt
09-19 04:29 DEBUG  WindowsBackend: arch=amd64
09-19 04:29 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\data\isolist.ini
09-19 04:29 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:29 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:29 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:29 DEBUG  WindowsBackend: Fetching host info...
09-19 04:29 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:29 DEBUG  WindowsBackend: windows version=vista
09-19 04:29 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:29 DEBUG  WindowsBackend: windows_sp=None
09-19 04:29 DEBUG  WindowsBackend: windows_build=7600
09-19 04:29 DEBUG  WindowsBackend: gmt=6
09-19 04:29 DEBUG  WindowsBackend: country=US
09-19 04:29 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:29 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:29 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:29 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:29 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:29 DEBUG  WindowsBackend: windows_language=English
09-19 04:29 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:29 DEBUG  WindowsBackend: bootloader=vista
09-19 04:29 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29297.21875 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(C: hd 29297.21875 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:29 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:29 DEBUG  WindowsBackend: uninstaller_path=None
09-19 04:29 DEBUG  WindowsBackend: previous_target_dir=None
09-19 04:29 DEBUG  WindowsBackend: previous_distro_name=None
09-19 04:29 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:29 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:29 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:29 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:29 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:29 DEBUG  CommonBackend: Searching for local CDs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:29 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:29 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:29 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:29 INFO   root: Running the installer...
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 04:29 INFO   root: Received settings
09-19 04:29 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\translations, languages=['en_US', 'en']
09-19 04:29 DEBUG  TaskList: # Running tasklist...
09-19 04:29 DEBUG  TaskList: ## Running select_target_dir...
09-19 04:29 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 04:29 DEBUG  TaskList: ## Finished select_target_dir
09-19 04:29 DEBUG  TaskList: ## Running create_dir_structure...
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 04:29 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 04:29 DEBUG  TaskList: ## Finished create_dir_structure
09-19 04:29 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 04:29 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 04:29 DEBUG  TaskList: ## Running create_uninstaller...
09-19 04:29 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 04:29 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 04:29 DEBUG  TaskList: ## Finished create_uninstaller
09-19 04:29 DEBUG  TaskList: ## Running copy_installation_files...
09-19 04:29 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 04:29 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\winboot -> G:\ubuntu\winboot
09-19 04:29 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl3D7.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 04:29 DEBUG  TaskList: ## Finished copy_installation_files
09-19 04:29 DEBUG  TaskList: ## Running get_iso...
09-19 04:29 DEBUG  TaskList: New task copy_file
09-19 04:29 DEBUG  TaskList: ### Running copy_file...
09-19 04:30 DEBUG  TaskList: ### Finished copy_file
09-19 04:30 DEBUG  TaskList: New task check_iso
09-19 04:30 DEBUG  TaskList: ### Running check_iso...
09-19 04:30 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 04:30 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 04:30 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 04:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:30 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 04:30 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 04:30 DEBUG  TaskList: New task get_metalink
09-19 04:30 DEBUG  TaskList: #### Running get_metalink...
09-19 04:30 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:30 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:30 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 04:30 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 04:30 DEBUG  TaskList: #### Finished get_metalink
09-19 04:30 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 04:30 DEBUG  TaskList: ### Finished check_iso
09-19 04:30 DEBUG  TaskList: ## Finished get_iso
09-19 04:30 DEBUG  TaskList: ## Running extract_kernel...
09-19 04:30 DEBUG  CommonBackend: Copying files from CD J:\
09-19 04:30 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 04:30 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 04:30 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 04:30 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 04:30 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 04:30 DEBUG  TaskList: ## Finished extract_kernel
09-19 04:30 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 04:30 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 04:30 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 04:30 DEBUG  TaskList: ## Running create_preseed...
09-19 04:30 DEBUG  TaskList: ## Finished create_preseed
09-19 04:30 DEBUG  TaskList: ## Running modify_bootloader...
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 DEBUG  TaskList: ### Running modify_bcd...
09-19 04:30 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29297.21875 mb free ntfs)
09-19 04:30 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {9d96414c-c36f-11df-a39e-001b244c972d} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {9d96414c-c36f-11df-a39e-001b244c972d} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:30 DEBUG  TaskList: # Cancelling tasklist
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {9d96414c-c36f-11df-a39e-001b244c972d} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {9d96414c-c36f-11df-a39e-001b244c972d} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 DEBUG  TaskList: New task modify_bcd
09-19 04:30 DEBUG  TaskList: ## Finished modify_bootloader
09-19 04:30 DEBUG  TaskList: # Finished tasklist
09-19 04:31 INFO   root: === wubi 10.04 rev189 ===
09-19 04:31 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 04:31 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\data
09-19 04:31 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\bin\7z.exe
09-19 04:31 DEBUG  CommonBackend: Fetching basic info...
09-19 04:31 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 04:31 DEBUG  CommonBackend: platform=win32
09-19 04:31 DEBUG  CommonBackend: osname=nt
09-19 04:31 DEBUG  CommonBackend: language=en_US
09-19 04:31 DEBUG  CommonBackend: encoding=cp936
09-19 04:31 DEBUG  WindowsBackend: arch=amd64
09-19 04:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\data\isolist.ini
09-19 04:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:31 DEBUG  WindowsBackend: Fetching host info...
09-19 04:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:31 DEBUG  WindowsBackend: windows version=vista
09-19 04:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:31 DEBUG  WindowsBackend: windows_sp=None
09-19 04:31 DEBUG  WindowsBackend: windows_build=7600
09-19 04:31 DEBUG  WindowsBackend: gmt=6
09-19 04:31 DEBUG  WindowsBackend: country=US
09-19 04:31 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:31 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:31 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:31 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:31 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:31 DEBUG  WindowsBackend: windows_language=English
09-19 04:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:31 DEBUG  WindowsBackend: bootloader=vista
09-19 04:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29262.5898438 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(C: hd 29262.5898438 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:31 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:31 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:31 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:31 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:31 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:31 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:31 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:31 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:31 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:31 DEBUG  CommonBackend: Searching for local CDs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:31 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:31 INFO   root: Running the CD menu...
09-19 04:31 DEBUG  WindowsFrontend: __init__...
09-19 04:31 DEBUG  WindowsFrontend: on_init...
09-19 04:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\translations, languages=['en_US', 'en']
09-19 04:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl3EF3.tmp\translations, languages=['en_US', 'en']
09-19 04:31 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:31 DEBUG  root: application.on_quit
09-19 04:31 INFO   root: sys.exit
09-19 04:31 INFO   root: === wubi 10.04 rev189 ===
09-19 04:31 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 04:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
09-19 04:31 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\data
09-19 04:31 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\bin\7z.exe
09-19 04:31 DEBUG  CommonBackend: Fetching basic info...
09-19 04:31 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
09-19 04:31 DEBUG  CommonBackend: platform=win32
09-19 04:31 DEBUG  CommonBackend: osname=nt
09-19 04:31 DEBUG  CommonBackend: language=en_US
09-19 04:31 DEBUG  CommonBackend: encoding=cp936
09-19 04:31 DEBUG  WindowsBackend: arch=amd64
09-19 04:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\data\isolist.ini
09-19 04:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 04:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 04:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 04:31 DEBUG  WindowsBackend: Fetching host info...
09-19 04:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 04:31 DEBUG  WindowsBackend: windows version=vista
09-19 04:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 04:31 DEBUG  WindowsBackend: windows_sp=None
09-19 04:31 DEBUG  WindowsBackend: windows_build=7600
09-19 04:31 DEBUG  WindowsBackend: gmt=6
09-19 04:31 DEBUG  WindowsBackend: country=US
09-19 04:31 DEBUG  WindowsBackend: timezone=America/New_York
09-19 04:31 DEBUG  WindowsBackend: windows_username=TU TU
09-19 04:31 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 04:31 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 04:31 DEBUG  WindowsBackend: windows_language_code=1033
09-19 04:31 DEBUG  WindowsBackend: windows_language=English
09-19 04:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 04:31 DEBUG  WindowsBackend: bootloader=vista
09-19 04:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29267.4570313 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(C: hd 29267.4570313 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 04:31 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 04:31 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 04:31 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 04:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 04:31 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 04:31 DEBUG  WindowsBackend: keyboard_layout=us
09-19 04:31 DEBUG  WindowsBackend: keyboard_variant=
09-19 04:31 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 04:31 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 04:31 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 04:31 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 04:31 DEBUG  CommonBackend: Searching for local CDs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 04:31 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 04:31 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 04:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 04:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 04:31 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 04:31 INFO   root: Running the uninstaller...
09-19 04:31 INFO   CommonBackend: This is the uninstaller running
09-19 04:31 DEBUG  WindowsFrontend: __init__...
09-19 04:31 DEBUG  WindowsFrontend: on_init...
09-19 04:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\translations, languages=['en_US', 'en']
09-19 04:31 INFO   root: Received settings
09-19 04:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\translations, languages=['en_US', 'en']
09-19 04:31 DEBUG  TaskList: # Running tasklist...
09-19 04:31 DEBUG  TaskList: ## Running Backup ISO...
09-19 04:31 DEBUG  TaskList: ## Finished Backup ISO
09-19 04:31 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 04:31 DEBUG  WindowsBackend: Could not find bcd id
09-19 04:31 DEBUG  WindowsBackend: undo_bootini C:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29267.4570313 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: undo_bootini D:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32011.3359375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: undo_bootini E:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: undo_bootini G:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: undo_bootini H:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 04:31 DEBUG  WindowsBackend: undo_bootini I:
09-19 04:31 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 04:31 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 04:31 DEBUG  TaskList: ## Running Remove target dir...
09-19 04:31 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 04:32 DEBUG  TaskList: ## Finished Remove target dir
09-19 04:32 DEBUG  TaskList: ## Running Remove registry key...
09-19 04:32 DEBUG  TaskList: ## Finished Remove registry key
09-19 04:32 DEBUG  TaskList: # Finished tasklist
09-19 04:32 INFO   root: Almost finished uninstalling
09-19 04:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9B64.tmp\translations, languages=['en_US', 'en']
09-19 04:32 INFO   root: Finished uninstallation
09-19 04:32 DEBUG  root: application.quit
09-19 04:32 DEBUG  WindowsFrontend: frontend.quit
09-19 04:32 DEBUG  WindowsFrontend: frontend.on_quit
09-19 04:32 DEBUG  root: application.on_quit
09-19 04:32 INFO   root: sys.exit
09-19 05:00 INFO   root: === wubi 10.04 rev189 ===
09-19 05:00 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 05:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 05:00 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\data
09-19 05:00 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\bin\7z.exe
09-19 05:00 DEBUG  CommonBackend: Fetching basic info...
09-19 05:00 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 05:00 DEBUG  CommonBackend: platform=win32
09-19 05:00 DEBUG  CommonBackend: osname=nt
09-19 05:00 DEBUG  CommonBackend: language=en_US
09-19 05:00 DEBUG  CommonBackend: encoding=cp936
09-19 05:00 DEBUG  WindowsBackend: arch=amd64
09-19 05:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\data\isolist.ini
09-19 05:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 05:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 05:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 05:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 05:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 05:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 05:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 05:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 05:00 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 05:00 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 05:00 DEBUG  WindowsBackend: Fetching host info...
09-19 05:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 05:00 DEBUG  WindowsBackend: windows version=vista
09-19 05:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 05:00 DEBUG  WindowsBackend: windows_sp=None
09-19 05:00 DEBUG  WindowsBackend: windows_build=7600
09-19 05:00 DEBUG  WindowsBackend: gmt=6
09-19 05:00 DEBUG  WindowsBackend: country=US
09-19 05:00 DEBUG  WindowsBackend: timezone=America/New_York
09-19 05:00 DEBUG  WindowsBackend: windows_username=TU TU
09-19 05:00 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 05:00 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 05:00 DEBUG  WindowsBackend: windows_language_code=1033
09-19 05:00 DEBUG  WindowsBackend: windows_language=English
09-19 05:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 05:00 DEBUG  WindowsBackend: bootloader=vista
09-19 05:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29333.9101563 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(C: hd 29333.9101563 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 05:00 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 05:00 DEBUG  WindowsBackend: uninstaller_path=None
09-19 05:00 DEBUG  WindowsBackend: previous_target_dir=None
09-19 05:00 DEBUG  WindowsBackend: previous_distro_name=None
09-19 05:00 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 05:00 DEBUG  WindowsBackend: keyboard_layout=us
09-19 05:00 DEBUG  WindowsBackend: keyboard_variant=
09-19 05:00 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 05:00 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 05:00 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 05:00 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 05:00 DEBUG  CommonBackend: Searching for local CDs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 05:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:00 INFO   root: Running the installer...
09-19 05:00 DEBUG  WindowsFrontend: __init__...
09-19 05:00 DEBUG  WindowsFrontend: on_init...
09-19 05:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\translations, languages=['en_US', 'en']
09-19 05:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\translations, languages=['en_US', 'en']
09-19 05:00 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 05:00 INFO   root: Received settings
09-19 05:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\translations, languages=['en_US', 'en']
09-19 05:00 DEBUG  TaskList: # Running tasklist...
09-19 05:00 DEBUG  TaskList: ## Running select_target_dir...
09-19 05:00 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 05:00 DEBUG  TaskList: ## Finished select_target_dir
09-19 05:00 DEBUG  TaskList: ## Running create_dir_structure...
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 05:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 05:00 DEBUG  TaskList: ## Finished create_dir_structure
09-19 05:00 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 05:00 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 05:00 DEBUG  TaskList: ## Running create_uninstaller...
09-19 05:00 DEBUG  WindowsBackend: Copying uninstaller H:\Drive D\Download\Ubuntu 10.04\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 05:01 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 05:01 DEBUG  TaskList: ## Finished create_uninstaller
09-19 05:01 DEBUG  TaskList: ## Running copy_installation_files...
09-19 05:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 05:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\winboot -> G:\ubuntu\winboot
09-19 05:01 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 05:01 DEBUG  TaskList: ## Finished copy_installation_files
09-19 05:01 DEBUG  TaskList: ## Running get_iso...
09-19 05:01 DEBUG  CommonBackend: Searching for local CD
09-19 05:01 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5DA9.tmp\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 05:01 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 05:01 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 05:01 DEBUG  CommonBackend: Searching for local ISO
09-19 05:01 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  WindowsBackend:   extracting .disk\info from H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 05:01 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 05:01 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  CommonBackend: Trying to use ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  TaskList: New task check_iso
09-19 05:01 DEBUG  TaskList: ### Running check_iso...
09-19 05:01 DEBUG  CommonBackend: Checking H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 05:01 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 05:01 DEBUG  TaskList: New task get_metalink
09-19 05:01 DEBUG  TaskList: #### Running get_metalink...
09-19 05:01 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 05:01 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 05:01 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 05:01 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 05:01 DEBUG  TaskList: #### Finished get_metalink
09-19 05:01 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso, ignoring
09-19 05:01 DEBUG  TaskList: ### Finished check_iso
09-19 05:01 DEBUG  TaskList: New task copy_file
09-19 05:01 DEBUG  CommonBackend: Copying H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso > G:\ubuntu\install\installation.iso
09-19 05:01 DEBUG  TaskList: ### Running copy_file...
09-19 05:01 DEBUG  TaskList: ### Finished copy_file
09-19 05:01 DEBUG  TaskList: ## Finished get_iso
09-19 05:01 DEBUG  TaskList: ## Running extract_kernel...
09-19 05:01 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
09-19 05:01 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
09-19 05:01 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
09-19 05:01 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
09-19 05:01 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 05:01 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 05:01 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 05:01 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 05:01 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 05:01 DEBUG  TaskList: ## Finished extract_kernel
09-19 05:01 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 05:01 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 05:01 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 05:01 DEBUG  TaskList: ## Running create_preseed...
09-19 05:01 DEBUG  TaskList: ## Finished create_preseed
09-19 05:01 DEBUG  TaskList: ## Running modify_bootloader...
09-19 05:01 DEBUG  TaskList: New task modify_bcd
09-19 05:01 DEBUG  TaskList: ### Running modify_bcd...
09-19 05:01 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29333.9101563 mb free ntfs)
09-19 05:01 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f6-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f6-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 05:01 DEBUG  TaskList: # Cancelling tasklist
09-19 05:01 DEBUG  TaskList: New task modify_bcd
09-19 05:01 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f6-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f6-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 05:01 DEBUG  TaskList: New task modify_bcd
09-19 05:01 DEBUG  TaskList: New task modify_bcd
09-19 05:01 DEBUG  TaskList: New task modify_bcd
09-19 05:01 DEBUG  TaskList: ## Finished modify_bootloader
09-19 05:01 DEBUG  TaskList: # Finished tasklist
09-19 09:56 INFO   root: === wubi 10.04 rev189 ===
09-19 09:56 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 09:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 09:56 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\data
09-19 09:56 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\bin\7z.exe
09-19 09:56 DEBUG  CommonBackend: Fetching basic info...
09-19 09:56 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 09:56 DEBUG  CommonBackend: platform=win32
09-19 09:56 DEBUG  CommonBackend: osname=nt
09-19 09:56 DEBUG  CommonBackend: language=en_US
09-19 09:56 DEBUG  CommonBackend: encoding=cp936
09-19 09:56 DEBUG  WindowsBackend: arch=amd64
09-19 09:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\data\isolist.ini
09-19 09:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 09:56 DEBUG  WindowsBackend: Fetching host info...
09-19 09:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 09:56 DEBUG  WindowsBackend: windows version=vista
09-19 09:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 09:56 DEBUG  WindowsBackend: windows_sp=None
09-19 09:56 DEBUG  WindowsBackend: windows_build=7600
09-19 09:56 DEBUG  WindowsBackend: gmt=6
09-19 09:56 DEBUG  WindowsBackend: country=US
09-19 09:56 DEBUG  WindowsBackend: timezone=America/New_York
09-19 09:56 DEBUG  WindowsBackend: windows_username=TU TU
09-19 09:56 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 09:56 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 09:56 DEBUG  WindowsBackend: windows_language_code=1033
09-19 09:56 DEBUG  WindowsBackend: windows_language=English
09-19 09:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 09:56 DEBUG  WindowsBackend: bootloader=vista
09-19 09:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29336.7851563 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(C: hd 29336.7851563 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.25 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 09:56 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 09:56 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 09:56 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 09:56 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 09:56 DEBUG  WindowsBackend: keyboard_layout=us
09-19 09:56 DEBUG  WindowsBackend: keyboard_variant=
09-19 09:56 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 09:56 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 09:56 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 09:56 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 09:56 DEBUG  CommonBackend: Searching for local CDs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 INFO   root: Already installed, running the uninstaller...
09-19 09:56 INFO   root: Running the uninstaller...
09-19 09:56 INFO   CommonBackend: This is the uninstaller running
09-19 09:56 DEBUG  WindowsFrontend: __init__...
09-19 09:56 DEBUG  WindowsFrontend: on_init...
09-19 09:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\translations, languages=['en_US', 'en']
09-19 09:56 INFO   root: Received settings
09-19 09:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\translations, languages=['en_US', 'en']
09-19 09:56 DEBUG  TaskList: # Running tasklist...
09-19 09:56 DEBUG  TaskList: ## Running Backup ISO...
09-19 09:56 DEBUG  TaskList: ## Finished Backup ISO
09-19 09:56 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 09:56 DEBUG  WindowsBackend: Could not find bcd id
09-19 09:56 DEBUG  WindowsBackend: undo_bootini C:
09-19 09:56 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29336.7851563 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: undo_bootini D:
09-19 09:56 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.25 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: undo_bootini E:
09-19 09:56 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: undo_bootini G:
09-19 09:56 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: undo_bootini H:
09-19 09:56 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:56 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 09:56 DEBUG  TaskList: ## Running Remove target dir...
09-19 09:56 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 09:56 DEBUG  TaskList: ## Finished Remove target dir
09-19 09:56 DEBUG  TaskList: ## Running Remove registry key...
09-19 09:56 DEBUG  TaskList: ## Finished Remove registry key
09-19 09:56 DEBUG  TaskList: # Finished tasklist
09-19 09:56 INFO   root: Almost finished uninstalling
09-19 09:56 INFO   root: Finished uninstallation
09-19 09:56 DEBUG  CommonBackend: Fetching basic info...
09-19 09:56 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 09:56 DEBUG  CommonBackend: platform=win32
09-19 09:56 DEBUG  CommonBackend: osname=nt
09-19 09:56 DEBUG  WindowsBackend: arch=amd64
09-19 09:56 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\data\isolist.ini
09-19 09:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 09:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 09:56 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 09:56 DEBUG  WindowsBackend: Fetching host info...
09-19 09:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 09:56 DEBUG  WindowsBackend: windows version=vista
09-19 09:56 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 09:56 DEBUG  WindowsBackend: windows_sp=None
09-19 09:56 DEBUG  WindowsBackend: windows_build=7600
09-19 09:56 DEBUG  WindowsBackend: gmt=6
09-19 09:56 DEBUG  WindowsBackend: country=US
09-19 09:56 DEBUG  WindowsBackend: timezone=America/New_York
09-19 09:56 DEBUG  WindowsBackend: windows_username=TU TU
09-19 09:56 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 09:56 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 09:56 DEBUG  WindowsBackend: windows_language_code=1033
09-19 09:56 DEBUG  WindowsBackend: windows_language=English
09-19 09:56 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 09:56 DEBUG  WindowsBackend: bootloader=vista
09-19 09:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29336.8398438 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(C: hd 29336.8398438 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.25 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:56 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 09:56 DEBUG  WindowsBackend: uninstaller_path=None
09-19 09:56 DEBUG  WindowsBackend: previous_target_dir=None
09-19 09:56 DEBUG  WindowsBackend: previous_distro_name=None
09-19 09:56 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 09:56 DEBUG  WindowsBackend: keyboard_layout=us
09-19 09:56 DEBUG  WindowsBackend: keyboard_variant=
09-19 09:56 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 09:56 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 09:56 DEBUG  CommonBackend: Searching for local CDs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:56 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:56 INFO   root: Running the installer...
09-19 09:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\translations, languages=['en_US', 'en']
09-19 09:56 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\translations, languages=['en_US', 'en']
09-19 09:57 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 09:57 INFO   root: Received settings
09-19 09:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\translations, languages=['en_US', 'en']
09-19 09:57 DEBUG  TaskList: # Running tasklist...
09-19 09:57 DEBUG  TaskList: ## Running select_target_dir...
09-19 09:57 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 09:57 DEBUG  TaskList: ## Finished select_target_dir
09-19 09:57 DEBUG  TaskList: ## Running create_dir_structure...
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 09:57 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 09:57 DEBUG  TaskList: ## Finished create_dir_structure
09-19 09:57 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 09:57 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 09:57 DEBUG  TaskList: ## Running create_uninstaller...
09-19 09:57 DEBUG  WindowsBackend: Copying uninstaller H:\Drive D\Download\Ubuntu 10.04\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 09:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 09:57 DEBUG  TaskList: ## Finished create_uninstaller
09-19 09:57 DEBUG  TaskList: ## Running copy_installation_files...
09-19 09:57 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 09:57 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\winboot -> G:\ubuntu\winboot
09-19 09:57 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 09:57 DEBUG  TaskList: ## Finished copy_installation_files
09-19 09:57 DEBUG  TaskList: ## Running get_iso...
09-19 09:57 DEBUG  CommonBackend: Searching for local CD
09-19 09:57 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl9F0C.tmp\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:57 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:57 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:57 DEBUG  CommonBackend: Searching for local ISO
09-19 09:57 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  WindowsBackend:   extracting .disk\info from H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 09:57 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 09:57 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  CommonBackend: Trying to use ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  TaskList: New task check_iso
09-19 09:57 DEBUG  TaskList: ### Running check_iso...
09-19 09:57 DEBUG  CommonBackend: Checking H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 09:57 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 09:57 DEBUG  TaskList: New task get_metalink
09-19 09:57 DEBUG  TaskList: #### Running get_metalink...
09-19 09:57 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 09:57 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 09:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 09:57 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 09:57 DEBUG  TaskList: #### Finished get_metalink
09-19 09:57 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso, ignoring
09-19 09:57 DEBUG  TaskList: ### Finished check_iso
09-19 09:57 DEBUG  TaskList: New task copy_file
09-19 09:57 DEBUG  CommonBackend: Copying H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso > G:\ubuntu\install\installation.iso
09-19 09:57 DEBUG  TaskList: ### Running copy_file...
09-19 09:57 DEBUG  TaskList: ### Finished copy_file
09-19 09:57 DEBUG  TaskList: ## Finished get_iso
09-19 09:57 DEBUG  TaskList: ## Running extract_kernel...
09-19 09:57 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
09-19 09:57 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
09-19 09:57 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
09-19 09:57 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
09-19 09:57 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 09:57 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 09:57 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 09:57 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 09:57 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 09:57 DEBUG  TaskList: ## Finished extract_kernel
09-19 09:57 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 09:57 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 09:57 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 09:57 DEBUG  TaskList: ## Running create_preseed...
09-19 09:57 DEBUG  TaskList: ## Finished create_preseed
09-19 09:57 DEBUG  TaskList: ## Running modify_bootloader...
09-19 09:57 DEBUG  TaskList: New task modify_bcd
09-19 09:57 DEBUG  TaskList: ### Running modify_bcd...
09-19 09:57 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29336.8398438 mb free ntfs)
09-19 09:57 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f7-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f7-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 09:57 DEBUG  TaskList: # Cancelling tasklist
09-19 09:57 DEBUG  TaskList: New task modify_bcd
09-19 09:57 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f7-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f7-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 09:57 DEBUG  TaskList: New task modify_bcd
09-19 09:57 DEBUG  TaskList: New task modify_bcd
09-19 09:57 DEBUG  TaskList: New task modify_bcd
09-19 09:57 DEBUG  TaskList: ## Finished modify_bootloader
09-19 09:57 DEBUG  TaskList: # Finished tasklist
09-19 09:58 INFO   root: === wubi 10.04 rev189 ===
09-19 09:58 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 09:58 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
09-19 09:58 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\data
09-19 09:58 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\bin\7z.exe
09-19 09:58 DEBUG  CommonBackend: Fetching basic info...
09-19 09:58 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
09-19 09:58 DEBUG  CommonBackend: platform=win32
09-19 09:58 DEBUG  CommonBackend: osname=nt
09-19 09:58 DEBUG  CommonBackend: language=en_US
09-19 09:58 DEBUG  CommonBackend: encoding=cp936
09-19 09:58 DEBUG  WindowsBackend: arch=amd64
09-19 09:58 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\data\isolist.ini
09-19 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 09:58 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 09:58 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 09:58 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 09:58 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 09:58 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 09:58 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 09:58 DEBUG  WindowsBackend: Fetching host info...
09-19 09:58 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 09:58 DEBUG  WindowsBackend: windows version=vista
09-19 09:58 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 09:58 DEBUG  WindowsBackend: windows_sp=None
09-19 09:58 DEBUG  WindowsBackend: windows_build=7600
09-19 09:58 DEBUG  WindowsBackend: gmt=6
09-19 09:58 DEBUG  WindowsBackend: country=US
09-19 09:58 DEBUG  WindowsBackend: timezone=America/New_York
09-19 09:58 DEBUG  WindowsBackend: windows_username=TU TU
09-19 09:58 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 09:58 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 09:58 DEBUG  WindowsBackend: windows_language_code=1033
09-19 09:58 DEBUG  WindowsBackend: windows_language=English
09-19 09:58 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 09:58 DEBUG  WindowsBackend: bootloader=vista
09-19 09:58 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29204.953125 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(C: hd 29204.953125 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 09:58 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 09:58 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 09:58 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 09:58 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 09:58 DEBUG  WindowsBackend: keyboard_layout=us
09-19 09:58 DEBUG  WindowsBackend: keyboard_variant=
09-19 09:58 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 09:58 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 09:58 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 09:58 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 09:58 DEBUG  CommonBackend: Searching for local CDs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:58 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:58 INFO   root: Running the uninstaller...
09-19 09:58 INFO   CommonBackend: This is the uninstaller running
09-19 09:58 DEBUG  WindowsFrontend: __init__...
09-19 09:58 DEBUG  WindowsFrontend: on_init...
09-19 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\translations, languages=['en_US', 'en']
09-19 09:58 INFO   root: Received settings
09-19 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\translations, languages=['en_US', 'en']
09-19 09:58 DEBUG  TaskList: # Running tasklist...
09-19 09:58 DEBUG  TaskList: ## Running Backup ISO...
09-19 09:58 DEBUG  TaskList: ## Finished Backup ISO
09-19 09:58 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 09:58 DEBUG  WindowsBackend: Could not find bcd id
09-19 09:58 DEBUG  WindowsBackend: undo_bootini C:
09-19 09:58 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29204.953125 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: undo_bootini D:
09-19 09:58 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2421875 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: undo_bootini E:
09-19 09:58 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: undo_bootini G:
09-19 09:58 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 09:58 DEBUG  WindowsBackend: undo_bootini H:
09-19 09:58 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:58 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 09:58 DEBUG  TaskList: ## Running Remove target dir...
09-19 09:58 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 09:58 DEBUG  TaskList: ## Finished Remove target dir
09-19 09:58 DEBUG  TaskList: ## Running Remove registry key...
09-19 09:58 DEBUG  TaskList: ## Finished Remove registry key
09-19 09:58 DEBUG  TaskList: # Finished tasklist
09-19 09:58 INFO   root: Almost finished uninstalling
09-19 09:58 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl5ED1.tmp\translations, languages=['en_US', 'en']
09-19 09:58 INFO   root: Finished uninstallation
09-19 09:58 DEBUG  root: application.quit
09-19 09:58 DEBUG  WindowsFrontend: frontend.quit
09-19 09:58 DEBUG  WindowsFrontend: frontend.on_quit
09-19 09:58 DEBUG  root: application.on_quit
09-19 09:58 INFO   root: sys.exit
09-19 09:59 INFO   root: === wubi 10.04 rev189 ===
09-19 09:59 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 09:59 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 09:59 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\data
09-19 09:59 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\bin\7z.exe
09-19 09:59 DEBUG  CommonBackend: Fetching basic info...
09-19 09:59 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 09:59 DEBUG  CommonBackend: platform=win32
09-19 09:59 DEBUG  CommonBackend: osname=nt
09-19 09:59 DEBUG  CommonBackend: language=en_US
09-19 09:59 DEBUG  CommonBackend: encoding=cp936
09-19 09:59 DEBUG  WindowsBackend: arch=amd64
09-19 09:59 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\data\isolist.ini
09-19 09:59 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 09:59 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 09:59 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 09:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 09:59 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 09:59 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 09:59 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 09:59 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 09:59 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 09:59 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 09:59 DEBUG  WindowsBackend: Fetching host info...
09-19 09:59 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 09:59 DEBUG  WindowsBackend: windows version=vista
09-19 09:59 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 09:59 DEBUG  WindowsBackend: windows_sp=None
09-19 09:59 DEBUG  WindowsBackend: windows_build=7600
09-19 09:59 DEBUG  WindowsBackend: gmt=6
09-19 09:59 DEBUG  WindowsBackend: country=US
09-19 09:59 DEBUG  WindowsBackend: timezone=America/New_York
09-19 09:59 DEBUG  WindowsBackend: windows_username=TU TU
09-19 09:59 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 09:59 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 09:59 DEBUG  WindowsBackend: windows_language_code=1033
09-19 09:59 DEBUG  WindowsBackend: windows_language=English
09-19 09:59 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 09:59 DEBUG  WindowsBackend: bootloader=vista
09-19 09:59 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29203.2539063 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(C: hd 29203.2539063 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 09:59 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 09:59 DEBUG  WindowsBackend: uninstaller_path=None
09-19 09:59 DEBUG  WindowsBackend: previous_target_dir=None
09-19 09:59 DEBUG  WindowsBackend: previous_distro_name=None
09-19 09:59 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 09:59 DEBUG  WindowsBackend: keyboard_layout=us
09-19 09:59 DEBUG  WindowsBackend: keyboard_variant=
09-19 09:59 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 09:59 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 09:59 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 09:59 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 09:59 DEBUG  CommonBackend: Searching for local CDs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 09:59 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 09:59 INFO   root: Running the installer...
09-19 09:59 DEBUG  WindowsFrontend: __init__...
09-19 09:59 DEBUG  WindowsFrontend: on_init...
09-19 09:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\translations, languages=['en_US', 'en']
09-19 09:59 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\translations, languages=['en_US', 'en']
09-19 10:00 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 10:00 INFO   root: Received settings
09-19 10:00 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\translations, languages=['en_US', 'en']
09-19 10:00 DEBUG  TaskList: # Running tasklist...
09-19 10:00 DEBUG  TaskList: ## Running select_target_dir...
09-19 10:00 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 10:00 DEBUG  TaskList: ## Finished select_target_dir
09-19 10:00 DEBUG  TaskList: ## Running create_dir_structure...
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 10:00 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 10:00 DEBUG  TaskList: ## Finished create_dir_structure
09-19 10:00 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 10:00 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 10:00 DEBUG  TaskList: ## Running create_uninstaller...
09-19 10:00 DEBUG  WindowsBackend: Copying uninstaller H:\Drive D\Download\Ubuntu 10.04\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 10:00 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 10:00 DEBUG  TaskList: ## Finished create_uninstaller
09-19 10:00 DEBUG  TaskList: ## Running copy_installation_files...
09-19 10:00 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 10:00 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\winboot -> G:\ubuntu\winboot
09-19 10:00 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 10:00 DEBUG  TaskList: ## Finished copy_installation_files
09-19 10:00 DEBUG  TaskList: ## Running get_iso...
09-19 10:00 DEBUG  CommonBackend: Searching for local CD
09-19 10:00 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl782B.tmp\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:00 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:00 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:00 DEBUG  CommonBackend: Searching for local ISO
09-19 10:00 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  WindowsBackend:   extracting .disk\info from H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:00 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  CommonBackend: Trying to use ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  TaskList: New task check_iso
09-19 10:00 DEBUG  TaskList: ### Running check_iso...
09-19 10:00 DEBUG  CommonBackend: Checking H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:00 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 10:00 DEBUG  TaskList: New task get_metalink
09-19 10:00 DEBUG  TaskList: #### Running get_metalink...
09-19 10:00 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:00 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:00 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:00 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:00 DEBUG  TaskList: #### Finished get_metalink
09-19 10:00 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso, ignoring
09-19 10:00 DEBUG  TaskList: ### Finished check_iso
09-19 10:00 DEBUG  TaskList: New task copy_file
09-19 10:00 DEBUG  CommonBackend: Copying H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso > G:\ubuntu\install\installation.iso
09-19 10:00 DEBUG  TaskList: ### Running copy_file...
09-19 10:00 DEBUG  TaskList: ### Finished copy_file
09-19 10:00 DEBUG  TaskList: ## Finished get_iso
09-19 10:00 DEBUG  TaskList: ## Running extract_kernel...
09-19 10:00 DEBUG  CommonBackend: Extracting files from ISO G:\ubuntu\install\installation.iso
09-19 10:00 DEBUG  WindowsBackend:   extracting md5sum.txt from G:\ubuntu\install\installation.iso
09-19 10:00 DEBUG  WindowsBackend:   extracting casper\vmlinuz from G:\ubuntu\install\installation.iso
09-19 10:00 DEBUG  WindowsBackend:   extracting casper\initrd.lz from G:\ubuntu\install\installation.iso
09-19 10:00 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 10:00 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 10:00 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 10:00 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 10:00 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 10:00 DEBUG  TaskList: ## Finished extract_kernel
09-19 10:00 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 10:00 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 10:00 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 10:00 DEBUG  TaskList: ## Running create_preseed...
09-19 10:00 DEBUG  TaskList: ## Finished create_preseed
09-19 10:00 DEBUG  TaskList: ## Running modify_bootloader...
09-19 10:00 DEBUG  TaskList: New task modify_bcd
09-19 10:00 DEBUG  TaskList: ### Running modify_bcd...
09-19 10:00 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29203.2539063 mb free ntfs)
09-19 10:01 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f9-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f9-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:01 DEBUG  TaskList: # Cancelling tasklist
09-19 10:01 DEBUG  TaskList: New task modify_bcd
09-19 10:01 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f9-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71f9-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:01 DEBUG  TaskList: New task modify_bcd
09-19 10:01 DEBUG  TaskList: New task modify_bcd
09-19 10:01 DEBUG  TaskList: New task modify_bcd
09-19 10:01 DEBUG  TaskList: ## Finished modify_bootloader
09-19 10:01 DEBUG  TaskList: # Finished tasklist
09-19 10:20 INFO   root: === wubi 10.04 rev189 ===
09-19 10:20 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 10:20 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 10:20 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\data
09-19 10:20 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\bin\7z.exe
09-19 10:20 DEBUG  CommonBackend: Fetching basic info...
09-19 10:20 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 10:20 DEBUG  CommonBackend: platform=win32
09-19 10:20 DEBUG  CommonBackend: osname=nt
09-19 10:20 DEBUG  CommonBackend: language=en_US
09-19 10:20 DEBUG  CommonBackend: encoding=cp936
09-19 10:20 DEBUG  WindowsBackend: arch=amd64
09-19 10:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\data\isolist.ini
09-19 10:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:20 DEBUG  WindowsBackend: Fetching host info...
09-19 10:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:20 DEBUG  WindowsBackend: windows version=vista
09-19 10:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:20 DEBUG  WindowsBackend: windows_sp=None
09-19 10:20 DEBUG  WindowsBackend: windows_build=7600
09-19 10:20 DEBUG  WindowsBackend: gmt=6
09-19 10:20 DEBUG  WindowsBackend: country=US
09-19 10:20 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:20 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:20 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:20 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:20 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:20 DEBUG  WindowsBackend: windows_language=English
09-19 10:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:20 DEBUG  WindowsBackend: bootloader=vista
09-19 10:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29225.6015625 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(C: hd 29225.6015625 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 10:20 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 10:20 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 10:20 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 10:20 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:20 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:20 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:20 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 10:20 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 10:20 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:20 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:20 DEBUG  CommonBackend: Searching for local CDs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 INFO   root: Already installed, running the uninstaller...
09-19 10:20 INFO   root: Running the uninstaller...
09-19 10:20 INFO   CommonBackend: This is the uninstaller running
09-19 10:20 DEBUG  WindowsFrontend: __init__...
09-19 10:20 DEBUG  WindowsFrontend: on_init...
09-19 10:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\translations, languages=['en_US', 'en']
09-19 10:20 INFO   root: Received settings
09-19 10:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\translations, languages=['en_US', 'en']
09-19 10:20 DEBUG  TaskList: # Running tasklist...
09-19 10:20 DEBUG  TaskList: ## Running Backup ISO...
09-19 10:20 DEBUG  TaskList: ## Finished Backup ISO
09-19 10:20 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 10:20 DEBUG  WindowsBackend: Could not find bcd id
09-19 10:20 DEBUG  WindowsBackend: undo_bootini C:
09-19 10:20 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29225.6015625 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: undo_bootini D:
09-19 10:20 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2421875 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: undo_bootini E:
09-19 10:20 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: undo_bootini G:
09-19 10:20 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: undo_bootini H:
09-19 10:20 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:20 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 10:20 DEBUG  TaskList: ## Running Remove target dir...
09-19 10:20 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 10:20 DEBUG  TaskList: ## Finished Remove target dir
09-19 10:20 DEBUG  TaskList: ## Running Remove registry key...
09-19 10:20 DEBUG  TaskList: ## Finished Remove registry key
09-19 10:20 DEBUG  TaskList: # Finished tasklist
09-19 10:20 INFO   root: Almost finished uninstalling
09-19 10:20 INFO   root: Finished uninstallation
09-19 10:20 DEBUG  CommonBackend: Fetching basic info...
09-19 10:20 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 10:20 DEBUG  CommonBackend: platform=win32
09-19 10:20 DEBUG  CommonBackend: osname=nt
09-19 10:20 DEBUG  WindowsBackend: arch=amd64
09-19 10:20 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\data\isolist.ini
09-19 10:20 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:20 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:20 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:20 DEBUG  WindowsBackend: Fetching host info...
09-19 10:20 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:20 DEBUG  WindowsBackend: windows version=vista
09-19 10:20 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:20 DEBUG  WindowsBackend: windows_sp=None
09-19 10:20 DEBUG  WindowsBackend: windows_build=7600
09-19 10:20 DEBUG  WindowsBackend: gmt=6
09-19 10:20 DEBUG  WindowsBackend: country=US
09-19 10:20 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:20 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:20 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:20 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:20 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:20 DEBUG  WindowsBackend: windows_language=English
09-19 10:20 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:20 DEBUG  WindowsBackend: bootloader=vista
09-19 10:20 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29223.0976563 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(C: hd 29223.0976563 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:20 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 10:20 DEBUG  WindowsBackend: uninstaller_path=None
09-19 10:20 DEBUG  WindowsBackend: previous_target_dir=None
09-19 10:20 DEBUG  WindowsBackend: previous_distro_name=None
09-19 10:20 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:20 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:20 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:20 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:20 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:20 DEBUG  CommonBackend: Searching for local CDs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:20 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:20 INFO   root: Running the installer...
09-19 10:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\translations, languages=['en_US', 'en']
09-19 10:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\translations, languages=['en_US', 'en']
09-19 10:20 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 10:20 INFO   root: Received settings
09-19 10:20 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\translations, languages=['en_US', 'en']
09-19 10:20 DEBUG  TaskList: # Running tasklist...
09-19 10:20 DEBUG  TaskList: ## Running select_target_dir...
09-19 10:20 INFO   WindowsBackend: Installing into E:\ubuntu
09-19 10:20 DEBUG  TaskList: ## Finished select_target_dir
09-19 10:20 DEBUG  TaskList: ## Running create_dir_structure...
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
09-19 10:20 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
09-19 10:20 DEBUG  TaskList: ## Finished create_dir_structure
09-19 10:20 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 10:20 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 10:20 DEBUG  TaskList: ## Running create_uninstaller...
09-19 10:20 DEBUG  WindowsBackend: Copying uninstaller H:\Drive D\Download\Ubuntu 10.04\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 10:20 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 10:20 DEBUG  TaskList: ## Finished create_uninstaller
09-19 10:21 DEBUG  TaskList: ## Running copy_installation_files...
09-19 10:21 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
09-19 10:21 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\winboot -> E:\ubuntu\winboot
09-19 10:21 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
09-19 10:21 DEBUG  TaskList: ## Finished copy_installation_files
09-19 10:21 DEBUG  TaskList: ## Running get_iso...
09-19 10:21 DEBUG  CommonBackend: Searching for local CD
09-19 10:21 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl71B5.tmp\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:21 DEBUG  CommonBackend: Searching for local ISO
09-19 10:21 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  WindowsBackend:   extracting .disk\info from H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:21 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  CommonBackend: Trying to use ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  TaskList: New task check_iso
09-19 10:21 DEBUG  TaskList: ### Running check_iso...
09-19 10:21 DEBUG  CommonBackend: Checking H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  Distro:   checking Ubuntu ISO H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 INFO   Distro: Found a valid iso for Ubuntu: H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso
09-19 10:21 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 10:21 DEBUG  TaskList: New task get_metalink
09-19 10:21 DEBUG  TaskList: #### Running get_metalink...
09-19 10:21 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > E:\ubuntu\install
09-19 10:21 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:21 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > E:\ubuntu\install
09-19 10:21 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:21 DEBUG  TaskList: #### Finished get_metalink
09-19 10:21 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso, ignoring
09-19 10:21 DEBUG  TaskList: ### Finished check_iso
09-19 10:21 DEBUG  TaskList: New task copy_file
09-19 10:21 DEBUG  CommonBackend: Copying H:\Drive D\Download\Ubuntu 10.04\ubuntu-10.04-desktop-i386.iso > E:\ubuntu\install\installation.iso
09-19 10:21 DEBUG  TaskList: ### Running copy_file...
09-19 10:21 DEBUG  TaskList: ### Finished copy_file
09-19 10:21 DEBUG  TaskList: ## Finished get_iso
09-19 10:21 DEBUG  TaskList: ## Running extract_kernel...
09-19 10:21 DEBUG  CommonBackend: Extracting files from ISO E:\ubuntu\install\installation.iso
09-19 10:21 DEBUG  WindowsBackend:   extracting md5sum.txt from E:\ubuntu\install\installation.iso
09-19 10:21 DEBUG  WindowsBackend:   extracting casper\vmlinuz from E:\ubuntu\install\installation.iso
09-19 10:21 DEBUG  WindowsBackend:   extracting casper\initrd.lz from E:\ubuntu\install\installation.iso
09-19 10:21 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 10:21 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\vmlinuz
09-19 10:21 DEBUG  CommonBackend:   E:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 10:21 DEBUG  CommonBackend:   checking E:\ubuntu\install\boot\initrd.lz
09-19 10:21 DEBUG  CommonBackend:   E:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 10:21 DEBUG  TaskList: ## Finished extract_kernel
09-19 10:21 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 10:21 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 10:21 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 10:21 DEBUG  TaskList: ## Running create_preseed...
09-19 10:21 DEBUG  TaskList: ## Finished create_preseed
09-19 10:21 DEBUG  TaskList: ## Running modify_bootloader...
09-19 10:21 DEBUG  TaskList: New task modify_bcd
09-19 10:21 DEBUG  TaskList: ### Running modify_bcd...
09-19 10:21 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 29223.0976563 mb free ntfs)
09-19 10:21 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fb-c3ed-11df-b86d-c93a6949abcf} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fb-c3ed-11df-b86d-c93a6949abcf} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:21 DEBUG  TaskList: # Cancelling tasklist
09-19 10:21 DEBUG  TaskList: New task modify_bcd
09-19 10:21 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fb-c3ed-11df-b86d-c93a6949abcf} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fb-c3ed-11df-b86d-c93a6949abcf} device partition=E:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:21 DEBUG  TaskList: New task modify_bcd
09-19 10:21 DEBUG  TaskList: New task modify_bcd
09-19 10:21 DEBUG  TaskList: New task modify_bcd
09-19 10:21 DEBUG  TaskList: ## Finished modify_bootloader
09-19 10:21 DEBUG  TaskList: # Finished tasklist
09-19 10:22 INFO   root: === wubi 10.04 rev189 ===
09-19 10:22 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 10:22 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubuntu\\uninstall-wubi.exe"']
09-19 10:22 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\data
09-19 10:22 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\bin\7z.exe
09-19 10:22 DEBUG  CommonBackend: Fetching basic info...
09-19 10:22 DEBUG  CommonBackend: original_exe=E:\ubuntu\uninstall-wubi.exe
09-19 10:22 DEBUG  CommonBackend: platform=win32
09-19 10:22 DEBUG  CommonBackend: osname=nt
09-19 10:22 DEBUG  CommonBackend: language=en_US
09-19 10:22 DEBUG  CommonBackend: encoding=cp936
09-19 10:22 DEBUG  WindowsBackend: arch=amd64
09-19 10:22 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\data\isolist.ini
09-19 10:22 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:22 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:22 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:22 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:22 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:22 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:22 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:22 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:22 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:22 DEBUG  WindowsBackend: Fetching host info...
09-19 10:22 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:22 DEBUG  WindowsBackend: windows version=vista
09-19 10:22 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:22 DEBUG  WindowsBackend: windows_sp=None
09-19 10:22 DEBUG  WindowsBackend: windows_build=7600
09-19 10:22 DEBUG  WindowsBackend: gmt=6
09-19 10:22 DEBUG  WindowsBackend: country=US
09-19 10:22 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:22 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:22 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:22 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:22 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:22 DEBUG  WindowsBackend: windows_language=English
09-19 10:22 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:22 DEBUG  WindowsBackend: bootloader=vista
09-19 10:22 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29226.7070313 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(C: hd 29226.7070313 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2421875 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(E: hd 19357.9257813 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
09-19 10:22 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
09-19 10:22 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
09-19 10:22 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 10:22 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:22 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:22 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:22 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 10:22 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 10:22 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:22 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:22 DEBUG  CommonBackend: Searching for local CDs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:22 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
09-19 10:22 INFO   root: Running the uninstaller...
09-19 10:22 INFO   CommonBackend: This is the uninstaller running
09-19 10:22 DEBUG  WindowsFrontend: __init__...
09-19 10:22 DEBUG  WindowsFrontend: on_init...
09-19 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\translations, languages=['en_US', 'en']
09-19 10:22 INFO   root: Received settings
09-19 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\translations, languages=['en_US', 'en']
09-19 10:22 DEBUG  TaskList: # Running tasklist...
09-19 10:22 DEBUG  TaskList: ## Running Backup ISO...
09-19 10:22 DEBUG  TaskList: ## Finished Backup ISO
09-19 10:22 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 10:22 DEBUG  WindowsBackend: Could not find bcd id
09-19 10:22 DEBUG  WindowsBackend: undo_bootini C:
09-19 10:22 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 29226.7070313 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: undo_bootini D:
09-19 10:22 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2421875 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: undo_bootini E:
09-19 10:22 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 19357.9257813 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: undo_bootini G:
09-19 10:22 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 20389.6210938 mb free ntfs)
09-19 10:22 DEBUG  WindowsBackend: undo_bootini H:
09-19 10:22 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:22 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 10:22 DEBUG  TaskList: ## Running Remove target dir...
09-19 10:22 DEBUG  CommonBackend: Deleting E:\ubuntu
09-19 10:22 DEBUG  TaskList: ## Finished Remove target dir
09-19 10:22 DEBUG  TaskList: ## Running Remove registry key...
09-19 10:22 DEBUG  TaskList: ## Finished Remove registry key
09-19 10:22 DEBUG  TaskList: # Finished tasklist
09-19 10:22 INFO   root: Almost finished uninstalling
09-19 10:22 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2D85.tmp\translations, languages=['en_US', 'en']
09-19 10:22 INFO   root: Finished uninstallation
09-19 10:22 DEBUG  root: application.quit
09-19 10:22 DEBUG  WindowsFrontend: frontend.quit
09-19 10:22 DEBUG  WindowsFrontend: frontend.on_quit
09-19 10:22 DEBUG  root: application.on_quit
09-19 10:22 INFO   root: sys.exit
09-19 10:36 INFO   root: === wubi 10.04 rev189 ===
09-19 10:36 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 10:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="H:\\Drive D\\Download\\Ubuntu 10.04\\wubi.exe"']
09-19 10:36 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\data
09-19 10:36 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\bin\7z.exe
09-19 10:36 DEBUG  CommonBackend: Fetching basic info...
09-19 10:36 DEBUG  CommonBackend: original_exe=H:\Drive D\Download\Ubuntu 10.04\wubi.exe
09-19 10:36 DEBUG  CommonBackend: platform=win32
09-19 10:36 DEBUG  CommonBackend: osname=nt
09-19 10:36 DEBUG  CommonBackend: language=en_US
09-19 10:36 DEBUG  CommonBackend: encoding=cp936
09-19 10:36 DEBUG  WindowsBackend: arch=amd64
09-19 10:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\data\isolist.ini
09-19 10:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:36 DEBUG  WindowsBackend: Fetching host info...
09-19 10:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:36 DEBUG  WindowsBackend: windows version=vista
09-19 10:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:36 DEBUG  WindowsBackend: windows_sp=None
09-19 10:36 DEBUG  WindowsBackend: windows_build=7600
09-19 10:36 DEBUG  WindowsBackend: gmt=6
09-19 10:36 DEBUG  WindowsBackend: country=US
09-19 10:36 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:36 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:36 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:36 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:36 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:36 DEBUG  WindowsBackend: windows_language=English
09-19 10:36 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:36 DEBUG  WindowsBackend: bootloader=vista
09-19 10:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 29216.2070313 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(C: hd 29216.2070313 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.234375 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(G: hd 19700.9609375 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(H: hd 68070.2109375 mb free ntfs)
09-19 10:36 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 10:36 DEBUG  WindowsBackend: uninstaller_path=G:\linuxmint\uninstall-wubi.exe
09-19 10:36 DEBUG  WindowsBackend: previous_target_dir=G:\linuxmint
09-19 10:36 DEBUG  WindowsBackend: previous_distro_name=Linux Mint
09-19 10:36 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:36 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:36 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:36 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 10:36 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 10:36 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:36 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:36 DEBUG  CommonBackend: Searching for local CDs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl7FC9.tmp\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro:   parsing info from str=Linux Mint 9 "Isadora" - Release i386 (20100427.1)

09-19 10:36 DEBUG  Distro:   parsed info={'name': 'Linux Mint', 'subversion': 'Release', 'version': '9', 'build': '20100427.1', 'codename': 'Isadora', 'arch': 'i386'}
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu Netbook CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Ubuntu Netbook
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Kubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu Netbook CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Kubuntu Netbook
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Xubuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
09-19 10:36 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
09-19 10:36 DEBUG  Distro: wrong name: Linux Mint != Mythbuntu
09-19 10:36 INFO   root: Already installed, running the uninstaller...
09-19 10:36 INFO   root: Running the uninstaller...
09-19 10:36 INFO   CommonBackend: Launching previous uninestaller G:\linuxmint\uninstall-wubi.exe
09-19 10:36 DEBUG  root: application.quit
09-19 10:36 DEBUG  root: application.on_quit
09-19 10:36 INFO   root: sys.exit
09-19 10:36 INFO   root: Quitting application
09-19 10:40 INFO   root: === wubi 10.04 rev189 ===
09-19 10:40 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 10:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 10:40 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\data
09-19 10:40 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\bin\7z.exe
09-19 10:40 DEBUG  CommonBackend: Fetching basic info...
09-19 10:40 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 10:40 DEBUG  CommonBackend: platform=win32
09-19 10:40 DEBUG  CommonBackend: osname=nt
09-19 10:40 DEBUG  CommonBackend: language=en_US
09-19 10:40 DEBUG  CommonBackend: encoding=cp936
09-19 10:40 DEBUG  WindowsBackend: arch=amd64
09-19 10:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\data\isolist.ini
09-19 10:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:40 DEBUG  WindowsBackend: Fetching host info...
09-19 10:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:40 DEBUG  WindowsBackend: windows version=vista
09-19 10:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:40 DEBUG  WindowsBackend: windows_sp=None
09-19 10:40 DEBUG  WindowsBackend: windows_build=7600
09-19 10:40 DEBUG  WindowsBackend: gmt=6
09-19 10:40 DEBUG  WindowsBackend: country=US
09-19 10:40 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:40 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:40 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:40 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:40 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:40 DEBUG  WindowsBackend: windows_language=English
09-19 10:40 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:40 DEBUG  WindowsBackend: bootloader=vista
09-19 10:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28388.5976563 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(C: hd 28388.5976563 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2304688 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 10:40 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 10:40 DEBUG  WindowsBackend: uninstaller_path=None
09-19 10:40 DEBUG  WindowsBackend: previous_target_dir=None
09-19 10:40 DEBUG  WindowsBackend: previous_distro_name=None
09-19 10:40 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:40 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:40 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:40 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 10:40 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 10:40 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:40 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:40 DEBUG  CommonBackend: Searching for local CDs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:40 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:40 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:40 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:40 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 10:40 INFO   root: Running the CD menu...
09-19 10:40 DEBUG  WindowsFrontend: __init__...
09-19 10:40 DEBUG  WindowsFrontend: on_init...
09-19 10:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\translations, languages=['en_US', 'en']
09-19 10:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\translations, languages=['en_US', 'en']
09-19 10:40 INFO   root: CD menu finished
09-19 10:40 INFO   root: Running the installer...
09-19 10:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\translations, languages=['en_US', 'en']
09-19 10:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\translations, languages=['en_US', 'en']
09-19 10:40 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 10:40 INFO   root: Received settings
09-19 10:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\translations, languages=['en_US', 'en']
09-19 10:40 DEBUG  TaskList: # Running tasklist...
09-19 10:40 DEBUG  TaskList: ## Running select_target_dir...
09-19 10:40 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 10:40 DEBUG  TaskList: ## Finished select_target_dir
09-19 10:40 DEBUG  TaskList: ## Running create_dir_structure...
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 10:40 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 10:40 DEBUG  TaskList: ## Finished create_dir_structure
09-19 10:40 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 10:40 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 10:40 DEBUG  TaskList: ## Running create_uninstaller...
09-19 10:40 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 10:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 10:40 DEBUG  TaskList: ## Finished create_uninstaller
09-19 10:40 DEBUG  TaskList: ## Running copy_installation_files...
09-19 10:40 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 10:40 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\winboot -> G:\ubuntu\winboot
09-19 10:40 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylC7D1.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 10:40 DEBUG  TaskList: ## Finished copy_installation_files
09-19 10:40 DEBUG  TaskList: ## Running get_iso...
09-19 10:40 DEBUG  TaskList: New task copy_file
09-19 10:40 DEBUG  TaskList: ### Running copy_file...
09-19 10:41 DEBUG  TaskList: ### Finished copy_file
09-19 10:41 DEBUG  TaskList: New task check_iso
09-19 10:41 DEBUG  TaskList: ### Running check_iso...
09-19 10:41 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 10:41 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 10:41 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 10:41 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:41 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 10:41 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 10:41 DEBUG  TaskList: New task get_metalink
09-19 10:41 DEBUG  TaskList: #### Running get_metalink...
09-19 10:41 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:41 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-19 10:41 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink, basename=lucid-desktop-i386.metalink, length=1007, text=None
09-19 10:42 DEBUG  downloader: download finished (read 1007 bytes)
09-19 10:42 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > G:\ubuntu\install
09-19 10:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=131, text=None
09-19 10:42 DEBUG  downloader: download finished (read 131 bytes)
09-19 10:42 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > G:\ubuntu\install
09-19 10:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
09-19 10:42 DEBUG  downloader: download finished (read 189 bytes)
09-19 10:42 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-19 10:42 INFO   saplog: Checking block bindings..
09-19 10:42 INFO   saplog: Key verified successfully.
09-19 10:42 DEBUG  CommonBackend: metalink md5sums:
4b88f9df6e8ca890e6887186a5755930  maverick-desktop-amd64.metalink
a1dda02202aa3e908de372385d0f7607  maverick-desktop-i386.metalink

09-19 10:42 ERROR  CommonBackend: The md5 of the metalink does match
09-19 10:42 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
09-19 10:42 DEBUG  TaskList: #### Finished get_metalink
09-19 10:42 DEBUG  TaskList: New task get_file_md5
09-19 10:42 DEBUG  TaskList: #### Running get_file_md5...
09-19 10:42 DEBUG  TaskList: #### Finished get_file_md5
09-19 10:42 ERROR  CommonBackend: Invalid md5 for ISO G:\ubuntu\install\installation.iso (9a95ed6f6ec38fb58c446dba1add6a08 != d044a2a0c8103fc3e5b7e18b0f7de1c8)
None
09-19 10:42 DEBUG  TaskList: ### Finished check_iso
09-19 10:42 DEBUG  CommonBackend: Searching for local ISO
09-19 10:42 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-19 10:42 DEBUG  TaskList: New task download
09-19 10:42 DEBUG  TaskList: ### Running download...
09-19 10:42 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 10:42 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
09-19 10:42 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
09-19 10:42 DEBUG  TaskList: ### Finished download
09-19 10:42 DEBUG  TaskList: New task download
09-19 10:42 DEBUG  TaskList: ### Running download...
09-19 10:42 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 10:42 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso, basename=lucid-desktop-i386.iso, length=718864384, text=None
09-19 10:44 INFO   WindowsFrontend: Operation cancelled
09-19 10:44 INFO   WindowsFrontend: Cancelled cancellation, resuming
09-19 10:45 INFO   WindowsFrontend: Operation cancelled
09-19 10:45 DEBUG  WindowsFrontend: frontend.quit
09-19 10:45 DEBUG  WindowsFrontend: frontend.on_quit
09-19 10:45 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-19 10:45 DEBUG  TaskList: # Cancelling tasklist
09-19 10:45 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-19 10:45 DEBUG  root: application.on_quit
09-19 10:45 DEBUG  root: Forceful exit
09-19 10:45 INFO   root: sys.exit
09-19 10:45 INFO   root: === wubi 10.04 rev189 ===
09-19 10:45 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 10:45 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 10:45 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\data
09-19 10:45 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\bin\7z.exe
09-19 10:45 DEBUG  CommonBackend: Fetching basic info...
09-19 10:45 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 10:45 DEBUG  CommonBackend: platform=win32
09-19 10:45 DEBUG  CommonBackend: osname=nt
09-19 10:45 DEBUG  CommonBackend: language=en_US
09-19 10:45 DEBUG  CommonBackend: encoding=cp936
09-19 10:45 DEBUG  WindowsBackend: arch=amd64
09-19 10:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\data\isolist.ini
09-19 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:45 DEBUG  WindowsBackend: Fetching host info...
09-19 10:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:45 DEBUG  WindowsBackend: windows version=vista
09-19 10:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:45 DEBUG  WindowsBackend: windows_sp=None
09-19 10:45 DEBUG  WindowsBackend: windows_build=7600
09-19 10:45 DEBUG  WindowsBackend: gmt=6
09-19 10:45 DEBUG  WindowsBackend: country=US
09-19 10:45 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:45 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:45 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:45 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:45 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:45 DEBUG  WindowsBackend: windows_language=English
09-19 10:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:45 DEBUG  WindowsBackend: bootloader=vista
09-19 10:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28322.3242188 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(C: hd 28322.3242188 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2304688 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(G: hd 19687.1289063 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 10:45 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 10:45 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 10:45 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 10:45 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:45 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:45 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:45 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 10:45 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 10:45 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:45 DEBUG  CommonBackend: Searching for local CDs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:45 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:45 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 10:45 INFO   root: Running the CD menu...
09-19 10:45 DEBUG  WindowsFrontend: __init__...
09-19 10:45 DEBUG  WindowsFrontend: on_init...
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 INFO   root: CD menu finished
09-19 10:45 INFO   root: Already installed, running the uninstaller...
09-19 10:45 INFO   root: Running the uninstaller...
09-19 10:45 INFO   CommonBackend: This is the uninstaller running
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 INFO   root: Received settings
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 DEBUG  TaskList: # Running tasklist...
09-19 10:45 DEBUG  TaskList: ## Running Backup ISO...
09-19 10:45 DEBUG  TaskList: ## Finished Backup ISO
09-19 10:45 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 10:45 DEBUG  WindowsBackend: Could not find bcd id
09-19 10:45 DEBUG  WindowsBackend: undo_bootini C:
09-19 10:45 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28322.3242188 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: undo_bootini D:
09-19 10:45 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2304688 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: undo_bootini E:
09-19 10:45 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: undo_bootini G:
09-19 10:45 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19687.1289063 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: undo_bootini H:
09-19 10:45 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68771.0585938 mb free ntfs)
09-19 10:45 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 10:45 DEBUG  TaskList: ## Running Remove target dir...
09-19 10:45 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 10:45 DEBUG  TaskList: ## Finished Remove target dir
09-19 10:45 DEBUG  TaskList: ## Running Remove registry key...
09-19 10:45 DEBUG  TaskList: ## Finished Remove registry key
09-19 10:45 DEBUG  TaskList: # Finished tasklist
09-19 10:45 INFO   root: Almost finished uninstalling
09-19 10:45 INFO   root: Finished uninstallation
09-19 10:45 DEBUG  CommonBackend: Fetching basic info...
09-19 10:45 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 10:45 DEBUG  CommonBackend: platform=win32
09-19 10:45 DEBUG  CommonBackend: osname=nt
09-19 10:45 DEBUG  WindowsBackend: arch=amd64
09-19 10:45 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\data\isolist.ini
09-19 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 10:45 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 10:45 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 10:45 DEBUG  WindowsBackend: Fetching host info...
09-19 10:45 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 10:45 DEBUG  WindowsBackend: windows version=vista
09-19 10:45 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 10:45 DEBUG  WindowsBackend: windows_sp=None
09-19 10:45 DEBUG  WindowsBackend: windows_build=7600
09-19 10:45 DEBUG  WindowsBackend: gmt=6
09-19 10:45 DEBUG  WindowsBackend: country=US
09-19 10:45 DEBUG  WindowsBackend: timezone=America/New_York
09-19 10:45 DEBUG  WindowsBackend: windows_username=TU TU
09-19 10:45 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 10:45 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 10:45 DEBUG  WindowsBackend: windows_language_code=1033
09-19 10:45 DEBUG  WindowsBackend: windows_language=English
09-19 10:45 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 10:45 DEBUG  WindowsBackend: bootloader=vista
09-19 10:45 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28322.84375 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(C: hd 28322.84375 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2304688 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 10:45 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 10:45 DEBUG  WindowsBackend: uninstaller_path=None
09-19 10:45 DEBUG  WindowsBackend: previous_target_dir=None
09-19 10:45 DEBUG  WindowsBackend: previous_distro_name=None
09-19 10:45 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 10:45 DEBUG  WindowsBackend: keyboard_layout=us
09-19 10:45 DEBUG  WindowsBackend: keyboard_variant=
09-19 10:45 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 10:45 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 10:45 DEBUG  CommonBackend: Searching for local CDs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 10:45 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 10:45 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 10:45 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 10:45 INFO   root: Running the installer...
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 10:45 INFO   root: Received settings
09-19 10:45 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\translations, languages=['en_US', 'en']
09-19 10:45 DEBUG  TaskList: # Running tasklist...
09-19 10:45 DEBUG  TaskList: ## Running select_target_dir...
09-19 10:45 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 10:45 DEBUG  TaskList: ## Finished select_target_dir
09-19 10:45 DEBUG  TaskList: ## Running create_dir_structure...
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 10:45 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 10:45 DEBUG  TaskList: ## Finished create_dir_structure
09-19 10:45 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 10:45 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 10:45 DEBUG  TaskList: ## Running create_uninstaller...
09-19 10:45 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 10:45 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 10:45 DEBUG  TaskList: ## Finished create_uninstaller
09-19 10:45 DEBUG  TaskList: ## Running copy_installation_files...
09-19 10:45 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 10:45 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\winboot -> G:\ubuntu\winboot
09-19 10:45 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl2E21.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 10:45 DEBUG  TaskList: ## Finished copy_installation_files
09-19 10:45 DEBUG  TaskList: ## Running get_iso...
09-19 10:45 DEBUG  TaskList: New task copy_file
09-19 10:45 DEBUG  TaskList: ### Running copy_file...
09-19 10:46 DEBUG  TaskList: ### Finished copy_file
09-19 10:46 DEBUG  TaskList: New task check_iso
09-19 10:46 DEBUG  TaskList: ### Running check_iso...
09-19 10:46 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 10:46 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 10:46 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 10:46 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 10:46 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 10:46 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 10:46 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 10:46 DEBUG  TaskList: New task get_metalink
09-19 10:46 DEBUG  TaskList: #### Running get_metalink...
09-19 10:46 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:46 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:46 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 10:46 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 10:46 DEBUG  TaskList: #### Finished get_metalink
09-19 10:46 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 10:46 DEBUG  TaskList: ### Finished check_iso
09-19 10:46 DEBUG  TaskList: ## Finished get_iso
09-19 10:46 DEBUG  TaskList: ## Running extract_kernel...
09-19 10:46 DEBUG  CommonBackend: Copying files from CD J:\
09-19 10:47 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 10:47 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 10:47 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 10:47 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 10:47 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 10:47 DEBUG  TaskList: ## Finished extract_kernel
09-19 10:47 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 10:47 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 10:47 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 10:47 DEBUG  TaskList: ## Running create_preseed...
09-19 10:47 DEBUG  TaskList: ## Finished create_preseed
09-19 10:47 DEBUG  TaskList: ## Running modify_bootloader...
09-19 10:47 DEBUG  TaskList: New task modify_bcd
09-19 10:47 DEBUG  TaskList: ### Running modify_bcd...
09-19 10:47 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28322.84375 mb free ntfs)
09-19 10:47 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fd-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fd-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:47 DEBUG  TaskList: # Cancelling tasklist
09-19 10:47 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fd-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fd-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 10:47 DEBUG  TaskList: New task modify_bcd
09-19 10:47 DEBUG  TaskList: New task modify_bcd
09-19 10:47 DEBUG  TaskList: New task modify_bcd
09-19 10:47 DEBUG  TaskList: New task modify_bcd
09-19 10:47 DEBUG  TaskList: ## Finished modify_bootloader
09-19 10:47 DEBUG  TaskList: # Finished tasklist
09-19 11:55 INFO   root: === wubi 10.04 rev189 ===
09-19 11:55 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 11:55 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\ubuntu\\uninstall-wubi.exe"']
09-19 11:55 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\data
09-19 11:55 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\bin\7z.exe
09-19 11:55 DEBUG  CommonBackend: Fetching basic info...
09-19 11:55 DEBUG  CommonBackend: original_exe=G:\ubuntu\uninstall-wubi.exe
09-19 11:55 DEBUG  CommonBackend: platform=win32
09-19 11:55 DEBUG  CommonBackend: osname=nt
09-19 11:55 DEBUG  CommonBackend: language=en_US
09-19 11:55 DEBUG  CommonBackend: encoding=cp936
09-19 11:55 DEBUG  WindowsBackend: arch=amd64
09-19 11:55 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\data\isolist.ini
09-19 11:55 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 11:55 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 11:55 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 11:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 11:55 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 11:55 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 11:55 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 11:55 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 11:55 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 11:55 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 11:55 DEBUG  WindowsBackend: Fetching host info...
09-19 11:55 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 11:55 DEBUG  WindowsBackend: windows version=vista
09-19 11:55 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 11:55 DEBUG  WindowsBackend: windows_sp=None
09-19 11:55 DEBUG  WindowsBackend: windows_build=7600
09-19 11:55 DEBUG  WindowsBackend: gmt=6
09-19 11:55 DEBUG  WindowsBackend: country=US
09-19 11:55 DEBUG  WindowsBackend: timezone=America/New_York
09-19 11:55 DEBUG  WindowsBackend: windows_username=TU TU
09-19 11:55 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 11:55 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 11:55 DEBUG  WindowsBackend: windows_language_code=1033
09-19 11:55 DEBUG  WindowsBackend: windows_language=English
09-19 11:55 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 11:55 DEBUG  WindowsBackend: bootloader=vista
09-19 11:55 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28340.6289063 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(C: hd 28340.6289063 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2304688 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.6757813 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(G: hd 19675.8710938 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 11:55 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 11:55 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 11:55 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 11:55 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 11:55 DEBUG  WindowsBackend: keyboard_layout=us
09-19 11:55 DEBUG  WindowsBackend: keyboard_variant=
09-19 11:55 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 11:55 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 11:55 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 11:55 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 11:55 DEBUG  CommonBackend: Searching for local CDs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 11:55 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 11:55 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 11:55 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 11:55 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 11:55 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 11:55 INFO   root: Running the uninstaller...
09-19 11:55 INFO   CommonBackend: This is the uninstaller running
09-19 11:55 DEBUG  WindowsFrontend: __init__...
09-19 11:55 DEBUG  WindowsFrontend: on_init...
09-19 11:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\translations, languages=['en_US', 'en']
09-19 11:55 INFO   root: Received settings
09-19 11:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\translations, languages=['en_US', 'en']
09-19 11:55 DEBUG  TaskList: # Running tasklist...
09-19 11:55 DEBUG  TaskList: ## Running Backup ISO...
09-19 11:55 DEBUG  TaskList: ## Finished Backup ISO
09-19 11:55 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 11:55 DEBUG  WindowsBackend: Could not find bcd id
09-19 11:55 DEBUG  WindowsBackend: undo_bootini C:
09-19 11:55 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28340.6289063 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: undo_bootini D:
09-19 11:55 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2304688 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: undo_bootini E:
09-19 11:55 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20071.6757813 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: undo_bootini G:
09-19 11:55 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19675.8710938 mb free ntfs)
09-19 11:55 DEBUG  WindowsBackend: undo_bootini H:
09-19 11:55 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68771.0585938 mb free ntfs)
09-19 11:55 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 11:55 DEBUG  TaskList: ## Running Remove target dir...
09-19 11:55 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 11:55 DEBUG  TaskList: ## Finished Remove target dir
09-19 11:55 DEBUG  TaskList: ## Running Remove registry key...
09-19 11:55 DEBUG  TaskList: ## Finished Remove registry key
09-19 11:55 DEBUG  TaskList: # Finished tasklist
09-19 11:55 INFO   root: Almost finished uninstalling
09-19 11:55 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylBD38.tmp\translations, languages=['en_US', 'en']
09-19 11:56 INFO   root: Finished uninstallation
09-19 11:56 DEBUG  root: application.quit
09-19 11:56 DEBUG  WindowsFrontend: frontend.quit
09-19 11:56 DEBUG  WindowsFrontend: frontend.on_quit
09-19 11:56 DEBUG  root: application.on_quit
09-19 11:56 INFO   root: sys.exit
09-19 12:24 INFO   root: === wubi 10.04 rev189 ===
09-19 12:24 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 12:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="J:\\wubi.exe"', '--cdmenu']
09-19 12:24 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\data
09-19 12:24 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\bin\7z.exe
09-19 12:24 DEBUG  CommonBackend: Fetching basic info...
09-19 12:24 DEBUG  CommonBackend: original_exe=J:\wubi.exe
09-19 12:24 DEBUG  CommonBackend: platform=win32
09-19 12:24 DEBUG  CommonBackend: osname=nt
09-19 12:24 DEBUG  CommonBackend: language=en_US
09-19 12:24 DEBUG  CommonBackend: encoding=cp936
09-19 12:24 DEBUG  WindowsBackend: arch=amd64
09-19 12:24 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\data\isolist.ini
09-19 12:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 12:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 12:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 12:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 12:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 12:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 12:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 12:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 12:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 12:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 12:24 DEBUG  WindowsBackend: Fetching host info...
09-19 12:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 12:24 DEBUG  WindowsBackend: windows version=vista
09-19 12:24 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 12:24 DEBUG  WindowsBackend: windows_sp=None
09-19 12:24 DEBUG  WindowsBackend: windows_build=7600
09-19 12:24 DEBUG  WindowsBackend: gmt=6
09-19 12:24 DEBUG  WindowsBackend: country=US
09-19 12:24 DEBUG  WindowsBackend: timezone=America/New_York
09-19 12:24 DEBUG  WindowsBackend: windows_username=TU TU
09-19 12:24 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 12:24 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 12:24 DEBUG  WindowsBackend: windows_language_code=1033
09-19 12:24 DEBUG  WindowsBackend: windows_language=English
09-19 12:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 12:24 DEBUG  WindowsBackend: bootloader=vista
09-19 12:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28326.9414063 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(C: hd 28326.9414063 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2070313 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(E: hd 20071.0 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 12:24 DEBUG  WindowsBackend: drive=Drive(K: hd 71.22265625 mb free ntfs)
09-19 12:24 DEBUG  WindowsBackend: uninstaller_path=None
09-19 12:24 DEBUG  WindowsBackend: previous_target_dir=None
09-19 12:24 DEBUG  WindowsBackend: previous_distro_name=None
09-19 12:24 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 12:24 DEBUG  WindowsBackend: keyboard_layout=us
09-19 12:24 DEBUG  WindowsBackend: keyboard_variant=
09-19 12:24 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 12:24 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 12:24 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 12:24 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 12:24 DEBUG  CommonBackend: Searching for local CDs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:24 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:24 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 12:24 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 12:24 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 12:24 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 12:24 INFO   root: Running the CD menu...
09-19 12:24 DEBUG  WindowsFrontend: __init__...
09-19 12:24 DEBUG  WindowsFrontend: on_init...
09-19 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\translations, languages=['en_US', 'en']
09-19 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\translations, languages=['en_US', 'en']
09-19 12:24 INFO   root: CD menu finished
09-19 12:24 INFO   root: Running the installer...
09-19 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\translations, languages=['en_US', 'en']
09-19 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\translations, languages=['en_US', 'en']
09-19 12:24 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 12:24 INFO   root: Received settings
09-19 12:24 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\translations, languages=['en_US', 'en']
09-19 12:24 DEBUG  TaskList: # Running tasklist...
09-19 12:24 DEBUG  TaskList: ## Running select_target_dir...
09-19 12:24 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 12:24 DEBUG  TaskList: ## Finished select_target_dir
09-19 12:24 DEBUG  TaskList: ## Running create_dir_structure...
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 12:24 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 12:24 DEBUG  TaskList: ## Finished create_dir_structure
09-19 12:24 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 12:24 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 12:24 DEBUG  TaskList: ## Running create_uninstaller...
09-19 12:24 DEBUG  WindowsBackend: Copying uninstaller J:\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 12:24 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 12:24 DEBUG  TaskList: ## Finished create_uninstaller
09-19 12:24 DEBUG  TaskList: ## Running copy_installation_files...
09-19 12:24 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 12:24 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\winboot -> G:\ubuntu\winboot
09-19 12:24 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pyl1083.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 12:24 DEBUG  TaskList: ## Finished copy_installation_files
09-19 12:24 DEBUG  TaskList: ## Running get_iso...
09-19 12:24 DEBUG  TaskList: New task copy_file
09-19 12:24 DEBUG  TaskList: ### Running copy_file...
09-19 12:25 DEBUG  TaskList: ### Finished copy_file
09-19 12:25 DEBUG  TaskList: New task check_iso
09-19 12:25 DEBUG  TaskList: ### Running check_iso...
09-19 12:25 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 12:25 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 12:25 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 12:25 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 12:25 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 12:25 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 12:25 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 12:25 DEBUG  TaskList: New task get_metalink
09-19 12:25 DEBUG  TaskList: #### Running get_metalink...
09-19 12:25 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 12:25 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 14] HTTP Error 404: Not Found
09-19 12:25 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 12:25 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.metalink, url=http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink, basename=lucid-desktop-i386.metalink, length=1007, text=None
09-19 12:25 DEBUG  downloader: download finished (read 1007 bytes)
09-19 12:25 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink) > G:\ubuntu\install
09-19 12:26 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=131, text=None
09-19 12:26 DEBUG  downloader: download finished (read 131 bytes)
09-19 12:26 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg) > G:\ubuntu\install
09-19 12:26 DEBUG  downloader: Download start filename=G:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/daily-live/current/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
09-19 12:26 DEBUG  downloader: download finished (read 189 bytes)
09-19 12:26 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
09-19 12:26 INFO   saplog: Checking block bindings..
09-19 12:26 INFO   saplog: Key verified successfully.
09-19 12:26 DEBUG  CommonBackend: metalink md5sums:
4b88f9df6e8ca890e6887186a5755930  maverick-desktop-amd64.metalink
a1dda02202aa3e908de372385d0f7607  maverick-desktop-i386.metalink

09-19 12:26 ERROR  CommonBackend: The md5 of the metalink does match
09-19 12:26 ERROR  CommonBackend: Cannot authenticate the metalink file, it might be corrupt
Traceback (most recent call last):
  File "\lib\wubi\backends\common\backend.py", line 367, in get_metalink
  File "\lib\wubi\backends\common\downloader.py", line 79, in download
  File "\lib\urlgrabber\grabber.py", line 927, in urlgrab
  File "\lib\urlgrabber\grabber.py", line 845, in _retry
  File "\lib\urlgrabber\grabber.py", line 913, in retryfunc
  File "\lib\urlgrabber\grabber.py", line 1001, in __init__
  File "\lib\urlgrabber\grabber.py", line 1072, in _do_open
  File "\lib\urlgrabber\grabber.py", line 1182, in _make_request
URLGrabError: [Errno 14] HTTP Error 404: Not Found
09-19 12:26 DEBUG  TaskList: #### Finished get_metalink
09-19 12:26 DEBUG  TaskList: New task get_file_md5
09-19 12:26 DEBUG  TaskList: #### Running get_file_md5...
09-19 12:26 DEBUG  TaskList: #### Finished get_file_md5
09-19 12:26 ERROR  CommonBackend: Invalid md5 for ISO G:\ubuntu\install\installation.iso (9a95ed6f6ec38fb58c446dba1add6a08 != d044a2a0c8103fc3e5b7e18b0f7de1c8)
None
09-19 12:26 DEBUG  TaskList: ### Finished check_iso
09-19 12:26 DEBUG  CommonBackend: Searching for local ISO
09-19 12:26 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
09-19 12:26 DEBUG  TaskList: New task download
09-19 12:26 DEBUG  TaskList: ### Running download...
09-19 12:26 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso.torrent) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 12:26 ERROR  TaskList: problem getting response info - HTTP Error 404: Not Found
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 129, in download
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: problem getting response info - HTTP Error 404: Not Found
09-19 12:26 ERROR  TaskList: Non fatal error problem getting response info - HTTP Error 404: Not Found in task download
09-19 12:26 DEBUG  TaskList: ### Finished download
09-19 12:26 DEBUG  TaskList: New task download
09-19 12:26 DEBUG  TaskList: ### Running download...
09-19 12:26 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso) > G:\ubuntu\install\lucid-desktop-i386.iso
09-19 12:26 DEBUG  downloader: Download start filename=G:\ubuntu\install\lucid-desktop-i386.iso, url=http://cdimage.ubuntu.com/lucid/daily-live/20100816.1/lucid-desktop-i386.iso, basename=lucid-desktop-i386.iso, length=718864384, text=None
09-19 12:29 INFO   WindowsFrontend: Operation cancelled
09-19 12:29 DEBUG  WindowsFrontend: frontend.quit
09-19 12:29 DEBUG  WindowsFrontend: frontend.on_quit
09-19 12:29 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
09-19 12:29 DEBUG  TaskList: # Cancelling tasklist
09-19 12:29 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
09-19 12:29 DEBUG  root: application.on_quit
09-19 12:29 DEBUG  root: Forceful exit
09-19 12:29 INFO   root: sys.exit
09-19 12:30 INFO   root: === wubi 10.04 rev189 ===
09-19 12:30 DEBUG  root: Logfile is c:\users\tutu~1\appdata\local\temp\wubi-10.04-rev189.log
09-19 12:30 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\TU TU\\Desktop\\Ubuntu 10.04\\wubi.exe"']
09-19 12:30 DEBUG  CommonBackend: data_dir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\data
09-19 12:30 DEBUG  WindowsBackend: 7z=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\bin\7z.exe
09-19 12:30 DEBUG  CommonBackend: Fetching basic info...
09-19 12:30 DEBUG  CommonBackend: original_exe=C:\Users\TU TU\Desktop\Ubuntu 10.04\wubi.exe
09-19 12:30 DEBUG  CommonBackend: platform=win32
09-19 12:30 DEBUG  CommonBackend: osname=nt
09-19 12:30 DEBUG  CommonBackend: language=en_US
09-19 12:30 DEBUG  CommonBackend: encoding=cp936
09-19 12:30 DEBUG  WindowsBackend: arch=amd64
09-19 12:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\data\isolist.ini
09-19 12:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 12:30 DEBUG  WindowsBackend: Fetching host info...
09-19 12:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 12:30 DEBUG  WindowsBackend: windows version=vista
09-19 12:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 12:30 DEBUG  WindowsBackend: windows_sp=None
09-19 12:30 DEBUG  WindowsBackend: windows_build=7600
09-19 12:30 DEBUG  WindowsBackend: gmt=6
09-19 12:30 DEBUG  WindowsBackend: country=US
09-19 12:30 DEBUG  WindowsBackend: timezone=America/New_York
09-19 12:30 DEBUG  WindowsBackend: windows_username=TU TU
09-19 12:30 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 12:30 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 12:30 DEBUG  WindowsBackend: windows_language_code=1033
09-19 12:30 DEBUG  WindowsBackend: windows_language=English
09-19 12:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 12:30 DEBUG  WindowsBackend: bootloader=vista
09-19 12:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28325.3632813 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(C: hd 28325.3632813 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2070313 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(E: hd 20070.8085938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(G: hd 19688.0273438 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(K: hd 71.22265625 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: uninstaller_path=G:\ubuntu\uninstall-wubi.exe
09-19 12:30 DEBUG  WindowsBackend: previous_target_dir=G:\ubuntu
09-19 12:30 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
09-19 12:30 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 12:30 DEBUG  WindowsBackend: keyboard_layout=us
09-19 12:30 DEBUG  WindowsBackend: keyboard_variant=
09-19 12:30 DEBUG  CommonBackend: python locale=('en_US', 'cp936')
09-19 12:30 DEBUG  CommonBackend: locale=en_US.UTF-8
09-19 12:30 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 12:30 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 12:30 DEBUG  CommonBackend: Searching for local CDs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 12:30 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 12:30 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 12:30 INFO   root: Running the CD menu...
09-19 12:30 DEBUG  WindowsFrontend: __init__...
09-19 12:30 DEBUG  WindowsFrontend: on_init...
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 INFO   root: CD menu finished
09-19 12:30 INFO   root: Already installed, running the uninstaller...
09-19 12:30 INFO   root: Running the uninstaller...
09-19 12:30 INFO   CommonBackend: This is the uninstaller running
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 INFO   root: Received settings
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 DEBUG  TaskList: # Running tasklist...
09-19 12:30 DEBUG  TaskList: ## Running Backup ISO...
09-19 12:30 DEBUG  TaskList: ## Finished Backup ISO
09-19 12:30 DEBUG  TaskList: ## Running Remove bootloader entry...
09-19 12:30 DEBUG  WindowsBackend: Could not find bcd id
09-19 12:30 DEBUG  WindowsBackend: undo_bootini C:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 28325.3632813 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini D:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 32010.2070313 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini E:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 20070.8085938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini G:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 19688.0273438 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini H:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 68771.0585938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini I:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 7325.859375 mb free fat32)
09-19 12:30 DEBUG  WindowsBackend: undo_bootini K:
09-19 12:30 DEBUG  WindowsBackend: undo_configsys Drive(K: hd 71.22265625 mb free ntfs)
09-19 12:30 DEBUG  TaskList: ## Finished Remove bootloader entry
09-19 12:30 DEBUG  TaskList: ## Running Remove target dir...
09-19 12:30 DEBUG  CommonBackend: Deleting G:\ubuntu
09-19 12:30 DEBUG  TaskList: ## Finished Remove target dir
09-19 12:30 DEBUG  TaskList: ## Running Remove registry key...
09-19 12:30 DEBUG  TaskList: ## Finished Remove registry key
09-19 12:30 DEBUG  TaskList: # Finished tasklist
09-19 12:30 INFO   root: Almost finished uninstalling
09-19 12:30 INFO   root: Finished uninstallation
09-19 12:30 DEBUG  CommonBackend: Fetching basic info...
09-19 12:30 DEBUG  CommonBackend: original_exe=C:\Users\TU TU\Desktop\Ubuntu 10.04\wubi.exe
09-19 12:30 DEBUG  CommonBackend: platform=win32
09-19 12:30 DEBUG  CommonBackend: osname=nt
09-19 12:30 DEBUG  WindowsBackend: arch=amd64
09-19 12:30 DEBUG  CommonBackend: Parsing isolist=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\data\isolist.ini
09-19 12:30 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
09-19 12:30 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
09-19 12:30 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
09-19 12:30 DEBUG  WindowsBackend: Fetching host info...
09-19 12:30 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
09-19 12:30 DEBUG  WindowsBackend: windows version=vista
09-19 12:30 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
09-19 12:30 DEBUG  WindowsBackend: windows_sp=None
09-19 12:30 DEBUG  WindowsBackend: windows_build=7600
09-19 12:30 DEBUG  WindowsBackend: gmt=6
09-19 12:30 DEBUG  WindowsBackend: country=US
09-19 12:30 DEBUG  WindowsBackend: timezone=America/New_York
09-19 12:30 DEBUG  WindowsBackend: windows_username=TU TU
09-19 12:30 DEBUG  WindowsBackend: user_full_name=TU TU
09-19 12:30 DEBUG  WindowsBackend: user_directory=C:\Users\TU TU
09-19 12:30 DEBUG  WindowsBackend: windows_language_code=1033
09-19 12:30 DEBUG  WindowsBackend: windows_language=English
09-19 12:30 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
09-19 12:30 DEBUG  WindowsBackend: bootloader=vista
09-19 12:30 DEBUG  WindowsBackend: system_drive=Drive(C: hd 28325.8398438 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(C: hd 28325.8398438 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(D: hd 32010.2070313 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(E: hd 20070.8085938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(G: hd 20389.6210938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(H: hd 68771.0585938 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(I: removable 7325.859375 mb free fat32)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free cdfs)
09-19 12:30 DEBUG  WindowsBackend: drive=Drive(K: hd 71.22265625 mb free ntfs)
09-19 12:30 DEBUG  WindowsBackend: uninstaller_path=None
09-19 12:30 DEBUG  WindowsBackend: previous_target_dir=None
09-19 12:30 DEBUG  WindowsBackend: previous_distro_name=None
09-19 12:30 DEBUG  WindowsBackend: keyboard_id=67699721
09-19 12:30 DEBUG  WindowsBackend: keyboard_layout=us
09-19 12:30 DEBUG  WindowsBackend: keyboard_variant=
09-19 12:30 DEBUG  WindowsBackend: total_memory_mb=2038.4296875
09-19 12:30 DEBUG  CommonBackend: Searching ISOs on USB devices
09-19 12:30 DEBUG  CommonBackend: Searching for local CDs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu Netbook CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
09-19 12:30 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
09-19 12:30 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
09-19 12:30 INFO   Distro: Found a valid CD for Ubuntu: J:\
09-19 12:30 INFO   root: Running the installer...
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 DEBUG  WinuiInstallationPage: target_drive=G:, installation_size=19000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=tutu
09-19 12:30 INFO   root: Received settings
09-19 12:30 INFO   WinuiPage: appname=wubi, localedir=C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\translations, languages=['en_US', 'en']
09-19 12:30 DEBUG  TaskList: # Running tasklist...
09-19 12:30 DEBUG  TaskList: ## Running select_target_dir...
09-19 12:30 INFO   WindowsBackend: Installing into G:\ubuntu
09-19 12:30 DEBUG  TaskList: ## Finished select_target_dir
09-19 12:30 DEBUG  TaskList: ## Running create_dir_structure...
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\disks\boot\grub
09-19 12:30 DEBUG  CommonBackend: Creating dir G:\ubuntu\install\boot\grub
09-19 12:30 DEBUG  TaskList: ## Finished create_dir_structure
09-19 12:30 DEBUG  TaskList: ## Running uncompress_target_dir...
09-19 12:30 DEBUG  TaskList: ## Finished uncompress_target_dir
09-19 12:30 DEBUG  TaskList: ## Running create_uninstaller...
09-19 12:30 DEBUG  WindowsBackend: Copying uninstaller C:\Users\TU TU\Desktop\Ubuntu 10.04\wubi.exe -> G:\ubuntu\uninstall-wubi.exe
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString G:\ubuntu\uninstall-wubi.exe
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir G:\ubuntu
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon G:\ubuntu\Ubuntu.ico
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
09-19 12:30 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
09-19 12:30 DEBUG  TaskList: ## Finished create_uninstaller
09-19 12:30 DEBUG  TaskList: ## Running copy_installation_files...
09-19 12:30 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\data\custom-installation -> G:\ubuntu\install\custom-installation
09-19 12:30 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\winboot -> G:\ubuntu\winboot
09-19 12:30 DEBUG  WindowsBackend: Copying C:\Users\TUTU~1\AppData\Local\Temp\pylAD10.tmp\data\images\Ubuntu.ico -> G:\ubuntu\Ubuntu.ico
09-19 12:30 DEBUG  TaskList: ## Finished copy_installation_files
09-19 12:30 DEBUG  TaskList: ## Running get_iso...
09-19 12:30 DEBUG  TaskList: New task copy_file
09-19 12:30 DEBUG  TaskList: ### Running copy_file...
09-19 12:31 DEBUG  TaskList: ### Finished copy_file
09-19 12:31 DEBUG  TaskList: New task check_iso
09-19 12:31 DEBUG  TaskList: ### Running check_iso...
09-19 12:31 DEBUG  CommonBackend: Checking G:\ubuntu\install\installation.iso
09-19 12:31 DEBUG  Distro:   checking Ubuntu ISO G:\ubuntu\install\installation.iso
09-19 12:31 DEBUG  WindowsBackend:   extracting .disk\info from G:\ubuntu\install\installation.iso
09-19 12:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
09-19 12:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
09-19 12:31 INFO   Distro: Found a valid iso for Ubuntu: G:\ubuntu\install\installation.iso
09-19 12:31 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
09-19 12:31 DEBUG  TaskList: New task get_metalink
09-19 12:31 DEBUG  TaskList: #### Running get_metalink...
09-19 12:31 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) > G:\ubuntu\install
09-19 12:31 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 12:31 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) > G:\ubuntu\install
09-19 12:31 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-i386.metalink) err=[Errno 4] IOError: <urlopen error (7, 'getaddrinfo failed')>
09-19 12:31 DEBUG  TaskList: #### Finished get_metalink
09-19 12:31 ERROR  CommonBackend: ERROR: the metalink file is not available, cannot check the md5 for G:\ubuntu\install\installation.iso, ignoring
09-19 12:31 DEBUG  TaskList: ### Finished check_iso
09-19 12:31 DEBUG  TaskList: ## Finished get_iso
09-19 12:31 DEBUG  TaskList: ## Running extract_kernel...
09-19 12:31 DEBUG  CommonBackend: Copying files from CD J:\
09-19 12:31 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
09-19 12:31 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\vmlinuz
09-19 12:31 DEBUG  CommonBackend:   G:\ubuntu\install\boot\vmlinuz md5 = 1c0d4864792ec0bb7660f303f805a2fe == 1c0d4864792ec0bb7660f303f805a2fe
09-19 12:31 DEBUG  CommonBackend:   checking G:\ubuntu\install\boot\initrd.lz
09-19 12:31 DEBUG  CommonBackend:   G:\ubuntu\install\boot\initrd.lz md5 = 3655dace1196d23a3fc82d569f93d33f == 3655dace1196d23a3fc82d569f93d33f
09-19 12:31 DEBUG  TaskList: ## Finished extract_kernel
09-19 12:31 DEBUG  TaskList: ## Running choose_disk_sizes...
09-19 12:31 DEBUG  WindowsBackend: total size=19000
  root=18744
  swap=256
  home=0
  usr=0
09-19 12:31 DEBUG  TaskList: ## Finished choose_disk_sizes
09-19 12:31 DEBUG  TaskList: ## Running create_preseed...
09-19 12:31 DEBUG  TaskList: ## Finished create_preseed
09-19 12:31 DEBUG  TaskList: ## Running modify_bootloader...
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: ### Running modify_bcd...
09-19 12:31 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 28325.8398438 mb free ntfs)
09-19 12:31 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fe-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fe-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 12:31 DEBUG  TaskList: # Cancelling tasklist
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fe-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 631, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /set {24ab71fe-c3ed-11df-b86d-c93a6949abcf} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

The request is not supported.


>>stdout=
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: New task modify_bcd
09-19 12:31 DEBUG  TaskList: ## Finished modify_bootloader
09-19 12:31 DEBUG  TaskList: # Finished tasklist
```

---

### Post by wilee-nilee on 2010-09-19
Op if you could edit that log file and put code it in code tags it would be quite helpful. Look In my signature and put the bracketed tags at the beginning and at the end. You can just hit edit and copy and paste the codes brackets from my sig in or type them in. This creates a scrolling window that is much easier to read. ;)

---

### Post by ilovelinux33467 on 2010-09-19
May I suggest the pastebin for that log?

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by LonelySEason on 2010-09-19
> **wilee-nilee said:**
> Op if you could edit that log file and put code it in code tags it would be quite helpful. Look In my signature and put the bracketed tags at the beginning and at the end. You can just hit edit and copy and paste the codes brackets from my sig in or type them in. This creates a scrolling window that is much easier to read. ;)

Yeha... thank you, I already edit it. hope u can take a look

---

### Post by LonelySEason on 2010-09-19
> **ilovelinux33467 said:**
> May I suggest the pastebin for that log?

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

thank alot, here is the link

[http://paste.ubuntu.com/496336/](http://paste.ubuntu.com/496336/)

---

### Post by wilee-nilee on 2010-09-19
> **LonelySEason said:**
> Yeha... thank you, I already edit it. hope u can take a look

Awesome that will make it easier, look for the user bcbc to stop by they are pretty knowledgeable about wubi

I'm of no help in this, I was just concerned that the text be the easiest to read for you to get help. 

I would just install it in virtualbox and try it out that way. If you like it and want to dual boot it we can help you. In virtual it will not run quite as well as wubi, and wubi wont run quite as well as a real dual boot either.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

This will actually be more stable, if you hard shutdown a wubi it can cause problems in a virtual machine not likely.

Not sure what the problem with bcd and wubi so I'm just giving suggestions

---

### Post by LonelySEason on 2010-09-19
> **wilee-nilee said:**
> Awesome that will make it easier, look for the user bcbc to stop by they are pretty knowledgeable about wubi

I'm of no help in this, I was just concerned that the text be the easiest to read for you to get help. 

I would just install it in virtualbox and try it out that way. If you like it and want to dual boot it we can help you. In virtual it will not run quite as well as wubi, and wubi wont run quite as well as a real dual boot either.
[http://www.virtualbox.org/](http://www.virtualbox.org/)

This will actually be more stable, if you hard shutdown a wubi it can cause problems in a virtual machine not likely.

Not sure what the problem with bcd and wubi so I'm just giving suggestions

Thank for your suggestions, just as u say, running with VirtualBox isn't quit ok, I just wanted to dual boot with Ubuntu & Window7 side by side, I did it before for several times but this time, don't know what's wrong, I just don't get it....
Anyway... thank for helping.

---

### Post by LonelySEason on 2010-09-24
Anyone got any idea??? I'm still waiting for the solution. Honestly... I really enjoy the Linux world and don't want to just use only Window7. Any help will be appreciate.

---

### Post by bcbc on 2010-09-24
I saw someone with a similar problem recently. They were trying to install wubi on a dynamic partition. I don't think there was any feedback confirming whether that was the problem, but... I see you are installing on partition G: - so what is that exactly? Have you tried installing to C: ?
I am not sure whether the problem is with wubi or whether bcdedit doesn't like you adding an entry for G: since it seems that the attempt to add an entry to bcd is failing.

> >>command=C:\Windows\System32\bcdedit.exe /set {1c8d4435-c3d2-11df-b939-84289a803bcc} device partition=G:
>>retval=1
>>stderr=An error has occurred setting the element data.

PS I have no idea whether this is the real issue - just a guess. When you install wubi.exe make sure you are running it as an administrator (right click, run as admin).

---

### Post by LonelySEason on 2010-09-25
> **bcbc said:**
> I saw someone with a similar problem recently. They were trying to install wubi on a dynamic partition. I don't think there was any feedback confirming whether that was the problem, but... I see you are installing on partition G: - so what is that exactly? Have you tried installing to C: ?
I am not sure whether the problem is with wubi or whether bcdedit doesn't like you adding an entry for G: since it seems that the attempt to add an entry to bcd is failing.



PS I have no idea whether this is the real issue - just a guess. When you install wubi.exe make sure you are running it as an administrator (right click, run as admin).

Thank, I think it's about the Window, coz I just format the whole harddisk and then try to reinstall but I can't delete the old partitions and also can not to create new partition. 
Anyway... thank for your help.

---

