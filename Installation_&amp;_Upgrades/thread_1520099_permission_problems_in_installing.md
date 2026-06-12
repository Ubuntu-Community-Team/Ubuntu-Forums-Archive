---
title: "permission problems in installing"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by rahulshri1990 on 2010-06-29
sir,   I am using a compaq cq 40 2 gb ram 250 gb harddisk laptop with windows vista homebasic.
i am trying to install ubuntu with wubi 9.04 but while extracting the files from the cd the error message which looks like as follwing appears.


"" an error occured"
   Permission denied.
  for more information see the log file
   C:\user\rahul\appdata\temp\wubi-9.04-rev128.log..
please suggest me some way..

---

### Post by dino99 on 2010-06-29
why not a real install ?

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by bcbc on 2010-06-29
> **rahulshri1990 said:**
> sir,   I am using a compaq cq 40 2 gb ram 250 gb harddisk laptop with windows vista homebasic.
i am trying to install ubuntu with wubi 9.04 but while extracting the files from the cd the error message which looks like as follwing appears.


"" an error occured"
   Permission denied.
  for more information see the log file
   C:\user\rahul\appdata\temp\wubi-9.04-rev128.log..
please suggest me some way..

What does the log file say?

Have you tried installing from an Ubuntu CD, or are you just running wubi.exe? If the latter, it tries to check and download the latest version so there may be an internet issue.

If you have wubi.exe and the ubuntu .iso in the same folder, you can run wubi with option '--skipmd5check' to bypass the check and potential download of the latest .iso

