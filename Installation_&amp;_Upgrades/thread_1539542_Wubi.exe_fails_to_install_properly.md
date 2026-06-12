---
title: "Wubi.exe fails to install properly"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by orbach on 2010-07-26
OK, I first downloaded wubi,exe from the main site. The installation seemed to work but when I 

rebooted it complained no disk could be found and no iso file could be found, then dropped to a 

shell.

I followed the instructions here and downloaded the latest wubi.exe via the given link, 
wubi-r190.exe, and ran that. I first uninstalled the previous installation using the uninstaller in the ubuntu folder. Well, this latest version proceeds to install but then complains it cannot find the iso via the metalink and the installation fails altogether.

Then I was told to download wubi.exe from [http://wubi-installer.org/](http://wubi-installer.org/) and this version behaves just like the first one I downloaded from the main site.

I installed unto Windows drive D: which is a second hard drive I have. All the files seem to be there, especially the iso file it cannot find. There is nothing else on that hard drive. The disk files for the main Ubuntu fs and the swap fs are there too. I am running Windows XP Professional with all updates and the D drive is an empty NTFS file system.

The installation seems to work but when I boot into Ubuntu it displays the following message.

```

(initramfs) stdin: error 0
/scripts/casper-premount/20iso_scan: line 46: can't open /dev/sr0: No medium found

Could not find the ISO /ubuntu/install/ubuntu-10.04-desktop-amd64.iso. This could also 
happen if the file system is not clean because of an operating system crash, an interrupted 
boot process, an improper shutdown, or unplugging of a removable device without first 
unmounting or ejecting it. To fix this, simply reboot in to Windows, let it fully start, 
log in, run 'chkdsk /r', then gracefully shutdown and reboot back into Windows. After 
this you should be able to reboot again and resume the installation.
(initramfs)

```Attached also is the installation boot file.

There is nothing wrong with the disk or hard drive and the files seem to be all there. Is the boot process confused about the partition I chose to install Ubuntu on? Seems likely. How does the Ubuntu loader know to boot from the D drive?

OK couldn't upload the log file as an attachment. Here is the log file:

```

07-26 15:31 INFO   root: === wubi 10.04 rev189 ===
07-26 15:31 DEBUG  root: Logfile is c:\docume~1\jose\locals~1\temp\wubi-10.04-rev189.log
07-26 15:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jose\\Desktop\\wubi.exe"']
07-26 15:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data
07-26 15:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
07-26 15:31 DEBUG  CommonBackend: Fetching basic info...
07-26 15:31 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jose\Desktop\wubi.exe
07-26 15:31 DEBUG  CommonBackend: platform=win32
07-26 15:31 DEBUG  CommonBackend: osname=nt
07-26 15:31 DEBUG  CommonBackend: language=en_US
07-26 15:31 DEBUG  CommonBackend: encoding=cp1252
07-26 15:31 DEBUG  WindowsBackend: arch=amd64
07-26 15:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
07-26 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-26 15:31 DEBUG  WindowsBackend: Fetching host info...
07-26 15:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 15:31 DEBUG  WindowsBackend: windows version=xp
07-26 15:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-26 15:31 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-26 15:31 DEBUG  WindowsBackend: windows_build=2600
07-26 15:31 DEBUG  WindowsBackend: gmt=-5
07-26 15:31 DEBUG  WindowsBackend: country=US
07-26 15:31 DEBUG  WindowsBackend: timezone=America/New_York
07-26 15:31 DEBUG  WindowsBackend: windows_username=Jose
07-26 15:31 DEBUG  WindowsBackend: user_full_name=Jose
07-26 15:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jose
07-26 15:31 DEBUG  WindowsBackend: windows_language_code=1033
07-26 15:31 DEBUG  WindowsBackend: windows_language=English
07-26 15:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
07-26 15:31 DEBUG  WindowsBackend: bootloader=xp
07-26 15:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 13329.1132813 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(C: hd 13329.1132813 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(D: hd 35222.6914063 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(E: hd 336732.984375 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(F: hd 57887.8164063 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(W: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(X: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-26 15:31 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-26 15:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-26 15:31 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 15:31 DEBUG  WindowsBackend: keyboard_layout=us
07-26 15:31 DEBUG  WindowsBackend: keyboard_variant=
07-26 15:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-26 15:31 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 15:31 DEBUG  WindowsBackend: total_memory_mb=2046.484375
07-26 15:31 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 15:31 DEBUG  CommonBackend: Searching for local CDs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 INFO   root: Already installed, running the uninstaller...
07-26 15:31 INFO   root: Running the uninstaller...
07-26 15:31 INFO   CommonBackend: Launching previous uninestaller D:\ubuntu\uninstall-wubi.exe
07-26 15:31 DEBUG  root: application.quit
07-26 15:31 DEBUG  root: application.on_quit
07-26 15:31 INFO   root: sys.exit
07-26 15:31 INFO   root: Quitting application
07-26 15:31 INFO   root: === wubi 10.04 rev189 ===
07-26 15:31 DEBUG  root: Logfile is c:\docume~1\jose\locals~1\temp\wubi-10.04-rev189.log
07-26 15:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jose\\Desktop\\wubi.exe"']
07-26 15:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\data
07-26 15:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\bin\7z.exe
07-26 15:31 DEBUG  CommonBackend: Fetching basic info...
07-26 15:31 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jose\Desktop\wubi.exe
07-26 15:31 DEBUG  CommonBackend: platform=win32
07-26 15:31 DEBUG  CommonBackend: osname=nt
07-26 15:31 DEBUG  CommonBackend: language=en_US
07-26 15:31 DEBUG  CommonBackend: encoding=cp1252
07-26 15:31 DEBUG  WindowsBackend: arch=amd64
07-26 15:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\data\isolist.ini
07-26 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 15:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-26 15:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-26 15:31 DEBUG  WindowsBackend: Fetching host info...
07-26 15:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 15:31 DEBUG  WindowsBackend: windows version=xp
07-26 15:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-26 15:31 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-26 15:31 DEBUG  WindowsBackend: windows_build=2600
07-26 15:31 DEBUG  WindowsBackend: gmt=-5
07-26 15:31 DEBUG  WindowsBackend: country=US
07-26 15:31 DEBUG  WindowsBackend: timezone=America/New_York
07-26 15:31 DEBUG  WindowsBackend: windows_username=Jose
07-26 15:31 DEBUG  WindowsBackend: user_full_name=Jose
07-26 15:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jose
07-26 15:31 DEBUG  WindowsBackend: windows_language_code=1033
07-26 15:31 DEBUG  WindowsBackend: windows_language=English
07-26 15:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
07-26 15:31 DEBUG  WindowsBackend: bootloader=xp
07-26 15:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 13328.4804688 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(C: hd 13328.4804688 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(D: hd 35222.78125 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(E: hd 336732.984375 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(F: hd 57887.8164063 mb free ntfs)
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(W: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: drive=Drive(X: cd 0.0 mb free )
07-26 15:31 DEBUG  WindowsBackend: uninstaller_path=None
07-26 15:31 DEBUG  WindowsBackend: previous_target_dir=None
07-26 15:31 DEBUG  WindowsBackend: previous_distro_name=None
07-26 15:31 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 15:31 DEBUG  WindowsBackend: keyboard_layout=us
07-26 15:31 DEBUG  WindowsBackend: keyboard_variant=
07-26 15:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-26 15:31 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 15:31 DEBUG  WindowsBackend: total_memory_mb=2046.484375
07-26 15:31 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 15:31 DEBUG  CommonBackend: Searching for local CDs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu Netbook CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 15:31 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:31 INFO   root: Running the installer...
07-26 15:31 DEBUG  WindowsFrontend: __init__...
07-26 15:31 DEBUG  WindowsFrontend: on_init...
07-26 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
07-26 15:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
07-26 15:32 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=30000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jose
07-26 15:32 INFO   root: Received settings
07-26 15:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
07-26 15:32 DEBUG  TaskList: # Running tasklist...
07-26 15:32 DEBUG  TaskList: ## Running select_target_dir...
07-26 15:32 INFO   WindowsBackend: Installing into D:\ubuntu
07-26 15:32 DEBUG  TaskList: ## Finished select_target_dir
07-26 15:32 DEBUG  TaskList: ## Running create_dir_structure...
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-26 15:32 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-26 15:32 DEBUG  TaskList: ## Finished create_dir_structure
07-26 15:32 DEBUG  TaskList: ## Running uncompress_target_dir...
07-26 15:32 DEBUG  TaskList: ## Finished uncompress_target_dir
07-26 15:32 DEBUG  TaskList: ## Running create_uninstaller...
07-26 15:32 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jose\Desktop\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-26 15:32 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-26 15:32 DEBUG  TaskList: ## Finished create_uninstaller
07-26 15:32 DEBUG  TaskList: ## Running copy_installation_files...
07-26 15:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-26 15:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\winboot -> D:\ubuntu\winboot
07-26 15:32 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-26 15:32 DEBUG  TaskList: ## Finished copy_installation_files
07-26 15:32 DEBUG  TaskList: ## Running get_iso...
07-26 15:32 DEBUG  CommonBackend: Searching for local CD
07-26 15:32 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 15:32 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 15:32 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 15:32 DEBUG  CommonBackend: Searching for local ISO
07-26 15:32 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-26 15:32 DEBUG  TaskList: New task get_metalink
07-26 15:32 DEBUG  TaskList: ### Running get_metalink...
07-26 15:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink) > D:\ubuntu\install
07-26 15:32 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-26 15:32 DEBUG  downloader: download finished (read 7472 bytes)
07-26 15:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink](http://releases.ubuntu.com/10.04/MD5SUMS-metalink) > D:\ubuntu\install
07-26 15:32 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-26 15:32 DEBUG  downloader: download finished (read 639 bytes)
07-26 15:32 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-26 15:32 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-26 15:32 DEBUG  downloader: download finished (read 189 bytes)
07-26 15:32 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-26 15:32 INFO   saplog: Checking block bindings..
07-26 15:32 INFO   saplog: Key verified successfully.
07-26 15:32 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-26 15:32 DEBUG  TaskList: ### Finished get_metalink
07-26 15:32 DEBUG  TaskList: New task download
07-26 15:32 DEBUG  TaskList: ### Running download...
07-26 15:32 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent) > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  TaskList: ### Finished download
07-26 15:42 DEBUG  TaskList: New task check_iso
07-26 15:42 DEBUG  TaskList: ### Running check_iso...
07-26 15:42 DEBUG  CommonBackend: Checking D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release amd64 (20100429)
07-26 15:42 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'amd64'}
07-26 15:42 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  TaskList: New task get_file_md5
07-26 15:42 DEBUG  TaskList: #### Running get_file_md5...
07-26 15:42 DEBUG  TaskList: #### Finished get_file_md5
07-26 15:42 DEBUG  TaskList: ### Finished check_iso
07-26 15:42 DEBUG  TaskList: ## Finished get_iso
07-26 15:42 DEBUG  TaskList: ## Running extract_kernel...
07-26 15:42 DEBUG  CommonBackend: Extracting files from ISO D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  WindowsBackend:   extracting md5sum.txt from D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  WindowsBackend:   extracting casper\vmlinuz from D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  WindowsBackend:   extracting casper\initrd.lz from D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-26 15:42 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-26 15:42 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
07-26 15:42 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = 135737a6c8608631a2cde5a8aad7995c == 135737a6c8608631a2cde5a8aad7995c
07-26 15:42 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.lz
07-26 15:42 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.lz md5 = 4c67c0bd8c44ecca988e71e7631ed0aa == 4c67c0bd8c44ecca988e71e7631ed0aa
07-26 15:42 DEBUG  TaskList: ## Finished extract_kernel
07-26 15:42 DEBUG  TaskList: ## Running choose_disk_sizes...
07-26 15:42 DEBUG  WindowsBackend: total size=30000
  root=29744
  swap=256
  home=0
  usr=0
07-26 15:42 DEBUG  TaskList: ## Finished choose_disk_sizes
07-26 15:42 DEBUG  TaskList: ## Running create_preseed...
07-26 15:42 DEBUG  TaskList: ## Finished create_preseed
07-26 15:42 DEBUG  TaskList: ## Running modify_bootloader...
07-26 15:42 DEBUG  TaskList: New task modify_bootini
07-26 15:42 DEBUG  TaskList: ### Running modify_bootini...
07-26 15:42 DEBUG  WindowsBackend: modify_bootini C:
07-26 15:42 DEBUG  TaskList: ### Finished modify_bootini
07-26 15:42 DEBUG  TaskList: New task modify_bootini
07-26 15:42 DEBUG  TaskList: ### Running modify_bootini...
07-26 15:42 DEBUG  WindowsBackend: modify_bootini D:
07-26 15:42 DEBUG  WindowsBackend: Could not find boot.ini D:\boot.ini
07-26 15:42 DEBUG  TaskList: ### Finished modify_bootini
07-26 15:42 DEBUG  TaskList: New task modify_bootini
07-26 15:42 DEBUG  TaskList: ### Running modify_bootini...
07-26 15:42 DEBUG  WindowsBackend: modify_bootini E:
07-26 15:42 DEBUG  WindowsBackend: Could not find boot.ini E:\boot.ini
07-26 15:42 DEBUG  TaskList: ### Finished modify_bootini
07-26 15:42 DEBUG  TaskList: New task modify_bootini
07-26 15:42 DEBUG  TaskList: ### Running modify_bootini...
07-26 15:42 DEBUG  WindowsBackend: modify_bootini F:
07-26 15:42 DEBUG  WindowsBackend: Could not find boot.ini F:\boot.ini
07-26 15:42 DEBUG  TaskList: ### Finished modify_bootini
07-26 15:42 DEBUG  TaskList: ## Finished modify_bootloader
07-26 15:42 DEBUG  TaskList: ## Running modify_grub_configuration...
07-26 15:42 DEBUG  TaskList: ## Finished modify_grub_configuration
07-26 15:42 DEBUG  TaskList: ## Running create_virtual_disks...
07-26 15:42 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\root.disk of 29744MB
07-26 15:42 DEBUG  Virtualdisk:  Creating virtual disk D:\ubuntu\disks\swap.disk of 256MB
07-26 15:42 DEBUG  TaskList: ## Finished create_virtual_disks
07-26 15:42 DEBUG  TaskList: ## Running uncompress_files...
07-26 15:42 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot /U /A /F
07-26 15:42 DEBUG  WindowsBackend: compact D:\ubuntu\install\boot\*.* /U /A /F
07-26 15:42 DEBUG  TaskList: ## Finished uncompress_files
07-26 15:42 DEBUG  TaskList: ## Running eject_cd...
07-26 15:42 DEBUG  TaskList: ## Finished eject_cd
07-26 15:42 DEBUG  TaskList: # Finished tasklist
07-26 15:42 INFO   root: Almost finished installing
07-26 15:42 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl1A.tmp\translations, languages=['en_US', 'en']
07-26 15:44 INFO   root: Finished installation
07-26 15:44 INFO   root: Rebooting
07-26 15:44 DEBUG  TaskList: # Running tasklist...
07-26 15:44 DEBUG  TaskList: ## Running reboot...
07-26 15:44 DEBUG  TaskList: ## Finished reboot
07-26 15:44 DEBUG  TaskList: # Finished tasklist
07-26 15:44 DEBUG  root: application.quit
07-26 15:44 DEBUG  WindowsFrontend: frontend.quit
07-26 15:44 DEBUG  WindowsFrontend: frontend.on_quit
07-26 15:44 DEBUG  root: application.on_quit
07-26 15:44 INFO   root: sys.exit

```

---

