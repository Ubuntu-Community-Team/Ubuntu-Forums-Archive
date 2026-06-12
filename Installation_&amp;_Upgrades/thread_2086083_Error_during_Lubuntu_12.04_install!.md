---
title: "Error during Lubuntu 12.04 install!"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by Ragi1992 on 2012-11-19
The error states: An error occured:
Could not retrieve the required installation files
For more information, please see the log file: C:\docume~1\stetson\locals~1\temp\wubi-12.04-rev269.log

Man I waited around 2 hours for this to install just to hear that!!

The install was suppose to be 17 GB with total of 29 GB in Hard disk.

Specifications:

System:
Windows XP Professional
Version 2002
Service pack 3

Computer:
Intel(R)
Pentium(R) 4 CPU 2.40 GHz
2.39 GHz, 512 MB of RAM

What can I do to fix this? Please help, I'm so tired of Windows!! :(

---

### Post by ibjsb4 on 2012-11-19
Edit: I totally missed the lubuntu

---

### Post by Ragi1992 on 2012-11-19
Does nobody know how to troubleshoot this?

---

### Post by vasa1 on 2012-11-19
Why are you going for wubi ????

---

### Post by bcbc on 2012-11-19
Lubuntu doesn't work with Wubi 12.04 since they released 12.04.1. It downloads the ISO and then tells you it's the wrong release. So if you look in C:\ubuntu\install you might find the ISO it downloaded. That's good - keep it handy, in other words copy it out of that directory because the \ubuntu directory will be deleted if you try to install again.