See the wubi guide for more info...[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by rahulshri1990 on 2010-06-29
The log file looks like,, i cann't understand what to do.. i donn't want to install a new ISO .


06-28 20:05 INFO   root: === wubi 9.04 rev128 ===
06-28 20:05 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:05 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
06-28 20:05 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\data
06-28 20:05 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\bin\7z.exe
06-28 20:05 DEBUG  CommonBackend: Fetching basic info...
06-28 20:05 DEBUG  CommonBackend: original_exe=F:\wubi.exe
06-28 20:05 DEBUG  CommonBackend: platform=win32
06-28 20:05 DEBUG  CommonBackend: osname=nt
06-28 20:05 DEBUG  CommonBackend: language=en_US
06-28 20:05 DEBUG  CommonBackend: encoding=cp1252
06-28 20:05 DEBUG  WindowsBackend: arch=amd64
06-28 20:05 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\data\isolist.ini
06-28 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:05 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:05 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:05 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:05 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:05 DEBUG  WindowsBackend: Fetching host info...
06-28 20:05 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:05 DEBUG  WindowsBackend: windows version=vista
06-28 20:05 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:05 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:05 DEBUG  WindowsBackend: windows_build=6001
06-28 20:05 DEBUG  WindowsBackend: gmt=-8
06-28 20:05 DEBUG  WindowsBackend: country=US
06-28 20:05 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:05 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:05 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:05 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:05 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:05 DEBUG  WindowsBackend: windows_language=English
06-28 20:05 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:05 DEBUG  WindowsBackend: bootloader=vista
06-28 20:05 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63741.1757813 mb free )
06-28 20:05 DEBUG  WindowsBackend: drive=Drive(C: hd 63741.1757813 mb free )
06-28 20:05 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:05 DEBUG  WindowsBackend: drive=Drive(E: hd 22849.1757813 mb free ntfs)
06-28 20:05 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:05 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-28 20:05 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-28 20:05 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-28 20:05 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:05 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:05 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:05 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:05 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:05 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:05 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:05 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:05 DEBUG  CommonBackend: Searching for local CDs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl954C.tmp\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:05 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:05 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:05 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:05 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:05 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:05 INFO   root: Running the CD menu...
06-28 20:05 DEBUG  WindowsFrontend: __init__...
06-28 20:05 DEBUG  WindowsFrontend: on_init...
06-28 20:05 INFO   root: CD menu finished
06-28 20:05 INFO   root: Already installed, running the uninstaller...
06-28 20:05 INFO   root: Running the uninstaller...
06-28 20:05 INFO   CommonBackend: Launching previous uninestaller C:\ubuntu\uninstall-wubi.exe
06-28 20:05 DEBUG  root: application.quit
06-28 20:05 DEBUG  WindowsFrontend: frontend.quit
06-28 20:05 DEBUG  WindowsFrontend: frontend.on_quit
06-28 20:05 DEBUG  root: application.on_quit
06-28 20:05 INFO   root: sys.exit
06-28 20:06 INFO   root: === wubi 9.04 rev128 ===
06-28 20:06 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
06-28 20:06 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\data
06-28 20:06 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\bin\7z.exe
06-28 20:06 DEBUG  CommonBackend: Fetching basic info...
06-28 20:06 DEBUG  CommonBackend: original_exe=F:\wubi.exe
06-28 20:06 DEBUG  CommonBackend: platform=win32
06-28 20:06 DEBUG  CommonBackend: osname=nt
06-28 20:06 DEBUG  CommonBackend: language=en_US
06-28 20:06 DEBUG  CommonBackend: encoding=cp1252
06-28 20:06 DEBUG  WindowsBackend: arch=amd64
06-28 20:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\data\isolist.ini
06-28 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:06 DEBUG  WindowsBackend: Fetching host info...
06-28 20:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:06 DEBUG  WindowsBackend: windows version=vista
06-28 20:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:06 DEBUG  WindowsBackend: windows_build=6001
06-28 20:06 DEBUG  WindowsBackend: gmt=-8
06-28 20:06 DEBUG  WindowsBackend: country=US
06-28 20:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:06 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:06 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:06 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:06 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:06 DEBUG  WindowsBackend: windows_language=English
06-28 20:06 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:06 DEBUG  WindowsBackend: bootloader=vista
06-28 20:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63780.6289063 mb free )
06-28 20:06 DEBUG  WindowsBackend: drive=Drive(C: hd 63780.6289063 mb free )
06-28 20:06 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:06 DEBUG  WindowsBackend: drive=Drive(E: hd 22849.1757813 mb free ntfs)
06-28 20:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:06 DEBUG  WindowsBackend: uninstaller_path=None
06-28 20:06 DEBUG  WindowsBackend: previous_target_dir=None
06-28 20:06 DEBUG  WindowsBackend: previous_distro_name=None
06-28 20:06 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:06 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:06 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:06 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:06 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:06 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:06 DEBUG  CommonBackend: Searching for local CDs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:06 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:06 INFO   root: Running the CD menu...
06-28 20:06 DEBUG  WindowsFrontend: __init__...
06-28 20:06 DEBUG  WindowsFrontend: on_init...
06-28 20:06 INFO   root: CD menu finished
06-28 20:06 INFO   root: Running the installer...
06-28 20:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=rahul
06-28 20:06 INFO   root: Received settings
06-28 20:06 DEBUG  TaskList: # Running tasklist...
06-28 20:06 DEBUG  TaskList: ## Running select_target_dir...
06-28 20:06 INFO   WindowsBackend: Installing into C:\ubuntu
06-28 20:06 DEBUG  TaskList: ## Finished select_target_dir
06-28 20:06 DEBUG  TaskList: ## Running create_dir_structure...
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-28 20:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-28 20:06 DEBUG  TaskList: ## Finished create_dir_structure
06-28 20:06 DEBUG  TaskList: ## Running uncompress_target_dir...
06-28 20:06 DEBUG  TaskList: ## Finished uncompress_target_dir
06-28 20:06 DEBUG  TaskList: ## Running create_uninstaller...
06-28 20:06 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-28 20:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-28 20:06 DEBUG  TaskList: ## Finished create_uninstaller
06-28 20:06 DEBUG  TaskList: ## Running copy_installation_files...
06-28 20:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-28 20:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\winboot -> C:\ubuntu\winboot
06-28 20:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylEBF.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-28 20:06 DEBUG  TaskList: ## Finished copy_installation_files
06-28 20:06 DEBUG  TaskList: ## Running get_iso...
06-28 20:06 DEBUG  TaskList: New task copy_file
06-28 20:06 DEBUG  TaskList: ### Running copy_file...
06-28 20:06 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-28 20:06 DEBUG  TaskList: # Cancelling tasklist
06-28 20:06 DEBUG  TaskList: New task check_iso
06-28 20:06 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-28 20:06 DEBUG  CommonBackend: Searching for local ISO
06-28 20:06 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-28 20:06 DEBUG  TaskList: New task get_metalink
06-28 20:06 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-28 20:06 DEBUG  TaskList: # Cancelling tasklist
06-28 20:06 DEBUG  TaskList: # Finished tasklist
06-28 20:19 INFO   root: === wubi 9.04 rev128 ===
06-28 20:19 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:19 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-28 20:19 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\data
06-28 20:19 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\bin\7z.exe
06-28 20:19 DEBUG  CommonBackend: Fetching basic info...
06-28 20:19 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-28 20:19 DEBUG  CommonBackend: platform=win32
06-28 20:19 DEBUG  CommonBackend: osname=nt
06-28 20:19 DEBUG  CommonBackend: language=en_US
06-28 20:19 DEBUG  CommonBackend: encoding=cp1252
06-28 20:19 DEBUG  WindowsBackend: arch=amd64
06-28 20:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\data\isolist.ini
06-28 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:19 DEBUG  WindowsBackend: Fetching host info...
06-28 20:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:19 DEBUG  WindowsBackend: windows version=vista
06-28 20:19 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:19 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:19 DEBUG  WindowsBackend: windows_build=6001
06-28 20:19 DEBUG  WindowsBackend: gmt=-8
06-28 20:19 DEBUG  WindowsBackend: country=US
06-28 20:19 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:19 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:19 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:19 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:19 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:19 DEBUG  WindowsBackend: windows_language=English
06-28 20:19 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:19 DEBUG  WindowsBackend: bootloader=vista
06-28 20:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63777.6914063 mb free )
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(C: hd 63777.6914063 mb free )
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:19 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-28 20:19 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-28 20:19 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-28 20:19 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:19 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:19 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:19 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:19 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:19 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:19 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  CommonBackend: Searching for local CDs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:19 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:19 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:19 INFO   root: Running the CD menu...
06-28 20:19 DEBUG  WindowsFrontend: __init__...
06-28 20:19 DEBUG  WindowsFrontend: on_init...
06-28 20:19 INFO   root: CD menu finished
06-28 20:19 INFO   root: Already installed, running the uninstaller...
06-28 20:19 INFO   root: Running the uninstaller...
06-28 20:19 INFO   CommonBackend: This is the uninstaller running
06-28 20:19 INFO   root: Received settings
06-28 20:19 DEBUG  TaskList: # Running tasklist...
06-28 20:19 DEBUG  TaskList: ## Running Backup ISO...
06-28 20:19 DEBUG  TaskList: ## Finished Backup ISO
06-28 20:19 DEBUG  TaskList: ## Running Remove bootloader entry...
06-28 20:19 DEBUG  WindowsBackend: Could not find bcd id
06-28 20:19 DEBUG  WindowsBackend: undo_bootini C:
06-28 20:19 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63777.6914063 mb free )
06-28 20:19 DEBUG  WindowsBackend: undo_bootini D:
06-28 20:19 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:19 DEBUG  WindowsBackend: undo_bootini E:
06-28 20:19 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:19 DEBUG  TaskList: ## Finished Remove bootloader entry
06-28 20:19 DEBUG  TaskList: ## Running Remove target dir...
06-28 20:19 DEBUG  CommonBackend: Deleting C:\ubuntu
06-28 20:19 DEBUG  TaskList: ## Finished Remove target dir
06-28 20:19 DEBUG  TaskList: ## Running Remove registry key...
06-28 20:19 DEBUG  TaskList: ## Finished Remove registry key
06-28 20:19 DEBUG  TaskList: # Finished tasklist
06-28 20:19 INFO   root: Almost finished uninstalling
06-28 20:19 INFO   root: Finished uninstallation
06-28 20:19 DEBUG  CommonBackend: Fetching basic info...
06-28 20:19 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-28 20:19 DEBUG  CommonBackend: platform=win32
06-28 20:19 DEBUG  CommonBackend: osname=nt
06-28 20:19 DEBUG  CommonBackend: language=en_US
06-28 20:19 DEBUG  CommonBackend: encoding=cp1252
06-28 20:19 DEBUG  WindowsBackend: arch=amd64
06-28 20:19 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\data\isolist.ini
06-28 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:19 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:19 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:19 DEBUG  WindowsBackend: Fetching host info...
06-28 20:19 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:19 DEBUG  WindowsBackend: windows version=vista
06-28 20:19 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:19 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:19 DEBUG  WindowsBackend: windows_build=6001
06-28 20:19 DEBUG  WindowsBackend: gmt=-8
06-28 20:19 DEBUG  WindowsBackend: country=US
06-28 20:19 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:19 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:19 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:19 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:19 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:19 DEBUG  WindowsBackend: windows_language=English
06-28 20:19 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:19 DEBUG  WindowsBackend: bootloader=vista
06-28 20:19 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63779.5898438 mb free )
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(C: hd 63779.5898438 mb free )
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:19 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:19 DEBUG  WindowsBackend: uninstaller_path=None
06-28 20:19 DEBUG  WindowsBackend: previous_target_dir=None
06-28 20:19 DEBUG  WindowsBackend: previous_distro_name=None
06-28 20:19 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:19 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:19 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:19 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:19 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:19 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:19 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:19 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:19 DEBUG  CommonBackend: Searching for local CDs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC590.tmp is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:19 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:19 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:19 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:19 INFO   root: Running the installer...
06-28 20:19 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=rahul
06-28 20:19 INFO   root: Received settings
06-28 20:19 DEBUG  TaskList: # Running tasklist...
06-28 20:19 DEBUG  TaskList: ## Running select_target_dir...
06-28 20:19 INFO   WindowsBackend: Installing into C:\ubuntu
06-28 20:19 DEBUG  TaskList: ## Finished select_target_dir
06-28 20:19 DEBUG  TaskList: ## Running create_dir_structure...
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-28 20:19 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-28 20:19 DEBUG  TaskList: ## Finished create_dir_structure
06-28 20:19 DEBUG  TaskList: ## Running uncompress_target_dir...
06-28 20:19 DEBUG  TaskList: ## Finished uncompress_target_dir
06-28 20:19 DEBUG  TaskList: ## Running create_uninstaller...
06-28 20:19 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-28 20:19 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-28 20:19 DEBUG  TaskList: ## Finished create_uninstaller
06-28 20:19 DEBUG  TaskList: ## Running copy_installation_files...
06-28 20:19 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-28 20:19 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\winboot -> C:\ubuntu\winboot
06-28 20:19 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC590.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-28 20:19 DEBUG  TaskList: ## Finished copy_installation_files
06-28 20:19 DEBUG  TaskList: ## Running get_iso...
06-28 20:19 DEBUG  TaskList: New task copy_file
06-28 20:19 DEBUG  TaskList: ### Running copy_file...
06-28 20:19 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-28 20:19 DEBUG  TaskList: # Cancelling tasklist
06-28 20:19 DEBUG  TaskList: New task check_iso
06-28 20:19 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-28 20:19 DEBUG  CommonBackend: Searching for local ISO
06-28 20:19 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-28 20:19 DEBUG  TaskList: New task get_metalink
06-28 20:19 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-28 20:19 DEBUG  TaskList: # Cancelling tasklist
06-28 20:19 DEBUG  TaskList: # Finished tasklist
06-28 20:21 INFO   root: === wubi 9.04 rev128 ===
06-28 20:21 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-28 20:21 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\data
06-28 20:21 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\bin\7z.exe
06-28 20:21 DEBUG  CommonBackend: Fetching basic info...
06-28 20:21 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-28 20:21 DEBUG  CommonBackend: platform=win32
06-28 20:21 DEBUG  CommonBackend: osname=nt
06-28 20:21 DEBUG  CommonBackend: language=en_US
06-28 20:21 DEBUG  CommonBackend: encoding=cp1252
06-28 20:21 DEBUG  WindowsBackend: arch=amd64
06-28 20:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\data\isolist.ini
06-28 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:21 DEBUG  WindowsBackend: Fetching host info...
06-28 20:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:21 DEBUG  WindowsBackend: windows version=vista
06-28 20:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:21 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:21 DEBUG  WindowsBackend: windows_build=6001
06-28 20:21 DEBUG  WindowsBackend: gmt=-8
06-28 20:21 DEBUG  WindowsBackend: country=US
06-28 20:21 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:21 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:21 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:21 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:21 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:21 DEBUG  WindowsBackend: windows_language=English
06-28 20:21 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:21 DEBUG  WindowsBackend: bootloader=vista
06-28 20:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63776.1328125 mb free )
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(C: hd 63776.1328125 mb free )
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:21 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-28 20:21 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-28 20:21 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-28 20:21 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:21 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:21 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:21 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:21 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:21 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:21 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  CommonBackend: Searching for local CDs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:21 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:21 INFO   root: Running the CD menu...
06-28 20:21 DEBUG  WindowsFrontend: __init__...
06-28 20:21 DEBUG  WindowsFrontend: on_init...
06-28 20:21 INFO   root: CD menu finished
06-28 20:21 INFO   root: Running the CD menu...
06-28 20:21 INFO   root: CD menu finished
06-28 20:21 INFO   root: Already installed, running the uninstaller...
06-28 20:21 INFO   root: Running the uninstaller...
06-28 20:21 INFO   CommonBackend: This is the uninstaller running
06-28 20:21 INFO   root: Received settings
06-28 20:21 DEBUG  TaskList: # Running tasklist...
06-28 20:21 DEBUG  TaskList: ## Running Backup ISO...
06-28 20:21 DEBUG  TaskList: ## Finished Backup ISO
06-28 20:21 DEBUG  TaskList: ## Running Remove bootloader entry...
06-28 20:21 DEBUG  WindowsBackend: Could not find bcd id
06-28 20:21 DEBUG  WindowsBackend: undo_bootini C:
06-28 20:21 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63776.1328125 mb free )
06-28 20:21 DEBUG  WindowsBackend: undo_bootini D:
06-28 20:21 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:21 DEBUG  WindowsBackend: undo_bootini E:
06-28 20:21 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:21 DEBUG  TaskList: ## Finished Remove bootloader entry
06-28 20:21 DEBUG  TaskList: ## Running Remove target dir...
06-28 20:21 DEBUG  CommonBackend: Deleting C:\ubuntu
06-28 20:21 DEBUG  TaskList: ## Finished Remove target dir
06-28 20:21 DEBUG  TaskList: ## Running Remove registry key...
06-28 20:21 DEBUG  TaskList: ## Finished Remove registry key
06-28 20:21 DEBUG  TaskList: # Finished tasklist
06-28 20:21 INFO   root: Almost finished uninstalling
06-28 20:21 INFO   root: Finished uninstallation
06-28 20:21 DEBUG  CommonBackend: Fetching basic info...
06-28 20:21 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-28 20:21 DEBUG  CommonBackend: platform=win32
06-28 20:21 DEBUG  CommonBackend: osname=nt
06-28 20:21 DEBUG  CommonBackend: language=en_US
06-28 20:21 DEBUG  CommonBackend: encoding=cp1252
06-28 20:21 DEBUG  WindowsBackend: arch=amd64
06-28 20:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\data\isolist.ini
06-28 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:21 DEBUG  WindowsBackend: Fetching host info...
06-28 20:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:21 DEBUG  WindowsBackend: windows version=vista
06-28 20:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:21 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:21 DEBUG  WindowsBackend: windows_build=6001
06-28 20:21 DEBUG  WindowsBackend: gmt=-8
06-28 20:21 DEBUG  WindowsBackend: country=US
06-28 20:21 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:21 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:21 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:21 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:21 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:21 DEBUG  WindowsBackend: windows_language=English
06-28 20:21 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:21 DEBUG  WindowsBackend: bootloader=vista
06-28 20:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63778.03125 mb free )
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(C: hd 63778.03125 mb free )
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:21 DEBUG  WindowsBackend: uninstaller_path=None
06-28 20:21 DEBUG  WindowsBackend: previous_target_dir=None
06-28 20:21 DEBUG  WindowsBackend: previous_distro_name=None
06-28 20:21 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:21 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:21 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:21 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:21 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:21 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:21 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:21 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:21 DEBUG  CommonBackend: Searching for local CDs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylC226.tmp is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:21 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:21 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:21 INFO   root: Running the CD boot helper...
06-28 20:21 INFO   root: CD boot helper confirmed
06-28 20:21 DEBUG  TaskList: # Running tasklist...
06-28 20:21 DEBUG  TaskList: ## Running select_target_dir...
06-28 20:21 INFO   WindowsBackend: Installing into C:\ubuntu
06-28 20:21 DEBUG  TaskList: ## Finished select_target_dir
06-28 20:21 DEBUG  TaskList: ## Running create_dir_structure...
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-28 20:21 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-28 20:21 DEBUG  TaskList: ## Finished create_dir_structure
06-28 20:21 DEBUG  TaskList: ## Running uncompress_target_dir...
06-28 20:21 DEBUG  TaskList: ## Finished uncompress_target_dir
06-28 20:21 DEBUG  TaskList: ## Running create_uninstaller...
06-28 20:21 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-28 20:21 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-28 20:21 DEBUG  TaskList: ## Finished create_uninstaller
06-28 20:21 DEBUG  TaskList: ## Running copy_installation_files...
06-28 20:21 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-28 20:21 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\winboot -> C:\ubuntu\winboot
06-28 20:21 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylC226.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-28 20:21 DEBUG  TaskList: ## Finished copy_installation_files
06-28 20:21 DEBUG  TaskList: ## Running use_cd...
06-28 20:21 DEBUG  TaskList: New task copy_file
06-28 20:21 DEBUG  TaskList: ### Running copy_file...
06-28 20:21 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-28 20:21 DEBUG  TaskList: # Cancelling tasklist
06-28 20:21 DEBUG  TaskList: New task check_iso
06-28 20:21 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 119, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 216, in run_cd_boot
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-28 20:21 DEBUG  TaskList: ## Finished use_cd
06-28 20:21 DEBUG  TaskList: # Finished tasklist
06-28 20:27 INFO   root: === wubi 9.04 rev128 ===
06-28 20:27 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
06-28 20:27 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\data
06-28 20:27 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\bin\7z.exe
06-28 20:27 DEBUG  CommonBackend: Fetching basic info...
06-28 20:27 DEBUG  CommonBackend: original_exe=F:\wubi.exe
06-28 20:27 DEBUG  CommonBackend: platform=win32
06-28 20:27 DEBUG  CommonBackend: osname=nt
06-28 20:27 DEBUG  CommonBackend: language=en_US
06-28 20:27 DEBUG  CommonBackend: encoding=cp1252
06-28 20:27 DEBUG  WindowsBackend: arch=amd64
06-28 20:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\data\isolist.ini
06-28 20:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:27 DEBUG  WindowsBackend: Fetching host info...
06-28 20:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:27 DEBUG  WindowsBackend: windows version=vista
06-28 20:27 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:27 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:27 DEBUG  WindowsBackend: windows_build=6001
06-28 20:27 DEBUG  WindowsBackend: gmt=-8
06-28 20:27 DEBUG  WindowsBackend: country=US
06-28 20:27 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:27 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:27 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:27 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:27 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:27 DEBUG  WindowsBackend: windows_language=English
06-28 20:27 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:27 DEBUG  WindowsBackend: bootloader=vista
06-28 20:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63775.578125 mb free )
06-28 20:27 DEBUG  WindowsBackend: drive=Drive(C: hd 63775.578125 mb free )
06-28 20:27 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:27 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:27 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-28 20:27 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-28 20:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-28 20:27 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:27 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:27 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:27 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:27 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:27 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:27 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:27 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:27 DEBUG  CommonBackend: Searching for local CDs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylDE9B.tmp\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:27 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:27 INFO   root: Running the CD menu...
06-28 20:27 DEBUG  WindowsFrontend: __init__...
06-28 20:27 DEBUG  WindowsFrontend: on_init...
06-28 20:27 INFO   root: CD menu finished
06-28 20:27 DEBUG  CommonBackend: Showing info
06-28 20:27 DEBUG  root: application.quit
06-28 20:27 DEBUG  WindowsFrontend: frontend.quit
06-28 20:27 DEBUG  WindowsFrontend: frontend.on_quit
06-28 20:27 DEBUG  root: application.on_quit
06-28 20:27 INFO   root: sys.exit
06-28 20:28 INFO   root: === wubi 9.04 rev128 ===
06-28 20:28 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-28 20:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\wubi.exe"']
06-28 20:28 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\data
06-28 20:28 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\bin\7z.exe
06-28 20:28 DEBUG  CommonBackend: Fetching basic info...
06-28 20:28 DEBUG  CommonBackend: original_exe=F:\wubi.exe
06-28 20:28 DEBUG  CommonBackend: platform=win32
06-28 20:28 DEBUG  CommonBackend: osname=nt
06-28 20:28 DEBUG  CommonBackend: language=en_US
06-28 20:28 DEBUG  CommonBackend: encoding=cp1252
06-28 20:28 DEBUG  WindowsBackend: arch=amd64
06-28 20:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\data\isolist.ini
06-28 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:28 DEBUG  WindowsBackend: Fetching host info...
06-28 20:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:28 DEBUG  WindowsBackend: windows version=vista
06-28 20:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:28 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:28 DEBUG  WindowsBackend: windows_build=6001
06-28 20:28 DEBUG  WindowsBackend: gmt=-8
06-28 20:28 DEBUG  WindowsBackend: country=US
06-28 20:28 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:28 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:28 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:28 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:28 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:28 DEBUG  WindowsBackend: windows_language=English
06-28 20:28 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:28 DEBUG  WindowsBackend: bootloader=vista
06-28 20:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63777.8945313 mb free )
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(C: hd 63777.8945313 mb free )
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:28 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-28 20:28 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-28 20:28 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-28 20:28 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:28 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:28 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:28 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:28 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:28 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:28 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  CommonBackend: Searching for local CDs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-28 20:28 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-28 20:28 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:28 INFO   root: Running the CD menu...
06-28 20:28 DEBUG  WindowsFrontend: __init__...
06-28 20:28 DEBUG  WindowsFrontend: on_init...
06-28 20:28 INFO   root: CD menu finished
06-28 20:28 INFO   root: Running the CD menu...
06-28 20:28 INFO   root: CD menu finished
06-28 20:28 INFO   root: Already installed, running the uninstaller...
06-28 20:28 INFO   root: Running the uninstaller...
06-28 20:28 INFO   CommonBackend: This is the uninstaller running
06-28 20:28 INFO   root: Received settings
06-28 20:28 DEBUG  TaskList: # Running tasklist...
06-28 20:28 DEBUG  TaskList: ## Running Backup ISO...
06-28 20:28 DEBUG  TaskList: ## Finished Backup ISO
06-28 20:28 DEBUG  TaskList: ## Running Remove bootloader entry...
06-28 20:28 DEBUG  WindowsBackend: Could not find bcd id
06-28 20:28 DEBUG  WindowsBackend: undo_bootini C:
06-28 20:28 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63777.8945313 mb free )
06-28 20:28 DEBUG  WindowsBackend: undo_bootini D:
06-28 20:28 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:28 DEBUG  WindowsBackend: undo_bootini E:
06-28 20:28 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:28 DEBUG  TaskList: ## Finished Remove bootloader entry
06-28 20:28 DEBUG  TaskList: ## Running Remove target dir...
06-28 20:28 DEBUG  CommonBackend: Deleting C:\ubuntu
06-28 20:28 DEBUG  TaskList: ## Finished Remove target dir
06-28 20:28 DEBUG  TaskList: ## Running Remove registry key...
06-28 20:28 DEBUG  TaskList: ## Finished Remove registry key
06-28 20:28 DEBUG  TaskList: # Finished tasklist
06-28 20:28 INFO   root: Almost finished uninstalling
06-28 20:28 INFO   root: Finished uninstallation
06-28 20:28 DEBUG  CommonBackend: Fetching basic info...
06-28 20:28 DEBUG  CommonBackend: original_exe=F:\wubi.exe
06-28 20:28 DEBUG  CommonBackend: platform=win32
06-28 20:28 DEBUG  CommonBackend: osname=nt
06-28 20:28 DEBUG  CommonBackend: language=en_US
06-28 20:28 DEBUG  CommonBackend: encoding=cp1252
06-28 20:28 DEBUG  WindowsBackend: arch=amd64
06-28 20:28 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\data\isolist.ini
06-28 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-28 20:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-28 20:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-28 20:28 DEBUG  WindowsBackend: Fetching host info...
06-28 20:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-28 20:28 DEBUG  WindowsBackend: windows version=vista
06-28 20:28 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-28 20:28 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-28 20:28 DEBUG  WindowsBackend: windows_build=6001
06-28 20:28 DEBUG  WindowsBackend: gmt=-8
06-28 20:28 DEBUG  WindowsBackend: country=US
06-28 20:28 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-28 20:28 DEBUG  WindowsBackend: windows_username=rahul
06-28 20:28 DEBUG  WindowsBackend: user_full_name=rahul
06-28 20:28 DEBUG  WindowsBackend: user_directory=rahul
06-28 20:28 DEBUG  WindowsBackend: windows_language_code=1033
06-28 20:28 DEBUG  WindowsBackend: windows_language=English
06-28 20:28 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-28 20:28 DEBUG  WindowsBackend: bootloader=vista
06-28 20:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63779.7929688 mb free )
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(C: hd 63779.7929688 mb free )
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(E: hd 22150.046875 mb free ntfs)
06-28 20:28 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-28 20:28 DEBUG  WindowsBackend: uninstaller_path=None
06-28 20:28 DEBUG  WindowsBackend: previous_target_dir=None
06-28 20:28 DEBUG  WindowsBackend: previous_distro_name=None
06-28 20:28 DEBUG  WindowsBackend: keyboard_id=67699721
06-28 20:28 DEBUG  WindowsBackend: keyboard_layout=us
06-28 20:28 DEBUG  WindowsBackend: keyboard_variant=
06-28 20:28 DEBUG  CommonBackend: locale=en_US.UTF-8
06-28 20:28 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-28 20:28 DEBUG  CommonBackend: Searching ISOs on USB devices
06-28 20:28 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-28 20:28 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-28 20:28 DEBUG  CommonBackend: Searching for local CDs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-28 20:28 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-28 20:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-28 20:28 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-28 20:28 INFO   root: Running the CD boot helper...
06-28 20:28 INFO   root: CD boot helper confirmed
06-28 20:28 DEBUG  TaskList: # Running tasklist...
06-28 20:28 DEBUG  TaskList: ## Running select_target_dir...
06-28 20:28 INFO   WindowsBackend: Installing into C:\ubuntu
06-28 20:28 DEBUG  TaskList: ## Finished select_target_dir
06-28 20:28 DEBUG  TaskList: ## Running create_dir_structure...
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-28 20:28 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-28 20:28 DEBUG  TaskList: ## Finished create_dir_structure
06-28 20:28 DEBUG  TaskList: ## Running uncompress_target_dir...
06-28 20:28 DEBUG  TaskList: ## Finished uncompress_target_dir
06-28 20:28 DEBUG  TaskList: ## Running create_uninstaller...
06-28 20:28 DEBUG  WindowsBackend: Copying uninstaller F:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-28 20:28 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-28 20:28 DEBUG  TaskList: ## Finished create_uninstaller
06-28 20:28 DEBUG  TaskList: ## Running copy_installation_files...
06-28 20:28 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-28 20:28 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\winboot -> C:\ubuntu\winboot
06-28 20:28 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl142C.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-28 20:28 DEBUG  TaskList: ## Finished copy_installation_files
06-28 20:28 DEBUG  TaskList: ## Running use_cd...
06-28 20:28 DEBUG  TaskList: New task copy_file
06-28 20:28 DEBUG  TaskList: ### Running copy_file...
06-28 20:28 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-28 20:28 DEBUG  TaskList: # Cancelling tasklist
06-28 20:28 DEBUG  TaskList: New task check_iso
06-28 20:28 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 119, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 216, in run_cd_boot
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-28 20:28 DEBUG  TaskList: ## Finished use_cd
06-28 20:28 DEBUG  TaskList: # Finished tasklist
06-29 00:06 INFO   root: === wubi 9.04 rev128 ===
06-29 00:06 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 00:06 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-29 00:06 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\data
06-29 00:06 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\bin\7z.exe
06-29 00:06 DEBUG  CommonBackend: Fetching basic info...
06-29 00:06 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 00:06 DEBUG  CommonBackend: platform=win32
06-29 00:06 DEBUG  CommonBackend: osname=nt
06-29 00:06 DEBUG  CommonBackend: language=en_US
06-29 00:06 DEBUG  CommonBackend: encoding=cp1252
06-29 00:06 DEBUG  WindowsBackend: arch=amd64
06-29 00:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\data\isolist.ini
06-29 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 00:06 DEBUG  WindowsBackend: Fetching host info...
06-29 00:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 00:06 DEBUG  WindowsBackend: windows version=vista
06-29 00:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 00:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 00:06 DEBUG  WindowsBackend: windows_build=6001
06-29 00:06 DEBUG  WindowsBackend: gmt=-8
06-29 00:06 DEBUG  WindowsBackend: country=US
06-29 00:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 00:06 DEBUG  WindowsBackend: windows_username=rahul
06-29 00:06 DEBUG  WindowsBackend: user_full_name=rahul
06-29 00:06 DEBUG  WindowsBackend: user_directory=rahul
06-29 00:06 DEBUG  WindowsBackend: windows_language_code=1033
06-29 00:06 DEBUG  WindowsBackend: windows_language=English
06-29 00:06 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 00:06 DEBUG  WindowsBackend: bootloader=vista
06-29 00:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63517.1054688 mb free )
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(C: hd 63517.1054688 mb free )
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-29 00:06 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-29 00:06 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-29 00:06 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-29 00:06 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 00:06 DEBUG  WindowsBackend: keyboard_layout=us
06-29 00:06 DEBUG  WindowsBackend: keyboard_variant=
06-29 00:06 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 00:06 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 00:06 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 00:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  CommonBackend: Searching for local CDs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-29 00:06 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-29 00:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-29 00:06 INFO   root: Running the CD menu...
06-29 00:06 DEBUG  WindowsFrontend: __init__...
06-29 00:06 DEBUG  WindowsFrontend: on_init...
06-29 00:06 INFO   root: CD menu finished
06-29 00:06 INFO   root: Already installed, running the uninstaller...
06-29 00:06 INFO   root: Running the uninstaller...
06-29 00:06 INFO   CommonBackend: This is the uninstaller running
06-29 00:06 INFO   root: Received settings
06-29 00:06 DEBUG  TaskList: # Running tasklist...
06-29 00:06 DEBUG  TaskList: ## Running Backup ISO...
06-29 00:06 DEBUG  TaskList: ## Finished Backup ISO
06-29 00:06 DEBUG  TaskList: ## Running Remove bootloader entry...
06-29 00:06 DEBUG  WindowsBackend: Could not find bcd id
06-29 00:06 DEBUG  WindowsBackend: undo_bootini C:
06-29 00:06 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 63517.1054688 mb free )
06-29 00:06 DEBUG  WindowsBackend: undo_bootini D:
06-29 00:06 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:06 DEBUG  WindowsBackend: undo_bootini E:
06-29 00:06 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:06 DEBUG  TaskList: ## Finished Remove bootloader entry
06-29 00:06 DEBUG  TaskList: ## Running Remove target dir...
06-29 00:06 DEBUG  CommonBackend: Deleting C:\ubuntu
06-29 00:06 DEBUG  TaskList: ## Finished Remove target dir
06-29 00:06 DEBUG  TaskList: ## Running Remove registry key...
06-29 00:06 DEBUG  TaskList: ## Finished Remove registry key
06-29 00:06 DEBUG  TaskList: # Finished tasklist
06-29 00:06 INFO   root: Almost finished uninstalling
06-29 00:06 INFO   root: Finished uninstallation
06-29 00:06 DEBUG  CommonBackend: Fetching basic info...
06-29 00:06 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 00:06 DEBUG  CommonBackend: platform=win32
06-29 00:06 DEBUG  CommonBackend: osname=nt
06-29 00:06 DEBUG  CommonBackend: language=en_US
06-29 00:06 DEBUG  CommonBackend: encoding=cp1252
06-29 00:06 DEBUG  WindowsBackend: arch=amd64
06-29 00:06 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\data\isolist.ini
06-29 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 00:06 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 00:06 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 00:06 DEBUG  WindowsBackend: Fetching host info...
06-29 00:06 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 00:06 DEBUG  WindowsBackend: windows version=vista
06-29 00:06 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 00:06 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 00:06 DEBUG  WindowsBackend: windows_build=6001
06-29 00:06 DEBUG  WindowsBackend: gmt=-8
06-29 00:06 DEBUG  WindowsBackend: country=US
06-29 00:06 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 00:06 DEBUG  WindowsBackend: windows_username=rahul
06-29 00:06 DEBUG  WindowsBackend: user_full_name=rahul
06-29 00:06 DEBUG  WindowsBackend: user_directory=rahul
06-29 00:06 DEBUG  WindowsBackend: windows_language_code=1033
06-29 00:06 DEBUG  WindowsBackend: windows_language=English
06-29 00:06 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 00:06 DEBUG  WindowsBackend: bootloader=vista
06-29 00:06 DEBUG  WindowsBackend: system_drive=Drive(C: hd 63518.7539063 mb free )
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(C: hd 63518.7539063 mb free )
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:06 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-29 00:06 DEBUG  WindowsBackend: uninstaller_path=None
06-29 00:06 DEBUG  WindowsBackend: previous_target_dir=None
06-29 00:06 DEBUG  WindowsBackend: previous_distro_name=None
06-29 00:06 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 00:06 DEBUG  WindowsBackend: keyboard_layout=us
06-29 00:06 DEBUG  WindowsBackend: keyboard_variant=
06-29 00:06 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 00:06 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 00:06 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 00:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:06 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:06 DEBUG  CommonBackend: Searching for local CDs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:06 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:06 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-29 00:06 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-29 00:06 INFO   root: Running the installer...
06-29 00:06 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=rahul
06-29 00:06 INFO   root: Received settings
06-29 00:06 DEBUG  TaskList: # Running tasklist...
06-29 00:06 DEBUG  TaskList: ## Running select_target_dir...
06-29 00:06 INFO   WindowsBackend: Installing into C:\ubuntu
06-29 00:06 DEBUG  TaskList: ## Finished select_target_dir
06-29 00:06 DEBUG  TaskList: ## Running create_dir_structure...
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-29 00:06 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-29 00:06 DEBUG  TaskList: ## Finished create_dir_structure
06-29 00:06 DEBUG  TaskList: ## Running uncompress_target_dir...
06-29 00:06 DEBUG  TaskList: ## Finished uncompress_target_dir
06-29 00:06 DEBUG  TaskList: ## Running create_uninstaller...
06-29 00:06 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-29 00:06 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-29 00:06 DEBUG  TaskList: ## Finished create_uninstaller
06-29 00:06 DEBUG  TaskList: ## Running copy_installation_files...
06-29 00:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-29 00:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\winboot -> C:\ubuntu\winboot
06-29 00:06 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylAE67.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-29 00:06 DEBUG  TaskList: ## Finished copy_installation_files
06-29 00:06 DEBUG  TaskList: ## Running get_iso...
06-29 00:06 DEBUG  TaskList: New task copy_file
06-29 00:06 DEBUG  TaskList: ### Running copy_file...
06-29 00:18 DEBUG  TaskList: ### Finished copy_file
06-29 00:18 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-29 00:18 DEBUG  TaskList: # Cancelling tasklist
06-29 00:18 DEBUG  TaskList: New task check_iso
06-29 00:18 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-29 00:18 DEBUG  CommonBackend: Searching for local ISO
06-29 00:18 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-29 00:18 DEBUG  TaskList: New task get_metalink
06-29 00:18 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-29 00:18 DEBUG  TaskList: # Cancelling tasklist
06-29 00:18 DEBUG  TaskList: # Finished tasklist
06-29 00:41 INFO   root: === wubi 9.04 rev128 ===
06-29 00:41 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 00:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-29 00:41 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\data
06-29 00:41 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\bin\7z.exe
06-29 00:41 DEBUG  CommonBackend: Fetching basic info...
06-29 00:41 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 00:41 DEBUG  CommonBackend: platform=win32
06-29 00:41 DEBUG  CommonBackend: osname=nt
06-29 00:41 DEBUG  CommonBackend: language=en_US
06-29 00:41 DEBUG  CommonBackend: encoding=cp1252
06-29 00:41 DEBUG  WindowsBackend: arch=amd64
06-29 00:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\data\isolist.ini
06-29 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 00:41 DEBUG  WindowsBackend: Fetching host info...
06-29 00:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 00:41 DEBUG  WindowsBackend: windows version=vista
06-29 00:41 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 00:41 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 00:41 DEBUG  WindowsBackend: windows_build=6001
06-29 00:41 DEBUG  WindowsBackend: gmt=-8
06-29 00:41 DEBUG  WindowsBackend: country=US
06-29 00:41 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 00:41 DEBUG  WindowsBackend: windows_username=rahul
06-29 00:41 DEBUG  WindowsBackend: user_full_name=rahul
06-29 00:41 DEBUG  WindowsBackend: user_directory=rahul
06-29 00:41 DEBUG  WindowsBackend: windows_language_code=1033
06-29 00:41 DEBUG  WindowsBackend: windows_language=English
06-29 00:41 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 00:41 DEBUG  WindowsBackend: bootloader=vista
06-29 00:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61737.375 mb free )
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(C: hd 61737.375 mb free )
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-29 00:41 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-29 00:41 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-29 00:41 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-29 00:41 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 00:41 DEBUG  WindowsBackend: keyboard_layout=us
06-29 00:41 DEBUG  WindowsBackend: keyboard_variant=
06-29 00:41 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 00:41 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 00:41 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 00:41 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  CommonBackend: Searching for local CDs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:   info=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
06-29 00:41 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
06-29 00:41 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-29 00:41 INFO   root: Running the CD menu...
06-29 00:41 DEBUG  WindowsFrontend: __init__...
06-29 00:41 DEBUG  WindowsFrontend: on_init...
06-29 00:41 INFO   root: CD menu finished
06-29 00:41 INFO   root: Already installed, running the uninstaller...
06-29 00:41 INFO   root: Running the uninstaller...
06-29 00:41 INFO   CommonBackend: This is the uninstaller running
06-29 00:41 INFO   root: Received settings
06-29 00:41 DEBUG  TaskList: # Running tasklist...
06-29 00:41 DEBUG  TaskList: ## Running Backup ISO...
06-29 00:41 DEBUG  TaskList: ## Finished Backup ISO
06-29 00:41 DEBUG  TaskList: ## Running Remove bootloader entry...
06-29 00:41 DEBUG  WindowsBackend: Could not find bcd id
06-29 00:41 DEBUG  WindowsBackend: undo_bootini C:
06-29 00:41 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 61737.375 mb free )
06-29 00:41 DEBUG  WindowsBackend: undo_bootini D:
06-29 00:41 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:41 DEBUG  WindowsBackend: undo_bootini E:
06-29 00:41 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:41 DEBUG  TaskList: ## Finished Remove bootloader entry
06-29 00:41 DEBUG  TaskList: ## Running Remove target dir...
06-29 00:41 DEBUG  CommonBackend: Deleting C:\ubuntu
06-29 00:41 DEBUG  TaskList: ## Finished Remove target dir
06-29 00:41 DEBUG  TaskList: ## Running Remove registry key...
06-29 00:41 DEBUG  TaskList: ## Finished Remove registry key
06-29 00:41 DEBUG  TaskList: # Finished tasklist
06-29 00:41 INFO   root: Almost finished uninstalling
06-29 00:41 INFO   root: Finished uninstallation
06-29 00:41 DEBUG  CommonBackend: Fetching basic info...
06-29 00:41 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 00:41 DEBUG  CommonBackend: platform=win32
06-29 00:41 DEBUG  CommonBackend: osname=nt
06-29 00:41 DEBUG  CommonBackend: language=en_US
06-29 00:41 DEBUG  CommonBackend: encoding=cp1252
06-29 00:41 DEBUG  WindowsBackend: arch=amd64
06-29 00:41 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\data\isolist.ini
06-29 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 00:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 00:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 00:41 DEBUG  WindowsBackend: Fetching host info...
06-29 00:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 00:41 DEBUG  WindowsBackend: windows version=vista
06-29 00:41 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 00:41 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 00:41 DEBUG  WindowsBackend: windows_build=6001
06-29 00:41 DEBUG  WindowsBackend: gmt=-8
06-29 00:41 DEBUG  WindowsBackend: country=US
06-29 00:41 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 00:41 DEBUG  WindowsBackend: windows_username=rahul
06-29 00:41 DEBUG  WindowsBackend: user_full_name=rahul
06-29 00:41 DEBUG  WindowsBackend: user_directory=rahul
06-29 00:41 DEBUG  WindowsBackend: windows_language_code=1033
06-29 00:41 DEBUG  WindowsBackend: windows_language=English
06-29 00:41 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 00:41 DEBUG  WindowsBackend: bootloader=vista
06-29 00:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62437.2773438 mb free )
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(C: hd 62437.2773438 mb free )
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 00:41 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
06-29 00:41 DEBUG  WindowsBackend: uninstaller_path=None
06-29 00:41 DEBUG  WindowsBackend: previous_target_dir=None
06-29 00:41 DEBUG  WindowsBackend: previous_distro_name=None
06-29 00:41 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 00:41 DEBUG  WindowsBackend: keyboard_layout=us
06-29 00:41 DEBUG  WindowsBackend: keyboard_variant=
06-29 00:41 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 00:41 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 00:41 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 00:41 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 00:41 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 00:41 DEBUG  CommonBackend: Searching for local CDs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 00:41 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 00:41 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
06-29 00:41 INFO   Distro: Found a valid CD for Ubuntu: F:\
06-29 00:41 INFO   root: Running the installer...
06-29 00:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=rahul
06-29 00:41 INFO   root: Received settings
06-29 00:41 DEBUG  TaskList: # Running tasklist...
06-29 00:41 DEBUG  TaskList: ## Running select_target_dir...
06-29 00:41 INFO   WindowsBackend: Installing into C:\ubuntu
06-29 00:41 DEBUG  TaskList: ## Finished select_target_dir
06-29 00:41 DEBUG  TaskList: ## Running create_dir_structure...
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-29 00:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-29 00:41 DEBUG  TaskList: ## Finished create_dir_structure
06-29 00:41 DEBUG  TaskList: ## Running uncompress_target_dir...
06-29 00:41 DEBUG  TaskList: ## Finished uncompress_target_dir
06-29 00:41 DEBUG  TaskList: ## Running create_uninstaller...
06-29 00:41 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-29 00:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-29 00:41 DEBUG  TaskList: ## Finished create_uninstaller
06-29 00:41 DEBUG  TaskList: ## Running copy_installation_files...
06-29 00:41 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-29 00:41 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\winboot -> C:\ubuntu\winboot
06-29 00:41 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pyl24EE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-29 00:41 DEBUG  TaskList: ## Finished copy_installation_files
06-29 00:41 DEBUG  TaskList: ## Running get_iso...
06-29 00:41 DEBUG  TaskList: New task copy_file
06-29 00:41 DEBUG  TaskList: ### Running copy_file...
06-29 00:52 DEBUG  TaskList: ### Finished copy_file
06-29 00:52 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-29 00:52 DEBUG  TaskList: # Cancelling tasklist
06-29 00:52 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 125, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 193, in run_cd_menu
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 117, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied
06-29 00:52 DEBUG  TaskList: New task check_iso
06-29 00:52 DEBUG  CommonBackend: Searching for local ISO
06-29 00:52 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-29 00:52 DEBUG  TaskList: New task get_metalink
06-29 00:52 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 482, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
06-29 00:52 DEBUG  TaskList: # Cancelling tasklist
06-29 00:52 DEBUG  TaskList: # Finished tasklist
06-29 05:33 INFO   root: === wubi 9.04 rev128 ===
06-29 05:33 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 05:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
06-29 05:33 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\data
06-29 05:33 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\bin\7z.exe
06-29 05:33 DEBUG  CommonBackend: Fetching basic info...
06-29 05:33 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
06-29 05:33 DEBUG  CommonBackend: platform=win32
06-29 05:33 DEBUG  CommonBackend: osname=nt
06-29 05:33 DEBUG  CommonBackend: language=en_US
06-29 05:33 DEBUG  CommonBackend: encoding=cp1252
06-29 05:33 DEBUG  WindowsBackend: arch=amd64
06-29 05:33 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\data\isolist.ini
06-29 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 05:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 05:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 05:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 05:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 05:33 DEBUG  WindowsBackend: Fetching host info...
06-29 05:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 05:33 DEBUG  WindowsBackend: windows version=vista
06-29 05:33 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 05:33 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 05:33 DEBUG  WindowsBackend: windows_build=6001
06-29 05:33 DEBUG  WindowsBackend: gmt=-8
06-29 05:33 DEBUG  WindowsBackend: country=US
06-29 05:33 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 05:33 DEBUG  WindowsBackend: windows_username=rahul
06-29 05:33 DEBUG  WindowsBackend: user_full_name=rahul
06-29 05:33 DEBUG  WindowsBackend: user_directory=rahul
06-29 05:33 DEBUG  WindowsBackend: windows_language_code=1033
06-29 05:33 DEBUG  WindowsBackend: windows_language=English
06-29 05:33 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 05:33 DEBUG  WindowsBackend: bootloader=vista
06-29 05:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 61832.7421875 mb free )
06-29 05:33 DEBUG  WindowsBackend: drive=Drive(C: hd 61832.7421875 mb free )
06-29 05:33 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 05:33 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:33 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
06-29 05:33 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
06-29 05:33 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-29 05:33 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 05:33 DEBUG  WindowsBackend: keyboard_layout=us
06-29 05:33 DEBUG  WindowsBackend: keyboard_variant=
06-29 05:33 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 05:33 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 05:33 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 05:33 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:33 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:33 DEBUG  CommonBackend: Searching for local CDs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylD6ED.tmp\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:33 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:33 INFO   root: Running the uninstaller...
06-29 05:33 INFO   CommonBackend: This is the uninstaller running
06-29 05:33 DEBUG  WindowsFrontend: __init__...
06-29 05:33 DEBUG  WindowsFrontend: on_init...
06-29 05:33 INFO   root: Received settings
06-29 05:33 DEBUG  TaskList: # Running tasklist...
06-29 05:33 DEBUG  TaskList: ## Running Backup ISO...
06-29 05:33 DEBUG  TaskList: ## Finished Backup ISO
06-29 05:33 DEBUG  TaskList: ## Running Remove bootloader entry...
06-29 05:33 DEBUG  WindowsBackend: Could not find bcd id
06-29 05:33 DEBUG  WindowsBackend: undo_bootini C:
06-29 05:33 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 61832.7421875 mb free )
06-29 05:33 DEBUG  WindowsBackend: undo_bootini D:
06-29 05:33 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26285.4882813 mb free ntfs)
06-29 05:33 DEBUG  WindowsBackend: undo_bootini E:
06-29 05:33 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:33 DEBUG  TaskList: ## Finished Remove bootloader entry
06-29 05:33 DEBUG  TaskList: ## Running Remove target dir...
06-29 05:33 DEBUG  CommonBackend: Deleting C:\ubuntu
06-29 05:33 DEBUG  TaskList: ## Finished Remove target dir
06-29 05:33 DEBUG  TaskList: ## Running Remove registry key...
06-29 05:33 DEBUG  TaskList: ## Finished Remove registry key
06-29 05:33 DEBUG  TaskList: # Finished tasklist
06-29 05:33 INFO   root: Almost finished uninstalling
06-29 05:33 INFO   root: Finished uninstallation
06-29 05:33 DEBUG  root: application.quit
06-29 05:33 DEBUG  WindowsFrontend: frontend.quit
06-29 05:33 DEBUG  WindowsFrontend: frontend.on_quit
06-29 05:33 DEBUG  root: application.on_quit
06-29 05:33 INFO   root: sys.exit
06-29 05:34 INFO   root: === wubi 9.04 rev128 ===
06-29 05:34 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 05:34 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-29 05:34 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\data
06-29 05:34 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\bin\7z.exe
06-29 05:34 DEBUG  CommonBackend: Fetching basic info...
06-29 05:34 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 05:34 DEBUG  CommonBackend: platform=win32
06-29 05:34 DEBUG  CommonBackend: osname=nt
06-29 05:34 DEBUG  CommonBackend: language=en_US
06-29 05:34 DEBUG  CommonBackend: encoding=cp1252
06-29 05:34 DEBUG  WindowsBackend: arch=amd64
06-29 05:34 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\data\isolist.ini
06-29 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 05:34 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 05:34 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 05:34 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 05:34 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 05:34 DEBUG  WindowsBackend: Fetching host info...
06-29 05:34 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 05:34 DEBUG  WindowsBackend: windows version=vista
06-29 05:34 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 05:34 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 05:34 DEBUG  WindowsBackend: windows_build=6001
06-29 05:34 DEBUG  WindowsBackend: gmt=-8
06-29 05:34 DEBUG  WindowsBackend: country=US
06-29 05:34 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 05:34 DEBUG  WindowsBackend: windows_username=rahul
06-29 05:34 DEBUG  WindowsBackend: user_full_name=rahul
06-29 05:34 DEBUG  WindowsBackend: user_directory=rahul
06-29 05:34 DEBUG  WindowsBackend: windows_language_code=1033
06-29 05:34 DEBUG  WindowsBackend: windows_language=English
06-29 05:34 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 05:34 DEBUG  WindowsBackend: bootloader=vista
06-29 05:34 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62532.6210938 mb free )
06-29 05:34 DEBUG  WindowsBackend: drive=Drive(C: hd 62532.6210938 mb free )
06-29 05:34 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 05:34 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:34 DEBUG  WindowsBackend: uninstaller_path=None
06-29 05:34 DEBUG  WindowsBackend: previous_target_dir=None
06-29 05:34 DEBUG  WindowsBackend: previous_distro_name=None
06-29 05:34 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 05:34 DEBUG  WindowsBackend: keyboard_layout=us
06-29 05:34 DEBUG  WindowsBackend: keyboard_variant=
06-29 05:34 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 05:34 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 05:34 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 05:34 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:34 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:34 DEBUG  CommonBackend: Searching for local CDs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:34 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:34 INFO   root: Running the installer...
06-29 05:34 DEBUG  WindowsFrontend: __init__...
06-29 05:34 DEBUG  WindowsFrontend: on_init...
06-29 05:35 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=21000MB, distro_name=Ubuntu, language=English, username=rahul
06-29 05:35 INFO   root: Received settings
06-29 05:35 DEBUG  TaskList: # Running tasklist...
06-29 05:35 DEBUG  TaskList: ## Running select_target_dir...
06-29 05:35 INFO   WindowsBackend: Installing into D:\ubuntu
06-29 05:35 DEBUG  TaskList: ## Finished select_target_dir
06-29 05:35 DEBUG  TaskList: ## Running create_dir_structure...
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-29 05:35 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-29 05:35 DEBUG  TaskList: ## Finished create_dir_structure
06-29 05:35 DEBUG  TaskList: ## Running uncompress_target_dir...
06-29 05:35 DEBUG  TaskList: ## Finished uncompress_target_dir
06-29 05:35 DEBUG  TaskList: ## Running create_uninstaller...
06-29 05:35 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-29 05:35 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-29 05:35 DEBUG  TaskList: ## Finished create_uninstaller
06-29 05:35 DEBUG  TaskList: ## Running copy_installation_files...
06-29 05:35 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-29 05:35 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\winboot -> D:\ubuntu\winboot
06-29 05:35 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-29 05:35 DEBUG  TaskList: ## Finished copy_installation_files
06-29 05:35 DEBUG  TaskList: ## Running get_iso...
06-29 05:35 DEBUG  CommonBackend: Searching for local CD
06-29 05:35 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp is a valid Ubuntu CD
06-29 05:35 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylA37F.tmp\casper\filesystem.squashfs
06-29 05:35 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:35 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:35 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:35 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:35 DEBUG  CommonBackend: Searching for local ISO
06-29 05:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-29 05:35 DEBUG  TaskList: New task get_metalink
06-29 05:35 DEBUG  TaskList: ### Running get_metalink...
06-29 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink) > D:\ubuntu\install
06-29 05:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink, basename=ubuntu-9.04-desktop-amd64.metalink, length=19580, text=None
06-29 05:35 DEBUG  downloader: download finished (read 19580 bytes)
06-29 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > D:\ubuntu\install
06-29 05:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
06-29 05:35 DEBUG  downloader: download finished (read 413 bytes)
06-29 05:35 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-29 05:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-29 05:35 DEBUG  downloader: download finished (read 189 bytes)
06-29 05:35 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-29 05:35 INFO   saplog: Checking block bindings..
06-29 05:35 INFO   saplog: Key verified successfully.
06-29 05:35 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

