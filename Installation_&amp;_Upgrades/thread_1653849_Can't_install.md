---
title: "Can't install"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by Snoopy2005uk on 2010-12-27
Hi, I am totally new to all of this. 

I downloaded the latest stable version of Ubuntu and I am trying to install it along with windows 7. 

It gets so far into the installation and pops up saying it doesnt have permission. I also tried by booting from the CD and have the same issue.

[IMG]http://i127.photobucket.com/albums/p157/Snoopy2005uk/Temp/error.jpg[/IMG]

Any ideas?

---

### Post by XeonBloomfield on 2010-12-27
What is shown as error when you try to install it by booting from CD?

Can you paste here content of log file? :
```
c:\users\ian\appdata\local\temp\**wubi-10.10-rev197.log**
```

---

### Post by Snoopy2005uk on 2010-12-27
Can't remember the exact message but it was coming up when I was telling it which hard drive to install too.

> 12-27 16:44 INFO   root: === wubi 10.10 rev197 ===
12-27 16:44 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 16:44 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 16:44 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\data
12-27 16:44 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\bin\7z.exe
12-27 16:44 DEBUG  CommonBackend: Fetching basic info...
12-27 16:44 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 16:44 DEBUG  CommonBackend: platform=win32
12-27 16:44 DEBUG  CommonBackend: osname=nt
12-27 16:44 DEBUG  CommonBackend: language=en_GB
12-27 16:44 DEBUG  CommonBackend: encoding=cp1252
12-27 16:44 DEBUG  WindowsBackend: arch=amd64
12-27 16:44 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\data\isolist.ini
12-27 16:44 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 16:44 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 16:44 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 16:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 16:44 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 16:44 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 16:44 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 16:44 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 16:44 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 16:44 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 16:44 DEBUG  WindowsBackend: Fetching host info...
12-27 16:44 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 16:44 DEBUG  WindowsBackend: windows version=vista
12-27 16:44 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 16:44 DEBUG  WindowsBackend: windows_sp=None
12-27 16:44 DEBUG  WindowsBackend: windows_build=7600
12-27 16:44 DEBUG  WindowsBackend: gmt=0
12-27 16:44 DEBUG  WindowsBackend: country=GB
12-27 16:44 DEBUG  WindowsBackend: timezone=Europe/London
12-27 16:44 DEBUG  WindowsBackend: windows_username=Ian
12-27 16:44 DEBUG  WindowsBackend: user_full_name=Ian
12-27 16:44 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 16:44 DEBUG  WindowsBackend: windows_language_code=1033
12-27 16:44 DEBUG  WindowsBackend: windows_language=English
12-27 16:44 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 16:44 DEBUG  WindowsBackend: bootloader=vista
12-27 16:44 DEBUG  WindowsBackend: system_drive=Drive(C: hd 7976.51953125 mb free ntfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(C: hd 7976.51953125 mb free ntfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(E: hd 238166.007813 mb free ntfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 16:44 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 16:44 DEBUG  WindowsBackend: uninstaller_path=None
12-27 16:44 DEBUG  WindowsBackend: previous_target_dir=None
12-27 16:44 DEBUG  WindowsBackend: previous_distro_name=None
12-27 16:44 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 16:44 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 16:44 DEBUG  WindowsBackend: keyboard_variant=
12-27 16:44 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 16:44 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 16:44 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 16:44 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 16:44 DEBUG  CommonBackend: Searching for local CDs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Ubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Kubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 16:44 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 16:44 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 16:44 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 16:44 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 16:44 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 16:44 INFO   root: Running the CD menu...
12-27 16:44 DEBUG  WindowsFrontend: __init__...
12-27 16:44 DEBUG  WindowsFrontend: on_init...
12-27 16:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\translations, languages=['en_GB', 'en']
12-27 16:44 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl6384.tmp\translations, languages=['en_GB', 'en']
12-27 16:45 DEBUG  root: application.quit
12-27 16:45 DEBUG  WindowsFrontend: frontend.quit
12-27 16:45 DEBUG  WindowsFrontend: frontend.on_quit
12-27 16:45 DEBUG  root: application.on_quit
12-27 16:45 INFO   root: sys.exit
12-27 17:27 INFO   root: === wubi 10.10 rev197 ===
12-27 17:27 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 17:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 17:27 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\data
12-27 17:27 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\bin\7z.exe
12-27 17:27 DEBUG  CommonBackend: Fetching basic info...
12-27 17:27 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:27 DEBUG  CommonBackend: platform=win32
12-27 17:27 DEBUG  CommonBackend: osname=nt
12-27 17:27 DEBUG  CommonBackend: language=en_GB
12-27 17:27 DEBUG  CommonBackend: encoding=cp1252
12-27 17:27 DEBUG  WindowsBackend: arch=amd64
12-27 17:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\data\isolist.ini
12-27 17:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:27 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:27 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:27 DEBUG  WindowsBackend: Fetching host info...
12-27 17:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:27 DEBUG  WindowsBackend: windows version=vista
12-27 17:27 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:27 DEBUG  WindowsBackend: windows_sp=None
12-27 17:27 DEBUG  WindowsBackend: windows_build=7600
12-27 17:27 DEBUG  WindowsBackend: gmt=0
12-27 17:27 DEBUG  WindowsBackend: country=GB
12-27 17:27 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:27 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:27 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:27 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:27 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:27 DEBUG  WindowsBackend: windows_language=English
12-27 17:27 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:27 DEBUG  WindowsBackend: bootloader=vista
12-27 17:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8022.8671875 mb free ntfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(C: hd 8022.8671875 mb free ntfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(E: hd 238162.257813 mb free ntfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:27 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:27 DEBUG  WindowsBackend: uninstaller_path=None
12-27 17:27 DEBUG  WindowsBackend: previous_target_dir=None
12-27 17:27 DEBUG  WindowsBackend: previous_distro_name=None
12-27 17:27 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:27 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:27 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:27 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 17:27 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 17:27 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:27 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:27 DEBUG  CommonBackend: Searching for local CDs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Ubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Kubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:27 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:27 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:27 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 17:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 17:27 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:27 INFO   root: Running the CD menu...
12-27 17:27 DEBUG  WindowsFrontend: __init__...
12-27 17:27 DEBUG  WindowsFrontend: on_init...
12-27 17:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\translations, languages=['en_GB', 'en']
12-27 17:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\translations, languages=['en_GB', 'en']
12-27 17:27 INFO   root: CD menu finished
12-27 17:27 INFO   root: Running the installer...
12-27 17:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\translations, languages=['en_GB', 'en']
12-27 17:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\translations, languages=['en_GB', 'en']
12-27 17:27 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=ian
12-27 17:27 INFO   root: Received settings
12-27 17:27 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\translations, languages=['en_GB', 'en']
12-27 17:27 DEBUG  TaskList: # Running tasklist...
12-27 17:27 DEBUG  TaskList: ## Running select_target_dir...
12-27 17:27 INFO   WindowsBackend: Installing into D:\ubuntu
12-27 17:27 DEBUG  TaskList: ## Finished select_target_dir
12-27 17:27 DEBUG  TaskList: ## Running create_dir_structure...
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-27 17:27 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-27 17:27 DEBUG  TaskList: ## Finished create_dir_structure
12-27 17:27 DEBUG  TaskList: ## Running uncompress_target_dir...
12-27 17:27 DEBUG  TaskList: ## Finished uncompress_target_dir
12-27 17:27 DEBUG  TaskList: ## Running create_uninstaller...
12-27 17:27 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-27 17:27 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-27 17:27 DEBUG  TaskList: ## Finished create_uninstaller
12-27 17:27 DEBUG  TaskList: ## Running copy_installation_files...
12-27 17:27 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-27 17:27 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\winboot -> D:\ubuntu\winboot
12-27 17:27 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylA38E.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
12-27 17:27 DEBUG  TaskList: ## Finished copy_installation_files
12-27 17:27 DEBUG  TaskList: ## Running get_iso...
12-27 17:27 DEBUG  TaskList: New task copy_file
12-27 17:27 DEBUG  TaskList: ### Running copy_file...
12-27 17:30 DEBUG  TaskList: ### Finished copy_file
12-27 17:30 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:30 DEBUG  TaskList: # Cancelling tasklist
12-27 17:30 DEBUG  TaskList: New task check_iso
12-27 17:30 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:30 DEBUG  CommonBackend: Searching for local ISO
12-27 17:30 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-27 17:30 DEBUG  TaskList: New task get_metalink
12-27 17:30 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-27 17:30 DEBUG  TaskList: # Cancelling tasklist
12-27 17:30 DEBUG  TaskList: # Finished tasklist
12-27 17:31 INFO   root: === wubi 10.10 rev197 ===
12-27 17:31 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 17:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 17:31 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\data
12-27 17:31 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\bin\7z.exe
12-27 17:31 DEBUG  CommonBackend: Fetching basic info...
12-27 17:31 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:31 DEBUG  CommonBackend: platform=win32
12-27 17:31 DEBUG  CommonBackend: osname=nt
12-27 17:31 DEBUG  CommonBackend: language=en_GB
12-27 17:31 DEBUG  CommonBackend: encoding=cp1252
12-27 17:31 DEBUG  WindowsBackend: arch=amd64
12-27 17:31 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\data\isolist.ini
12-27 17:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:31 DEBUG  WindowsBackend: Fetching host info...
12-27 17:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:31 DEBUG  WindowsBackend: windows version=vista
12-27 17:31 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:31 DEBUG  WindowsBackend: windows_sp=None
12-27 17:31 DEBUG  WindowsBackend: windows_build=7600
12-27 17:31 DEBUG  WindowsBackend: gmt=0
12-27 17:31 DEBUG  WindowsBackend: country=GB
12-27 17:31 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:31 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:31 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:31 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:31 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:31 DEBUG  WindowsBackend: windows_language=English
12-27 17:31 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:31 DEBUG  WindowsBackend: bootloader=vista
12-27 17:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8030.734375 mb free ntfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(C: hd 8030.734375 mb free ntfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(D: hd 37245.8945313 mb free ntfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(E: hd 238155.132813 mb free ntfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:31 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:31 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-27 17:31 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-27 17:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-27 17:31 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:31 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:31 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:31 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 17:31 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 17:31 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:31 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:31 DEBUG  CommonBackend: Searching for local CDs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Ubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Kubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:31 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 17:31 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 17:31 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:31 INFO   root: Running the CD menu...
12-27 17:31 DEBUG  WindowsFrontend: __init__...
12-27 17:31 DEBUG  WindowsFrontend: on_init...
12-27 17:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_GB', 'en']
12-27 17:31 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl70BC.tmp\translations, languages=['en_GB', 'en']
12-27 17:31 INFO   WindowsFrontend: Operation cancelled
12-27 17:31 DEBUG  WindowsFrontend: frontend.quit
12-27 17:31 DEBUG  WindowsFrontend: frontend.on_quit
12-27 17:31 DEBUG  root: application.on_quit
12-27 17:31 INFO   root: sys.exit
12-27 17:32 INFO   root: === wubi 10.10 rev197 ===
12-27 17:32 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 17:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 17:32 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\data
12-27 17:32 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\bin\7z.exe
12-27 17:32 DEBUG  CommonBackend: Fetching basic info...
12-27 17:32 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:32 DEBUG  CommonBackend: platform=win32
12-27 17:32 DEBUG  CommonBackend: osname=nt
12-27 17:32 DEBUG  CommonBackend: language=en_GB
12-27 17:32 DEBUG  CommonBackend: encoding=cp1252
12-27 17:32 DEBUG  WindowsBackend: arch=amd64
12-27 17:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\data\isolist.ini
12-27 17:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:32 DEBUG  WindowsBackend: Fetching host info...
12-27 17:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:32 DEBUG  WindowsBackend: windows version=vista
12-27 17:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:32 DEBUG  WindowsBackend: windows_sp=None
12-27 17:32 DEBUG  WindowsBackend: windows_build=7600
12-27 17:32 DEBUG  WindowsBackend: gmt=0
12-27 17:32 DEBUG  WindowsBackend: country=GB
12-27 17:32 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:32 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:32 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:32 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:32 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:32 DEBUG  WindowsBackend: windows_language=English
12-27 17:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:32 DEBUG  WindowsBackend: bootloader=vista
12-27 17:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8028.0546875 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(C: hd 8028.0546875 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(D: hd 37245.8945313 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(E: hd 238153.820313 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:32 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-27 17:32 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-27 17:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-27 17:32 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:32 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:32 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:32 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 17:32 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 17:32 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:32 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:32 DEBUG  CommonBackend: Searching for local CDs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 17:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 17:32 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:32 INFO   root: Running the CD menu...
12-27 17:32 DEBUG  WindowsFrontend: __init__...
12-27 17:32 DEBUG  WindowsFrontend: on_init...
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:32 INFO   root: CD menu finished
12-27 17:32 INFO   root: Already installed, running the uninstaller...
12-27 17:32 INFO   root: Running the uninstaller...
12-27 17:32 INFO   CommonBackend: This is the uninstaller running
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:32 INFO   root: Received settings
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:32 DEBUG  TaskList: # Running tasklist...
12-27 17:32 DEBUG  TaskList: ## Running Backup ISO...
12-27 17:32 DEBUG  TaskList: ## Finished Backup ISO
12-27 17:32 DEBUG  TaskList: ## Running Remove bootloader entry....
12-27 17:32 DEBUG  WindowsBackend: Could not find bcd id
12-27 17:32 DEBUG  WindowsBackend: undo_bootini C:
12-27 17:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8028.0546875 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: undo_bootini D:
12-27 17:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 37245.8945313 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: undo_bootini E:
12-27 17:32 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 238153.820313 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: undo_bootini F:
12-27 17:32 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:32 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-27 17:32 DEBUG  TaskList: ## Running Remove target dir....
12-27 17:32 DEBUG  CommonBackend: Deleting D:\ubuntu
12-27 17:32 DEBUG  TaskList: ## Finished Remove target dir.
12-27 17:32 DEBUG  TaskList: ## Running Remove registry key....
12-27 17:32 DEBUG  TaskList: ## Finished Remove registry key.
12-27 17:32 DEBUG  TaskList: # Finished tasklist
12-27 17:32 INFO   root: Almost finished uninstalling
12-27 17:32 INFO   root: Finished uninstallation
12-27 17:32 DEBUG  CommonBackend: Fetching basic info...
12-27 17:32 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:32 DEBUG  CommonBackend: platform=win32
12-27 17:32 DEBUG  CommonBackend: osname=nt
12-27 17:32 DEBUG  WindowsBackend: arch=amd64
12-27 17:32 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\data\isolist.ini
12-27 17:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:32 DEBUG  WindowsBackend: Fetching host info...
12-27 17:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:32 DEBUG  WindowsBackend: windows version=vista
12-27 17:32 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:32 DEBUG  WindowsBackend: windows_sp=None
12-27 17:32 DEBUG  WindowsBackend: windows_build=7600
12-27 17:32 DEBUG  WindowsBackend: gmt=0
12-27 17:32 DEBUG  WindowsBackend: country=GB
12-27 17:32 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:32 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:32 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:32 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:32 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:32 DEBUG  WindowsBackend: windows_language=English
12-27 17:32 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:32 DEBUG  WindowsBackend: bootloader=vista
12-27 17:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8029.0390625 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(C: hd 8029.0390625 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(E: hd 238153.070313 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:32 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:32 DEBUG  WindowsBackend: uninstaller_path=None
12-27 17:32 DEBUG  WindowsBackend: previous_target_dir=None
12-27 17:32 DEBUG  WindowsBackend: previous_distro_name=None
12-27 17:32 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:32 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:32 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:32 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:32 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:32 DEBUG  CommonBackend: Searching for local CDs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:32 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:32 INFO   root: Running the installer...
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:32 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:33 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=ian
12-27 17:33 INFO   root: Received settings
12-27 17:33 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\translations, languages=['en_GB', 'en']
12-27 17:33 DEBUG  TaskList: # Running tasklist...
12-27 17:33 DEBUG  TaskList: ## Running select_target_dir...
12-27 17:33 INFO   WindowsBackend: Installing into D:\ubuntu
12-27 17:33 DEBUG  TaskList: ## Finished select_target_dir
12-27 17:33 DEBUG  TaskList: ## Running create_dir_structure...
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
12-27 17:33 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
12-27 17:33 DEBUG  TaskList: ## Finished create_dir_structure
12-27 17:33 DEBUG  TaskList: ## Running uncompress_target_dir...
12-27 17:33 DEBUG  TaskList: ## Finished uncompress_target_dir
12-27 17:33 DEBUG  TaskList: ## Running create_uninstaller...
12-27 17:33 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-27 17:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-27 17:33 DEBUG  TaskList: ## Finished create_uninstaller
12-27 17:33 DEBUG  TaskList: ## Running copy_installation_files...
12-27 17:33 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
12-27 17:33 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\winboot -> D:\ubuntu\winboot
12-27 17:33 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl1045.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
12-27 17:33 DEBUG  TaskList: ## Finished copy_installation_files
12-27 17:33 DEBUG  TaskList: ## Running get_iso...
12-27 17:33 DEBUG  TaskList: New task copy_file
12-27 17:33 DEBUG  TaskList: ### Running copy_file...
12-27 17:35 DEBUG  TaskList: ### Finished copy_file
12-27 17:35 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:35 DEBUG  TaskList: # Cancelling tasklist
12-27 17:35 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:35 DEBUG  TaskList: New task check_iso
12-27 17:35 DEBUG  CommonBackend: Searching for local ISO
12-27 17:35 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-27 17:35 DEBUG  TaskList: New task get_metalink
12-27 17:35 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-27 17:35 DEBUG  TaskList: # Cancelling tasklist
12-27 17:35 DEBUG  TaskList: # Finished tasklist
12-27 17:36 INFO   root: === wubi 10.10 rev197 ===
12-27 17:36 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 17:36 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 17:36 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\data
12-27 17:36 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\bin\7z.exe
12-27 17:36 DEBUG  CommonBackend: Fetching basic info...
12-27 17:36 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:36 DEBUG  CommonBackend: platform=win32
12-27 17:36 DEBUG  CommonBackend: osname=nt
12-27 17:36 DEBUG  CommonBackend: language=en_GB
12-27 17:36 DEBUG  CommonBackend: encoding=cp1252
12-27 17:36 DEBUG  WindowsBackend: arch=amd64
12-27 17:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\data\isolist.ini
12-27 17:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:36 DEBUG  WindowsBackend: Fetching host info...
12-27 17:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:36 DEBUG  WindowsBackend: windows version=vista
12-27 17:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:36 DEBUG  WindowsBackend: windows_sp=None
12-27 17:36 DEBUG  WindowsBackend: windows_build=7600
12-27 17:36 DEBUG  WindowsBackend: gmt=0
12-27 17:36 DEBUG  WindowsBackend: country=GB
12-27 17:36 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:36 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:36 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:36 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:36 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:36 DEBUG  WindowsBackend: windows_language=English
12-27 17:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:36 DEBUG  WindowsBackend: bootloader=vista
12-27 17:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8029.20703125 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(C: hd 8029.20703125 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(D: hd 37245.8945313 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(E: hd 238144.195313 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:36 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
12-27 17:36 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
12-27 17:36 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-27 17:36 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:36 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:36 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:36 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 17:36 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 17:36 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:36 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:36 DEBUG  CommonBackend: Searching for local CDs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 17:36 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 17:36 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:36 INFO   root: Running the CD menu...
12-27 17:36 DEBUG  WindowsFrontend: __init__...
12-27 17:36 DEBUG  WindowsFrontend: on_init...
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:36 INFO   root: CD menu finished
12-27 17:36 INFO   root: Already installed, running the uninstaller...
12-27 17:36 INFO   root: Running the uninstaller...
12-27 17:36 INFO   CommonBackend: This is the uninstaller running
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:36 INFO   root: Received settings
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:36 DEBUG  TaskList: # Running tasklist...
12-27 17:36 DEBUG  TaskList: ## Running Backup ISO...
12-27 17:36 DEBUG  TaskList: ## Finished Backup ISO
12-27 17:36 DEBUG  TaskList: ## Running Remove bootloader entry....
12-27 17:36 DEBUG  WindowsBackend: Could not find bcd id
12-27 17:36 DEBUG  WindowsBackend: undo_bootini C:
12-27 17:36 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8029.20703125 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: undo_bootini D:
12-27 17:36 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 37245.8945313 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: undo_bootini E:
12-27 17:36 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 238144.195313 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: undo_bootini F:
12-27 17:36 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:36 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-27 17:36 DEBUG  TaskList: ## Running Remove target dir....
12-27 17:36 DEBUG  CommonBackend: Deleting D:\ubuntu
12-27 17:36 DEBUG  TaskList: ## Finished Remove target dir.
12-27 17:36 DEBUG  TaskList: ## Running Remove registry key....
12-27 17:36 DEBUG  TaskList: ## Finished Remove registry key.
12-27 17:36 DEBUG  TaskList: # Finished tasklist
12-27 17:36 INFO   root: Almost finished uninstalling
12-27 17:36 INFO   root: Finished uninstallation
12-27 17:36 DEBUG  CommonBackend: Fetching basic info...
12-27 17:36 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:36 DEBUG  CommonBackend: platform=win32
12-27 17:36 DEBUG  CommonBackend: osname=nt
12-27 17:36 DEBUG  WindowsBackend: arch=amd64
12-27 17:36 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\data\isolist.ini
12-27 17:36 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:36 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:36 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:36 DEBUG  WindowsBackend: Fetching host info...
12-27 17:36 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:36 DEBUG  WindowsBackend: windows version=vista
12-27 17:36 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:36 DEBUG  WindowsBackend: windows_sp=None
12-27 17:36 DEBUG  WindowsBackend: windows_build=7600
12-27 17:36 DEBUG  WindowsBackend: gmt=0
12-27 17:36 DEBUG  WindowsBackend: country=GB
12-27 17:36 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:36 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:36 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:36 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:36 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:36 DEBUG  WindowsBackend: windows_language=English
12-27 17:36 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:36 DEBUG  WindowsBackend: bootloader=vista
12-27 17:36 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8031.5 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(C: hd 8031.5 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(E: hd 238144.070313 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:36 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:36 DEBUG  WindowsBackend: uninstaller_path=None
12-27 17:36 DEBUG  WindowsBackend: previous_target_dir=None
12-27 17:36 DEBUG  WindowsBackend: previous_distro_name=None
12-27 17:36 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:36 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:36 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:36 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:36 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:36 DEBUG  CommonBackend: Searching for local CDs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:36 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:36 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:36 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:36 INFO   root: Running the installer...
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:36 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:37 DEBUG  WinuiInstallationPage: target_drive=E:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=ian
12-27 17:37 INFO   root: Received settings
12-27 17:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\translations, languages=['en_GB', 'en']
12-27 17:37 DEBUG  TaskList: # Running tasklist...
12-27 17:37 DEBUG  TaskList: ## Running select_target_dir...
12-27 17:37 INFO   WindowsBackend: Installing into E:\ubuntu
12-27 17:37 DEBUG  TaskList: ## Finished select_target_dir
12-27 17:37 DEBUG  TaskList: ## Running create_dir_structure...
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\install
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\disks\boot\grub
12-27 17:37 DEBUG  CommonBackend: Creating dir E:\ubuntu\install\boot\grub
12-27 17:37 DEBUG  TaskList: ## Finished create_dir_structure
12-27 17:37 DEBUG  TaskList: ## Running uncompress_target_dir...
12-27 17:37 DEBUG  TaskList: ## Finished uncompress_target_dir
12-27 17:37 DEBUG  TaskList: ## Running create_uninstaller...
12-27 17:37 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> E:\ubuntu\uninstall-wubi.exe
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString E:\ubuntu\uninstall-wubi.exe
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir E:\ubuntu
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon E:\ubuntu\Ubuntu.ico
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-27 17:37 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-27 17:37 DEBUG  TaskList: ## Finished create_uninstaller
12-27 17:37 DEBUG  TaskList: ## Running copy_installation_files...
12-27 17:37 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\data\custom-installation -> E:\ubuntu\install\custom-installation
12-27 17:37 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\winboot -> E:\ubuntu\winboot
12-27 17:37 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pyl3EB4.tmp\data\images\Ubuntu.ico -> E:\ubuntu\Ubuntu.ico
12-27 17:37 DEBUG  TaskList: ## Finished copy_installation_files
12-27 17:37 DEBUG  TaskList: ## Running get_iso...
12-27 17:37 DEBUG  TaskList: New task copy_file
12-27 17:37 DEBUG  TaskList: ### Running copy_file...
12-27 17:39 DEBUG  TaskList: ### Finished copy_file
12-27 17:39 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:39 DEBUG  TaskList: # Cancelling tasklist
12-27 17:39 DEBUG  TaskList: New task check_iso
12-27 17:39 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:39 DEBUG  CommonBackend: Searching for local ISO
12-27 17:39 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-27 17:39 DEBUG  TaskList: New task get_metalink
12-27 17:39 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-27 17:39 DEBUG  TaskList: # Cancelling tasklist
12-27 17:39 DEBUG  TaskList: # Finished tasklist
12-27 17:40 INFO   root: === wubi 10.10 rev197 ===
12-27 17:40 DEBUG  root: Logfile is c:\users\ian\appdata\local\temp\wubi-10.10-rev197.log
12-27 17:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="G:\\wubi.exe"', '--cdmenu']
12-27 17:40 DEBUG  CommonBackend: data_dir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\data
12-27 17:40 DEBUG  WindowsBackend: 7z=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\bin\7z.exe
12-27 17:40 DEBUG  CommonBackend: Fetching basic info...
12-27 17:40 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:40 DEBUG  CommonBackend: platform=win32
12-27 17:40 DEBUG  CommonBackend: osname=nt
12-27 17:40 DEBUG  CommonBackend: language=en_GB
12-27 17:40 DEBUG  CommonBackend: encoding=cp1252
12-27 17:40 DEBUG  WindowsBackend: arch=amd64
12-27 17:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\data\isolist.ini
12-27 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:40 DEBUG  WindowsBackend: Fetching host info...
12-27 17:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:40 DEBUG  WindowsBackend: windows version=vista
12-27 17:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:40 DEBUG  WindowsBackend: windows_sp=None
12-27 17:40 DEBUG  WindowsBackend: windows_build=7600
12-27 17:40 DEBUG  WindowsBackend: gmt=0
12-27 17:40 DEBUG  WindowsBackend: country=GB
12-27 17:40 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:40 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:40 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:40 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:40 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:40 DEBUG  WindowsBackend: windows_language=English
12-27 17:40 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:40 DEBUG  WindowsBackend: bootloader=vista
12-27 17:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8030.37109375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(C: hd 8030.37109375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(E: hd 237440.355469 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:40 DEBUG  WindowsBackend: uninstaller_path=E:\ubuntu\uninstall-wubi.exe
12-27 17:40 DEBUG  WindowsBackend: previous_target_dir=E:\ubuntu
12-27 17:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
12-27 17:40 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:40 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:40 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:40 DEBUG  CommonBackend: python locale=('en_GB', 'cp1252')
12-27 17:40 DEBUG  CommonBackend: locale=en_GB.UTF-8
12-27 17:40 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:40 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:40 DEBUG  CommonBackend: Searching for local CDs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:   parsing info from str=Ubuntu 10.10 "Maverick Meerkat" - Release i386 (20101007)
12-27 17:40 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.10', 'build': '20101007', 'codename': 'Maverick Meerkat', 'arch': 'i386'}
12-27 17:40 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:40 INFO   root: Running the CD menu...
12-27 17:40 DEBUG  WindowsFrontend: __init__...
12-27 17:40 DEBUG  WindowsFrontend: on_init...
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:40 INFO   root: CD menu finished
12-27 17:40 INFO   root: Already installed, running the uninstaller...
12-27 17:40 INFO   root: Running the uninstaller...
12-27 17:40 INFO   CommonBackend: This is the uninstaller running
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:40 INFO   root: Received settings
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:40 DEBUG  TaskList: # Running tasklist...
12-27 17:40 DEBUG  TaskList: ## Running Backup ISO...
12-27 17:40 DEBUG  TaskList: ## Finished Backup ISO
12-27 17:40 DEBUG  TaskList: ## Running Remove bootloader entry....
12-27 17:40 DEBUG  WindowsBackend: Could not find bcd id
12-27 17:40 DEBUG  WindowsBackend: undo_bootini C:
12-27 17:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 8030.37109375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: undo_bootini D:
12-27 17:40 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: undo_bootini E:
12-27 17:40 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 237440.355469 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: undo_bootini F:
12-27 17:40 DEBUG  WindowsBackend: undo_configsys Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:40 DEBUG  TaskList: ## Finished Remove bootloader entry.
12-27 17:40 DEBUG  TaskList: ## Running Remove target dir....
12-27 17:40 DEBUG  CommonBackend: Deleting E:\ubuntu
12-27 17:40 DEBUG  TaskList: ## Finished Remove target dir.
12-27 17:40 DEBUG  TaskList: ## Running Remove registry key....
12-27 17:40 DEBUG  TaskList: ## Finished Remove registry key.
12-27 17:40 DEBUG  TaskList: # Finished tasklist
12-27 17:40 INFO   root: Almost finished uninstalling
12-27 17:40 INFO   root: Finished uninstallation
12-27 17:40 DEBUG  CommonBackend: Fetching basic info...
12-27 17:40 DEBUG  CommonBackend: original_exe=G:\wubi.exe
12-27 17:40 DEBUG  CommonBackend: platform=win32
12-27 17:40 DEBUG  CommonBackend: osname=nt
12-27 17:40 DEBUG  WindowsBackend: arch=amd64
12-27 17:40 DEBUG  CommonBackend: Parsing isolist=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\data\isolist.ini
12-27 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
12-27 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
12-27 17:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
12-27 17:40 DEBUG  WindowsBackend: Fetching host info...
12-27 17:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
12-27 17:40 DEBUG  WindowsBackend: windows version=vista
12-27 17:40 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
12-27 17:40 DEBUG  WindowsBackend: windows_sp=None
12-27 17:40 DEBUG  WindowsBackend: windows_build=7600
12-27 17:40 DEBUG  WindowsBackend: gmt=0
12-27 17:40 DEBUG  WindowsBackend: country=GB
12-27 17:40 DEBUG  WindowsBackend: timezone=Europe/London
12-27 17:40 DEBUG  WindowsBackend: windows_username=Ian
12-27 17:40 DEBUG  WindowsBackend: user_full_name=Ian
12-27 17:40 DEBUG  WindowsBackend: user_directory=C:\Users\Ian
12-27 17:40 DEBUG  WindowsBackend: windows_language_code=1033
12-27 17:40 DEBUG  WindowsBackend: windows_language=English
12-27 17:40 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
12-27 17:40 DEBUG  WindowsBackend: bootloader=vista
12-27 17:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 8029.34375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(C: hd 8029.34375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(D: hd 37940.484375 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(E: hd 238134.945313 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(F: hd 23853.7382813 mb free ntfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free cdfs)
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(H: cd 0.0 mb free )
12-27 17:40 DEBUG  WindowsBackend: drive=Drive(I: cd 0.0 mb free )
12-27 17:40 DEBUG  WindowsBackend: uninstaller_path=None
12-27 17:40 DEBUG  WindowsBackend: previous_target_dir=None
12-27 17:40 DEBUG  WindowsBackend: previous_distro_name=None
12-27 17:40 DEBUG  WindowsBackend: keyboard_id=134809609
12-27 17:40 DEBUG  WindowsBackend: keyboard_layout=gb
12-27 17:40 DEBUG  WindowsBackend: keyboard_variant=
12-27 17:40 DEBUG  WindowsBackend: total_memory_mb=4094.4921875
12-27 17:40 DEBUG  CommonBackend: Searching ISOs on USB devices
12-27 17:40 DEBUG  CommonBackend: Searching for local CDs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
12-27 17:40 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
12-27 17:40 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
12-27 17:40 INFO   Distro: Found a valid CD for Ubuntu: G:\
12-27 17:40 INFO   root: Running the installer...
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:41 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=ian
12-27 17:41 INFO   root: Received settings
12-27 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\translations, languages=['en_GB', 'en']
12-27 17:41 DEBUG  TaskList: # Running tasklist...
12-27 17:41 DEBUG  TaskList: ## Running select_target_dir...
12-27 17:41 INFO   WindowsBackend: Installing into C:\ubuntu
12-27 17:41 DEBUG  TaskList: ## Finished select_target_dir
12-27 17:41 DEBUG  TaskList: ## Running create_dir_structure...
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
12-27 17:41 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
12-27 17:41 DEBUG  TaskList: ## Finished create_dir_structure
12-27 17:41 DEBUG  TaskList: ## Running uncompress_target_dir...
12-27 17:41 DEBUG  TaskList: ## Finished uncompress_target_dir
12-27 17:41 DEBUG  TaskList: ## Running create_uninstaller...
12-27 17:41 DEBUG  WindowsBackend: Copying uninstaller G:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.10-rev197
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
12-27 17:41 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
12-27 17:41 DEBUG  TaskList: ## Finished create_uninstaller
12-27 17:41 DEBUG  TaskList: ## Running copy_installation_files...
12-27 17:41 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
12-27 17:41 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\winboot -> C:\ubuntu\winboot
12-27 17:41 DEBUG  WindowsBackend: Copying C:\Users\Ian\AppData\Local\Temp\pylD1FE.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
12-27 17:41 DEBUG  TaskList: ## Finished copy_installation_files
12-27 17:41 DEBUG  TaskList: ## Running get_iso...
12-27 17:41 DEBUG  TaskList: New task copy_file
12-27 17:41 DEBUG  TaskList: ### Running copy_file...
12-27 17:43 DEBUG  TaskList: ### Finished copy_file
12-27 17:43 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:43 DEBUG  TaskList: # Cancelling tasklist
12-27 17:43 DEBUG  TaskList: New task check_iso
12-27 17:43 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 118, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 208, in copy_file
IOError: [Errno 13] Permission denied
12-27 17:43 DEBUG  CommonBackend: Searching for local ISO
12-27 17:43 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
12-27 17:43 DEBUG  TaskList: New task get_metalink
12-27 17:43 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 330, in download_iso
Exception: Cannot download the metalink and therefore the ISO
12-27 17:43 DEBUG  TaskList: # Cancelling tasklist
12-27 17:43 DEBUG  TaskList: # Finished tasklist


---