Then get the wubi.exe for 12.04 (not 12.04.1) from here: [http://old-releases.ubuntu.com/releases/12.04/](http://old-releases.ubuntu.com/releases/12.04/) (at the bottom of the page)

Place them together in the same folder before running and it should install.

---

### Post by JHawk56 on 2012-12-17
> **bcbc said:**
> Lubuntu doesn't work with Wubi 12.04 since they released 12.04.1. It downloads the ISO and then tells you it's the wrong release. So if you look in C:\ubuntu\install you might find the ISO it downloaded. That's good - keep it handy, in other words copy it out of that directory because the \ubuntu directory will be deleted if you try to install again.

Then get the wubi.exe for 12.04 (not 12.04.1) from here: [http://old-releases.ubuntu.com/releases/12.04/](http://old-releases.ubuntu.com/releases/12.04/) (at the bottom of the page)

Place them together in the same folder before running and it should install.
I have the identical problem as the OP. I was attempting to wubi install lubuntu 12.04 to my D: partition. I have a D:\ubuntu\install folder, but it does not contain the iso file, nor is that iso anywhere else on my system. Can I just grab the iso torrent and the correct wubi.exe, then run the wubi.exe? Where should I place those files?

Here's the installation log:

12-17 02:54 INFO   root: === wubi 12.04 rev269 ===
12-17 02:54 DEBUG  root: Logfile is c:\docume~1\john\locals~1\temp\wubi-12.04-rev269.log
12-17 02:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\John\\Local Settings\\Application Data\\Opera\\Opera\\temporary_downloads\\wubi.exe"']
12-17 02:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\data
12-17 02:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\bin\7z.exe
12-17 02:54 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-17 02:54 DEBUG  CommonBackend: Fetching basic info...
12-17 02:54 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\John\Local Settings\Application Data\Opera\Opera\temporary_downloads\wubi.exe
12-17 02:54 DEBUG  CommonBackend: platform=win32
12-17 02:54 DEBUG  CommonBackend: osname=nt
12-17 02:54 DEBUG  CommonBackend: language=en_US
12-17 02:54 DEBUG  CommonBackend: encoding=cp1252
12-17 02:54 DEBUG  WindowsBackend: arch=i386
12-17 02:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\data\isolist.ini
12-17 02:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 02:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 02:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-17 02:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 02:54 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 02:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 02:54 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-17 02:54 DEBUG  WindowsBackend: Fetching host info...
12-17 02:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 02:54 DEBUG  WindowsBackend: windows version=xp
12-17 02:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-17 02:54 DEBUG  WindowsBackend: windows_sp=Service Pack 2
12-17 02:54 DEBUG  WindowsBackend: windows_build=2600
12-17 02:54 DEBUG  WindowsBackend: gmt=-6
12-17 02:54 DEBUG  WindowsBackend: country=US
12-17 02:54 DEBUG  WindowsBackend: timezone=America/Chicago
12-17 02:54 DEBUG  WindowsBackend: windows_username=John
12-17 02:54 DEBUG  WindowsBackend: user_full_name=John
12-17 02:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\John
12-17 02:54 DEBUG  WindowsBackend: windows_language_code=1033
12-17 02:54 DEBUG  WindowsBackend: windows_language=English
12-17 02:54 DEBUG  WindowsBackend: processor_name=mobile AMD Athlon(tm) XP 2200+
12-17 02:54 DEBUG  WindowsBackend: bootloader=xp
12-17 02:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 678.76953125 mb free ntfs)
12-17 02:54 DEBUG  WindowsBackend: drive=Drive(C: hd 678.76953125 mb free ntfs)
12-17 02:54 DEBUG  WindowsBackend: drive=Drive(D: hd 16785.4335938 mb free ntfs)
12-17 02:54 DEBUG  WindowsBackend: drive=Drive(E: hd 524.328125 mb free ntfs)
12-17 02:54 DEBUG  WindowsBackend: drive=Drive(F: hd 2024.78515625 mb free ntfs)
12-17 02:54 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 02:54 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-17 02:54 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-17 02:54 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-17 02:54 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 02:54 DEBUG  WindowsBackend: keyboard_layout=us
12-17 02:54 DEBUG  WindowsBackend: keyboard_variant=
12-17 02:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 02:54 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 02:54 DEBUG  WindowsBackend: total_memory_mb=511.484375
12-17 02:54 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 02:54 DEBUG  CommonBackend: Searching for local CDs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylC3.tmp\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
12-17 02:54 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:54 INFO   root: Already installed, running the uninstaller...
12-17 02:54 INFO   root: Running the uninstaller...
12-17 02:54 INFO   CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
12-17 02:54 DEBUG  root: application.quit
12-17 02:54 DEBUG  root: application.on_quit
12-17 02:54 INFO   root: sys.exit
12-17 02:54 INFO   root: Quitting application
12-17 02:56 INFO   root: === wubi 12.04 rev269 ===
12-17 02:56 DEBUG  root: Logfile is c:\docume~1\john\locals~1\temp\wubi-12.04-rev269.log
12-17 02:56 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\John\\Local Settings\\Application Data\\Opera\\Opera\\temporary_downloads\\wubi (1).exe"']
12-17 02:56 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\data
12-17 02:56 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\bin\7z.exe
12-17 02:56 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
12-17 02:56 DEBUG  CommonBackend: Fetching basic info...
12-17 02:56 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\John\Local Settings\Application Data\Opera\Opera\temporary_downloads\wubi (1).exe
12-17 02:56 DEBUG  CommonBackend: platform=win32
12-17 02:56 DEBUG  CommonBackend: osname=nt
12-17 02:56 DEBUG  CommonBackend: language=en_US
12-17 02:56 DEBUG  CommonBackend: encoding=cp1252
12-17 02:56 DEBUG  WindowsBackend: arch=i386
12-17 02:56 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\data\isolist.ini
12-17 02:56 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Edubuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-17 02:56 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-17 02:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Edubuntu-amd64
12-17 02:56 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-17 02:56 DEBUG  CommonBackend:   Adding distro Lubuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-17 02:56 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-17 02:56 DEBUG  CommonBackend:   Adding distro Lubuntu-amd64
12-17 02:56 DEBUG  WindowsBackend: Fetching host info...
12-17 02:56 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-17 02:56 DEBUG  WindowsBackend: windows version=xp
12-17 02:56 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
12-17 02:56 DEBUG  WindowsBackend: windows_sp=Service Pack 2
12-17 02:56 DEBUG  WindowsBackend: windows_build=2600
12-17 02:56 DEBUG  WindowsBackend: gmt=-6
12-17 02:56 DEBUG  WindowsBackend: country=US
12-17 02:56 DEBUG  WindowsBackend: timezone=America/Chicago
12-17 02:56 DEBUG  WindowsBackend: windows_username=John
12-17 02:56 DEBUG  WindowsBackend: user_full_name=John
12-17 02:56 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\John
12-17 02:56 DEBUG  WindowsBackend: windows_language_code=1033
12-17 02:56 DEBUG  WindowsBackend: windows_language=English
12-17 02:56 DEBUG  WindowsBackend: processor_name=mobile AMD Athlon(tm) XP 2200+
12-17 02:56 DEBUG  WindowsBackend: bootloader=xp
12-17 02:56 DEBUG  WindowsBackend: system_drive=Drive(C: hd 676.55859375 mb free ntfs)
12-17 02:56 DEBUG  WindowsBackend: drive=Drive(C: hd 676.55859375 mb free ntfs)
12-17 02:56 DEBUG  WindowsBackend: drive=Drive(D: hd 19977.9570313 mb free ntfs)
12-17 02:56 DEBUG  WindowsBackend: drive=Drive(E: hd 524.45703125 mb free ntfs)
12-17 02:56 DEBUG  WindowsBackend: drive=Drive(F: hd 2024.91210938 mb free ntfs)
12-17 02:56 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
12-17 02:56 DEBUG  WindowsBackend: uninstaller_path=None
12-17 02:56 DEBUG  WindowsBackend: previous_target_dir=None
12-17 02:56 DEBUG  WindowsBackend: previous_distro_name=None
12-17 02:56 DEBUG  WindowsBackend: keyboard_id=67699721
12-17 02:56 DEBUG  WindowsBackend: keyboard_layout=us
12-17 02:56 DEBUG  WindowsBackend: keyboard_variant=
12-17 02:56 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
12-17 02:56 DEBUG  CommonBackend: locale=en_US.UTF-8
12-17 02:56 DEBUG  WindowsBackend: total_memory_mb=511.484375
12-17 02:56 DEBUG  CommonBackend: Searching ISOs on USB devices
12-17 02:56 DEBUG  CommonBackend: Searching for local CDs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Edubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
12-17 02:56 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:56 INFO   root: Running the installer...
12-17 02:56 DEBUG  WindowsFrontend: __init__...
12-17 02:56 DEBUG  WindowsFrontend: on_init...
12-17 02:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\translations, languages=['en_US', 'en']
12-17 02:56 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\translations, languages=['en_US', 'en']
12-17 02:57 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=12000MB, distro_name=Lubuntu, language=en_US, locale=en_US.UTF-8, username=john
12-17 02:57 INFO   root: Received settings
12-17 02:57 DEBUG  CommonBackend: Searching for local CD
12-17 02:57 DEBUG  Distro:   checking whether C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp is a valid Lubuntu CD
12-17 02:57 DEBUG  Distro:     does not contain C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\casper\filesystem.squashfs
12-17 02:57 DEBUG  Distro:   checking whether D:\ is a valid Lubuntu CD
12-17 02:57 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-17 02:57 DEBUG  Distro:   checking whether E:\ is a valid Lubuntu CD
12-17 02:57 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-17 02:57 DEBUG  Distro:   checking whether F:\ is a valid Lubuntu CD
12-17 02:57 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-17 02:57 DEBUG  Distro:   checking whether G:\ is a valid Lubuntu CD
12-17 02:57 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
12-17 02:57 DEBUG  CommonBackend: Searching for local ISO
12-17 02:57 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\translations, languages=['en_US', 'en']
12-17 02:57 DEBUG  TaskList: # Running tasklist...
12-17 02:57 DEBUG  TaskList: ## Running select_target_dir...
12-17 02:57 INFO   WindowsBackend: Installing into D:\ubuntu
12-17 02:57 DEBUG  TaskList: ## Finished select_target_dir
12-17 02:57 DEBUG  TaskList: ## Running create_dir_structure...
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-17 02:57 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-17 02:57 DEBUG  TaskList: ## Finished create_dir_structure
12-17 02:57 DEBUG  TaskList: ## Running uncompress_target_dir...
12-17 02:57 DEBUG  TaskList: ## Finished uncompress_target_dir
12-17 02:57 DEBUG  TaskList: ## Running create_uninstaller...
12-17 02:57 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\John\Local Settings\Application Data\Opera\Opera\temporary_downloads\wubi (1).exe -> D:\ubuntu\uninstall-wubi.exe
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Lubuntu
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Lubuntu.ico
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 12.04-rev269
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Lubuntu
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://lubuntu.net](http://lubuntu.net)
12-17 02:57 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-17 02:57 DEBUG  TaskList: ## Finished create_uninstaller
12-17 02:57 DEBUG  TaskList: ## Running copy_installation_files...
12-17 02:57 DEBUG  WindowsBackend: Copying C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-17 02:57 DEBUG  WindowsBackend: Copying C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\winboot -> D:\ubuntu\winboot
12-17 02:57 DEBUG  WindowsBackend: Copying C:\DOCUME~1\John\LOCALS~1\Temp\pylCB.tmp\data\images\Lubuntu.ico -> D:\ubuntu\Lubuntu.ico
12-17 02:57 DEBUG  TaskList: ## Finished copy_installation_files
12-17 02:57 DEBUG  TaskList: ## Running get_iso...
12-17 02:57 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-17 02:57 DEBUG  TaskList: New task get_metalink
12-17 02:57 DEBUG  TaskList: ### Running get_metalink...
12-17 02:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink) > D:\ubuntu\install
12-17 02:57 DEBUG  downloader: Download start filename=D:\ubuntu\install\lubuntu-12.04-desktop-i386.metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.metalink, basename=lubuntu-12.04-desktop-i386.metalink, length=1037, text=None
12-17 02:57 DEBUG  downloader: download finished (read 1037 bytes)
12-17 02:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink) > D:\ubuntu\install
12-17 02:57 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=586, text=None
12-17 02:57 DEBUG  downloader: download finished (read 586 bytes)
12-17 02:57 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg) > D:\ubuntu\install
12-17 02:57 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=198, text=None
12-17 02:57 DEBUG  downloader: download finished (read 198 bytes)
12-17 02:57 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-17 02:57 INFO   saplog: Checking block bindings..
12-17 02:57 INFO   saplog: Key verified successfully.
12-17 02:57 DEBUG  CommonBackend: metalink md5sums:
60979d07b6355e829b4468b29de1a40e  lubuntu-12.04-alternate-amd64+mac.metalink
9b28d0044548685aa6a44d7ff535dae9  lubuntu-12.04-alternate-amd64.metalink
1cdd6d6e020ea49496d90e490f2dedae  lubuntu-12.04-alternate-i386.metalink
1dc9aac7ea1b0b5f59818a6f0c7a3ff1  lubuntu-12.04-alternate-powerpc.metalink
c330d7adc56433a7625a604a92bd13f9  lubuntu-12.04-desktop-amd64+mac.metalink
6d31cbcbd249d1b5cfabc79a99058cc3  lubuntu-12.04-desktop-amd64.metalink
5051a1b9d698a5393f499908478ddae1  lubuntu-12.04-desktop-i386.metalink
a2aeb48a97620a0acd78ea260e5f4534  lubuntu-12.04-desktop-powerpc.metalink