06-29 05:35 DEBUG  TaskList: ### Finished get_metalink
06-29 05:35 DEBUG  TaskList: New task download
06-29 05:35 DEBUG  TaskList: ### Running download...
06-29 05:35 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso) > D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
06-29 05:35 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso, basename=ubuntu-9.04-desktop-amd64.iso, length=730554368, text=None
06-29 05:39 INFO   WindowsFrontend: Operation cancelled
06-29 05:39 DEBUG  WindowsFrontend: frontend.quit
06-29 05:39 DEBUG  WindowsFrontend: frontend.on_quit
06-29 05:39 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-29 05:39 DEBUG  TaskList: # Cancelling tasklist
06-29 05:39 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-29 05:39 DEBUG  root: application.on_quit
06-29 05:39 DEBUG  root: Forceful exit
06-29 05:39 INFO   root: sys.exit
06-29 05:39 INFO   root: === wubi 9.04 rev128 ===
06-29 05:39 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 05:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\ubu\\wubi.exe"']
06-29 05:39 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\data
06-29 05:39 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\bin\7z.exe
06-29 05:39 DEBUG  CommonBackend: Fetching basic info...
06-29 05:39 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 05:39 DEBUG  CommonBackend: platform=win32
06-29 05:39 DEBUG  CommonBackend: osname=nt
06-29 05:39 DEBUG  CommonBackend: language=en_US
06-29 05:39 DEBUG  CommonBackend: encoding=cp1252
06-29 05:39 DEBUG  WindowsBackend: arch=amd64
06-29 05:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\data\isolist.ini
06-29 05:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 05:39 DEBUG  WindowsBackend: Fetching host info...
06-29 05:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 05:39 DEBUG  WindowsBackend: windows version=vista
06-29 05:39 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 05:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 05:39 DEBUG  WindowsBackend: windows_build=6001
06-29 05:39 DEBUG  WindowsBackend: gmt=-8
06-29 05:39 DEBUG  WindowsBackend: country=US
06-29 05:39 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 05:39 DEBUG  WindowsBackend: windows_username=rahul
06-29 05:39 DEBUG  WindowsBackend: user_full_name=rahul
06-29 05:39 DEBUG  WindowsBackend: user_directory=rahul
06-29 05:39 DEBUG  WindowsBackend: windows_language_code=1033
06-29 05:39 DEBUG  WindowsBackend: windows_language=English
06-29 05:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 05:39 DEBUG  WindowsBackend: bootloader=vista
06-29 05:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62528.8398438 mb free )
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(C: hd 62528.8398438 mb free )
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(D: hd 26283.2226563 mb free ntfs)
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:39 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-29 05:39 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-29 05:39 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-29 05:39 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 05:39 DEBUG  WindowsBackend: keyboard_layout=us
06-29 05:39 DEBUG  WindowsBackend: keyboard_variant=
06-29 05:39 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 05:39 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 05:39 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 05:39 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  CommonBackend: Searching for local CDs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 INFO   root: Already installed, running the uninstaller...
06-29 05:39 INFO   root: Running the uninstaller...
06-29 05:39 INFO   CommonBackend: This is the uninstaller running
06-29 05:39 DEBUG  WindowsFrontend: __init__...
06-29 05:39 DEBUG  WindowsFrontend: on_init...
06-29 05:39 INFO   root: Received settings
06-29 05:39 DEBUG  TaskList: # Running tasklist...
06-29 05:39 DEBUG  TaskList: ## Running Backup ISO...
06-29 05:39 DEBUG  TaskList: ## Finished Backup ISO
06-29 05:39 DEBUG  TaskList: ## Running Remove bootloader entry...
06-29 05:39 DEBUG  WindowsBackend: Could not find bcd id
06-29 05:39 DEBUG  WindowsBackend: undo_bootini C:
06-29 05:39 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 62528.8398438 mb free )
06-29 05:39 DEBUG  WindowsBackend: undo_bootini D:
06-29 05:39 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26283.2226563 mb free ntfs)
06-29 05:39 DEBUG  WindowsBackend: undo_bootini E:
06-29 05:39 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:39 DEBUG  TaskList: ## Finished Remove bootloader entry
06-29 05:39 DEBUG  TaskList: ## Running Remove target dir...
06-29 05:39 DEBUG  CommonBackend: Deleting D:\ubuntu
06-29 05:39 DEBUG  TaskList: ## Finished Remove target dir
06-29 05:39 DEBUG  TaskList: ## Running Remove registry key...
06-29 05:39 DEBUG  TaskList: ## Finished Remove registry key
06-29 05:39 DEBUG  TaskList: # Finished tasklist
06-29 05:39 INFO   root: Almost finished uninstalling
06-29 05:39 INFO   root: Finished uninstallation
06-29 05:39 DEBUG  CommonBackend: Fetching basic info...
06-29 05:39 DEBUG  CommonBackend: original_exe=E:\ubu\wubi.exe
06-29 05:39 DEBUG  CommonBackend: platform=win32
06-29 05:39 DEBUG  CommonBackend: osname=nt
06-29 05:39 DEBUG  CommonBackend: language=en_US
06-29 05:39 DEBUG  CommonBackend: encoding=cp1252
06-29 05:39 DEBUG  WindowsBackend: arch=amd64
06-29 05:39 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\data\isolist.ini
06-29 05:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 05:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 05:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 05:39 DEBUG  WindowsBackend: Fetching host info...
06-29 05:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 05:39 DEBUG  WindowsBackend: windows version=vista
06-29 05:39 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 05:39 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 05:39 DEBUG  WindowsBackend: windows_build=6001
06-29 05:39 DEBUG  WindowsBackend: gmt=-8
06-29 05:39 DEBUG  WindowsBackend: country=US
06-29 05:39 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 05:39 DEBUG  WindowsBackend: windows_username=rahul
06-29 05:39 DEBUG  WindowsBackend: user_full_name=rahul
06-29 05:39 DEBUG  WindowsBackend: user_directory=rahul
06-29 05:39 DEBUG  WindowsBackend: windows_language_code=1033
06-29 05:39 DEBUG  WindowsBackend: windows_language=English
06-29 05:39 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 05:39 DEBUG  WindowsBackend: bootloader=vista
06-29 05:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62528.8359375 mb free )
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(C: hd 62528.8359375 mb free )
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(D: hd 26285.4882813 mb free ntfs)
06-29 05:39 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:39 DEBUG  WindowsBackend: uninstaller_path=None
06-29 05:39 DEBUG  WindowsBackend: previous_target_dir=None
06-29 05:39 DEBUG  WindowsBackend: previous_distro_name=None
06-29 05:39 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 05:39 DEBUG  WindowsBackend: keyboard_layout=us
06-29 05:39 DEBUG  WindowsBackend: keyboard_variant=
06-29 05:39 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 05:39 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 05:39 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 05:39 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:39 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:39 DEBUG  CommonBackend: Searching for local CDs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:39 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:39 INFO   root: Running the installer...
06-29 05:40 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=17000MB, distro_name=Ubuntu, language=English, username=rahul
06-29 05:40 INFO   root: Received settings
06-29 05:40 DEBUG  TaskList: # Running tasklist...
06-29 05:40 DEBUG  TaskList: ## Running select_target_dir...
06-29 05:40 INFO   WindowsBackend: Installing into D:\ubuntu
06-29 05:40 DEBUG  TaskList: ## Finished select_target_dir
06-29 05:40 DEBUG  TaskList: ## Running create_dir_structure...
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
06-29 05:40 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
06-29 05:40 DEBUG  TaskList: ## Finished create_dir_structure
06-29 05:40 DEBUG  TaskList: ## Running uncompress_target_dir...
06-29 05:40 DEBUG  TaskList: ## Finished uncompress_target_dir
06-29 05:40 DEBUG  TaskList: ## Running create_uninstaller...
06-29 05:40 DEBUG  WindowsBackend: Copying uninstaller E:\ubu\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev128
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
06-29 05:40 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
06-29 05:40 DEBUG  TaskList: ## Finished create_uninstaller
06-29 05:40 DEBUG  TaskList: ## Running copy_installation_files...
06-29 05:40 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
06-29 05:40 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\winboot -> D:\ubuntu\winboot
06-29 05:40 DEBUG  WindowsBackend: Copying C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
06-29 05:40 DEBUG  TaskList: ## Finished copy_installation_files
06-29 05:40 DEBUG  TaskList: ## Running get_iso...
06-29 05:40 DEBUG  CommonBackend: Searching for local CD
06-29 05:40 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp is a valid Ubuntu CD
06-29 05:40 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pylF45C.tmp\casper\filesystem.squashfs
06-29 05:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:40 DEBUG  CommonBackend: Searching for local ISO
06-29 05:40 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
06-29 05:40 DEBUG  TaskList: New task get_metalink
06-29 05:40 DEBUG  TaskList: ### Running get_metalink...
06-29 05:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink) > D:\ubuntu\install
06-29 05:40 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-amd64.metalink, basename=ubuntu-9.04-desktop-amd64.metalink, length=19580, text=None
06-29 05:40 DEBUG  downloader: download finished (read 19580 bytes)
06-29 05:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > D:\ubuntu\install
06-29 05:40 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
06-29 05:40 DEBUG  downloader: download finished (read 413 bytes)
06-29 05:40 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
06-29 05:40 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
06-29 05:40 DEBUG  downloader: download finished (read 189 bytes)
06-29 05:40 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
06-29 05:40 INFO   saplog: Checking block bindings..
06-29 05:40 INFO   saplog: Key verified successfully.
06-29 05:40 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

06-29 05:40 DEBUG  TaskList: ### Finished get_metalink
06-29 05:40 DEBUG  TaskList: New task download
06-29 05:40 DEBUG  TaskList: ### Running download...
06-29 05:40 DEBUG  downloader: downloading [http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso](http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso) > D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
06-29 05:40 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso, basename=ubuntu-9.04-desktop-amd64.iso, length=730554368, text=None
06-29 05:44 INFO   WindowsFrontend: Operation cancelled
06-29 05:44 DEBUG  WindowsFrontend: frontend.quit
06-29 05:44 DEBUG  WindowsFrontend: frontend.on_quit
06-29 05:44 DEBUG  WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-29 05:44 DEBUG  TaskList: # Cancelling tasklist
06-29 05:44 DEBUG  WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-29 05:44 DEBUG  root: application.on_quit
06-29 05:44 DEBUG  root: Forceful exit
06-29 05:44 INFO   root: sys.exit
06-29 05:44 INFO   root: === wubi 9.04 rev128 ===
06-29 05:44 DEBUG  root: Logfile is c:\users\rahul\appdata\local\temp\wubi-9.04-rev128.log
06-29 05:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"', '--uninstall']
06-29 05:44 DEBUG  CommonBackend: data_dir=C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\data
06-29 05:44 DEBUG  WindowsBackend: 7z=C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\bin\7z.exe
06-29 05:44 DEBUG  CommonBackend: Fetching basic info...
06-29 05:44 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
06-29 05:44 DEBUG  CommonBackend: platform=win32
06-29 05:44 DEBUG  CommonBackend: osname=nt
06-29 05:44 DEBUG  CommonBackend: language=en_US
06-29 05:44 DEBUG  CommonBackend: encoding=cp1252
06-29 05:44 DEBUG  WindowsBackend: arch=amd64
06-29 05:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\data\isolist.ini
06-29 05:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-29 05:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-29 05:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-29 05:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-29 05:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-29 05:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-29 05:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-29 05:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-29 05:44 DEBUG  WindowsBackend: Fetching host info...
06-29 05:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-29 05:44 DEBUG  WindowsBackend: windows version=vista
06-29 05:44 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Home Basic
06-29 05:44 DEBUG  WindowsBackend: windows_sp=Service Pack 1
06-29 05:44 DEBUG  WindowsBackend: windows_build=6001
06-29 05:44 DEBUG  WindowsBackend: gmt=-8
06-29 05:44 DEBUG  WindowsBackend: country=US
06-29 05:44 DEBUG  WindowsBackend: timezone=America/Los_Angeles
06-29 05:44 DEBUG  WindowsBackend: windows_username=rahul
06-29 05:44 DEBUG  WindowsBackend: user_full_name=rahul
06-29 05:44 DEBUG  WindowsBackend: user_directory=rahul
06-29 05:44 DEBUG  WindowsBackend: windows_language_code=1033
06-29 05:44 DEBUG  WindowsBackend: windows_language=English
06-29 05:44 DEBUG  WindowsBackend: processor_name=Intel(R) Pentium(R) Dual  CPU  T3400  @ 2.16GHz
06-29 05:44 DEBUG  WindowsBackend: bootloader=vista
06-29 05:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 62520.71875 mb free )
06-29 05:44 DEBUG  WindowsBackend: drive=Drive(C: hd 62520.71875 mb free )
06-29 05:44 DEBUG  WindowsBackend: drive=Drive(D: hd 26282.7382813 mb free ntfs)
06-29 05:44 DEBUG  WindowsBackend: drive=Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:44 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
06-29 05:44 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
06-29 05:44 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
06-29 05:44 DEBUG  WindowsBackend: keyboard_id=67699721
06-29 05:44 DEBUG  WindowsBackend: keyboard_layout=us
06-29 05:44 DEBUG  WindowsBackend: keyboard_variant=
06-29 05:44 DEBUG  CommonBackend: locale=en_US.UTF-8
06-29 05:44 DEBUG  WindowsBackend: total_memory_mb=2010.21484375
06-29 05:44 DEBUG  CommonBackend: Searching ISOs on USB devices
06-29 05:44 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Ubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Kubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Xubuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  Distro:   checking Mythbuntu ISO D:\tekken3.iso
06-29 05:44 DEBUG  Distro:     wrong size: 45101952 < 600000000
06-29 05:44 DEBUG  CommonBackend: Searching for local CDs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain C:\Users\rahul\AppData\Local\Temp\pyl8E0C.tmp\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
06-29 05:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
06-29 05:44 INFO   root: Running the uninstaller...
06-29 05:44 INFO   CommonBackend: This is the uninstaller running
06-29 05:44 DEBUG  WindowsFrontend: __init__...
06-29 05:44 DEBUG  WindowsFrontend: on_init...
06-29 05:44 INFO   root: Received settings
06-29 05:44 DEBUG  TaskList: # Running tasklist...
06-29 05:44 DEBUG  TaskList: ## Running Backup ISO...
06-29 05:44 DEBUG  TaskList: ## Finished Backup ISO
06-29 05:44 DEBUG  TaskList: ## Running Remove bootloader entry...
06-29 05:44 DEBUG  WindowsBackend: Could not find bcd id
06-29 05:44 DEBUG  WindowsBackend: undo_bootini C:
06-29 05:44 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 62520.71875 mb free )
06-29 05:44 DEBUG  WindowsBackend: undo_bootini D:
06-29 05:44 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 26282.7382813 mb free ntfs)
06-29 05:44 DEBUG  WindowsBackend: undo_bootini E:
06-29 05:44 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 22023.5234375 mb free ntfs)
06-29 05:44 DEBUG  TaskList: ## Finished Remove bootloader entry
06-29 05:44 DEBUG  TaskList: ## Running Remove target dir...
06-29 05:44 DEBUG  CommonBackend: Deleting D:\ubuntu
06-29 05:44 DEBUG  TaskList: ## Finished Remove target dir
06-29 05:44 DEBUG  TaskList: ## Running Remove registry key...
06-29 05:44 DEBUG  TaskList: ## Finished Remove registry key
06-29 05:44 DEBUG  TaskList: # Finished tasklist
06-29 05:44 INFO   root: Almost finished uninstalling
06-29 05:44 INFO   root: Finished uninstallation
06-29 05:44 DEBUG  root: application.quit
06-29 05:44 DEBUG  WindowsFrontend: frontend.quit
06-29 05:44 DEBUG  WindowsFrontend: frontend.on_quit
06-29 05:44 DEBUG  root: application.on_quit
06-29 05:44 INFO   root: sys.exit