12-17 02:57 DEBUG  TaskList: ### Finished get_metalink
12-17 02:57 DEBUG  TaskList: New task download
12-17 02:57 DEBUG  TaskList: ### Running download...
12-17 02:57 DEBUG  btdownloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent) > D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 03:29 DEBUG  TaskList: ### Finished download
12-17 03:29 DEBUG  TaskList: New task check_iso
12-17 03:29 DEBUG  TaskList: ### Running check_iso...
12-17 03:29 DEBUG  CommonBackend: Checking D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 03:29 DEBUG  Distro:   checking Lubuntu ISO D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 03:29 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 03:29 DEBUG  Distro:   parsing info from str=Lubuntu 12.04 "Precise Pangolin" - Release i386 (20120423)
12-17 03:29 DEBUG  Distro:   parsed info={'name': 'Lubuntu', 'subversion': 'Release', 'version': '12.04', 'build': '20120423', 'codename': 'Precise Pangolin', 'arch': 'i386'}
12-17 03:29 DEBUG  Distro: wrong version: 12.04 != 12.04.1
12-17 03:29 DEBUG  TaskList: ### Finished check_iso
12-17 03:29 DEBUG  TaskList: New task download
12-17 03:29 DEBUG  TaskList: ### Running download...
12-17 03:29 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso) > D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 03:29 DEBUG  downloader: Download start filename=D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso, url=http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso, basename=lubuntu-12.04-desktop-i386.iso, length=721727488, text=None
12-17 06:00 DEBUG  TaskList: ### Finished download
12-17 06:00 DEBUG  downloader: download finished (read 721727488 bytes)
12-17 06:00 DEBUG  TaskList: New task check_iso
12-17 06:00 DEBUG  TaskList: ### Running check_iso...
12-17 06:00 DEBUG  CommonBackend: Checking D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 06:00 DEBUG  Distro:   checking Lubuntu ISO D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 06:00 DEBUG  Distro: wrong version: 12.04 != 12.04.1
12-17 06:00 DEBUG  TaskList: ### Finished check_iso
12-17 06:00 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-17 06:00 DEBUG  TaskList: # Cancelling tasklist
12-17 06:00 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-17 06:00 DEBUG  TaskList: # Finished tasklist