---

### Post by dino99 on 2010-06-29
[http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-10-04-lucid-lynx-with-wubi/](http://www.liberiangeek.net/2010/03/how-to-install-ubuntu-10-04-lucid-lynx-with-wubi/)

**** please, highlight your code above and select WRAP tag ( # above)

---

### Post by bcbc on 2010-06-29
the first time you were running wubi.exe off a d: drive, and it was checking for z:\home\evan\bzr\... which seems broken. Where did you get this wubi.exe?
> 06-29 00:06 DEBUG TaskList: ## Running get_iso...
06-29 00:06 DEBUG TaskList: New task copy_file
06-29 00:06 DEBUG TaskList: ### Running copy_file...
06-29 00:18 DEBUG TaskList: ### Finished copy_file
06-29 00:18 ERROR TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\tasklist.py", line 196, in __call__
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\backends\common\utils.py", line 206, in copy_file
IOError: [Errno 13] Permission denied
06-29 00:18 DEBUG TaskList: # Cancelling tasklist
06-29 00:18 DEBUG TaskList: New task check_iso
06-29 00:18 ERROR root: [Errno 13] Permission denied
Traceback (most recent call last):
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 55, in run
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 125, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 193, in run_cd_menu
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 117, in select_task
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\application.py", line 155, in run_installer
File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\ wubi\frontends\win32\frontend.py", line 137, in run_tasks
IOError: [Errno 13] Permission denied


The second time, wubi.exe determined you needed a 64-bit version of ubuntu and started to download it. Then it seems like you canceled the operation?
> 06-29 05:40 DEBUG downloader: downloading [http://de.archive.ubuntu.com/ubuntu-...ktop-amd64.iso](http://de.archive.ubuntu.com/ubuntu-...ktop-amd64.iso) > D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso
06-29 05:40 DEBUG downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-amd64.iso, url=http://de.archive.ubuntu.com/ubuntu-releases/9.04/ubuntu-9.04-desktop-amd64.iso, basename=ubuntu-9.04-desktop-amd64.iso, length=730554368, text=None
06-29 05:44 INFO WindowsFrontend: Operation cancelled
06-29 05:44 DEBUG WindowsFrontend: frontend.quit
06-29 05:44 DEBUG WindowsFrontend: frontend.on_quit
06-29 05:44 DEBUG WindowsFrontend: stopping remaining background tasks: 'tasklist'
06-29 05:44 DEBUG TaskList: # Cancelling tasklist
06-29 05:44 DEBUG WindowsFrontend: Task cancellation timed out, the program will exit anyway
06-29 05:44 DEBUG root: application.on_quit
06-29 05:44 DEBUG root: Forceful exit

Try the options I gave in the first place, burn and run from CD OR place wubi.exe with the .iso in the same directory and use --skipmd5check as a command line option to wubi.exe

EDIT: you should only issue --skipmd5check if you want to install a different version than the default, e.g. 32 bit instead of 64 bit. In this case, please manually check the md5sum to ensure your copy of ubuntu is legitimate otherwise it's a security risk.

---