---

### Post by bcbc on 2012-12-17
> **JHawk56 said:**
> I have the identical problem as the OP. I was attempting to wubi install lubuntu 12.04 to my D: partition. I have a D:\ubuntu\install folder, but it does not contain the iso file, nor is that iso anywhere else on my system. Can I just grab the iso torrent and the correct wubi.exe, then run the wubi.exe? Where should I place those files?

Here's the installation log:

...
12-17 06:00 DEBUG  TaskList: ### Running check_iso...
12-17 06:00 DEBUG  CommonBackend: Checking D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 06:00 DEBUG  Distro:   checking Lubuntu ISO D:\ubuntu\install\lubuntu-12.04-desktop-i386.iso
12-17 06:00 DEBUG  Distro: wrong version: 12.04 != 12.04.1
12-17 06:00 DEBUG  TaskList: ### Finished check_iso
12-17 06:00 ERROR  TaskList: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-17 06:00 DEBUG  TaskList: # Cancelling tasklist
12-17 06:00 ERROR  root: Could not retrieve the required installation files
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 600, in get_iso
Exception: Could not retrieve the required installation files
12-17 06:00 DEBUG  TaskList: # Finished tasklist

That's unfortunate if Wubi is cleaning up the ISO on the way out. It should still be undeletable if you have software that can do that for you. But otherwise, you will just have to download it again.

Yes, you can download the 12.04 ISO via torrent and then the correct (12.04) Wubi.exe, place them in the same folder, and then run wubi.exe.

---

### Post by JHawk56 on 2012-12-17
> **bcbc said:**
> Yes, you can download the 12.04 ISO via torrent and then the correct (12.04) Wubi.exe, place them in the same folder, and then run wubi.exe.
Thanks. The installation bombed, but it appears to be a totally different issue now, so I'll research the forums and perhaps start a new thread.

---

