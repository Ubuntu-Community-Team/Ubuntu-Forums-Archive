---
title: "New to Ubuntu and issues already lol."
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by disintergrator on 2010-03-01
Hello,                                                     2/28/10
 

 I am new to Ubuntu, and I really do not know where to start.  I have been toying with the idea of insalling some version of Linux on a pc for the last decade, and have been thinking more specifically, reading about, and doing some general research here and there about Ubuntu over the last year or two.  That is what I finally decided on.  I only wish I had thought of keeping a log of my progress sooner than now.   
 

 I am attempting an install of Ubuntu Netbook 9.10 on my Dell XPS M1330 laptop.  It is proving to be a lot more of a challenge than I thought it would be.  The laptop came from the factory with Vista on it, as well as 2 other partitions on the hard drive: one was the Dell recovery, and one was for Media Direct.  When the laptop was off, there were two ways of turning it on: hit the regular power button (above the keyboard), and it will boot into Vista, or hit the Home (I think) button  (also above the keyboard, and to the left of the regular power button), and it would boot into Media Direct.  Media Direct is a program that allows you to view and organize your media files (kinda like Google's Picasa, but garnered more toward your music and movie collection.  I am not so worried about this program at the moment, but in the future, I think it might be nice to have a Tripple boot with MD, XP, and whatever flavor of Ubuntu or Linux I choose (which is Ubuntu Netbook, for the moment).
 

 Anyway, a year or so ago my friend took the laptop from me, after hearing me complain so much about Vista, and dual-booted it with XP Pro and an older version of Ubuntu.  He got it up and running fine and all, but I do seem to remember him having some issues with the SATA drive, and getting it connected to the internet.  Well, with my luck, I ended up having to send it back to Dell three times since then to replace the motherboard twice and the DVD-ROM once.  And on the first two times (the motherboard issues), they sent it back with factory settings, i.e. Vista.  I promptly installed XP Pro on it (and in doing so, I partitioned the hd with Ubuntu in mind....I made three seperate partitions: one for C:, one for Ububtu, and one for media storage), but did not want to have to ask my friend to reinstall Ubuntu on it, which is why I am here.  By the way, upon installing XP, the Home key beside the power button now does nothing, at least from XP.  I have been afraid to try it really due to some things I have read other people saying about when pressed it wipes out the MBR or something.  However, if it is possible to get a dual boot running, where I press the power button to go into one operating system, and press the home button to go into the other OS, then I think that would be sweet.  However, I digress...that is not why I am here at the moment.
 

 The other week I tried installing the latest version of xUbuntu on here,   I wish I had documented those problems.  I got errors on installing within XP, then tried off live cd, and got errors.  Tried a few work-arounds, and was still getting problems.  Then lo and behold, it started to work, one time.  It got about 25% of the way thru installing xUbuntu and then it got an error and rebooted during installation.  Upon the reboot, it gave me no boot menu, and went straight into xUbuntu and acted like everything was ok.  Wireless was working out of the box and I was very pleased with that.  But I was getting weird errors here and there.  And, upon booting back into XP, I noticed that the installation created two new hard drives under My Computer (G: & H:).  I ended up uninstalling it, convinced that the ChekSum might be wrong on the cd I made, but the 2 new drives remained, although I can not view their properties in XP, but I assume that is due to them being a different file system.  So I downloaded a copy of the Netbook edition, checked its sums and they turned out ok, then made a cd of it.  I tried installing a few times and it didnt work either, but finally took one time when I was using Wubi to install it in Windows.  Wireless was not working out of the box on this install, and today I just got that up and working by installing the drivers.  Then it prompted me to run updates, which I did.  And after rebooting after those, it comes up with:  
 ```
GNU GRUB version 1.97 beta4
[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]
sh:grub>
```When I pressed TAB, it would give a list of commands, only two of which I felt comfortable enough in trying: boot & reboot.  When trying boot, it would return the following error message:
 ```
error: no kernel loaded

```When trying the reboot command, it worked find and got me back to the boot menu, where picking Netbook would result in the same outcome again.  I have read a little into this problem, and some suggest a reinstall of Ubuntu.  I would not mind a reinstall of it, since I dont have much done on it yet, but would like some pointers along the way.  Such as getting it not to make two new drives, and maybe put it on the drive I have already partitioned for it.  It would also be nice to get that button working like I mentioned above, but I assume that would probably call for a total reinstall of XP as well.  Which is something I am not totally against, thought it might take me a hot minute to get ready for that.
 
 Currently I am attempting to uninstall Ubuntu Netbook so I can install and try it again, but every time I try to uninstall it from the Add/Remove Programs in XP, it gets all the way thru the top progress bar and about halfway thru on the bottom progress bar, and then it returns the following error message:
 ```
Invalid argument removing C:\ubuntu\disks\root.disk 
```And it notifies me of the following log left: wubi-9.10ubuntu1-rev160
 

 ```
02-28 03:24 INFO   root: === wubi 9.10ubuntu1 rev160 ===
 02-28 03:24 DEBUG  root: Logfile is c:\docume~1\tod\locals~1\temp\wubi-9.10ubuntu1-rev160.log
 02-28 03:24 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
 02-28 03:24 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\data
 02-28 03:24 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\bin\7z.exe
 02-28 03:24 DEBUG  CommonBackend: Fetching basic info...
 02-28 03:24 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
 02-28 03:24 DEBUG  CommonBackend: platform=win32
 02-28 03:24 DEBUG  CommonBackend: osname=nt
 02-28 03:24 DEBUG  CommonBackend: language=en_US
 02-28 03:24 DEBUG  CommonBackend: encoding=cp1252
 02-28 03:24 DEBUG  WindowsBackend: arch=amd64
 02-28 03:24 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\data\isolist.ini
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
 02-28 03:24 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
 02-28 03:24 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
 02-28 03:24 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
 02-28 03:24 DEBUG  WindowsBackend: Fetching host info...
 02-28 03:24 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
 02-28 03:24 DEBUG  WindowsBackend: windows version=xp
 02-28 03:24 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
 02-28 03:24 DEBUG  WindowsBackend: windows_sp=Service Pack 3
 02-28 03:24 DEBUG  WindowsBackend: windows_build=2600
 02-28 03:24 DEBUG  WindowsBackend: gmt=-5
 02-28 03:24 DEBUG  WindowsBackend: country=US
 02-28 03:24 DEBUG  WindowsBackend: timezone=America/New_York
 02-28 03:24 DEBUG  WindowsBackend: windows_username=tod
 02-28 03:24 DEBUG  WindowsBackend: user_full_name=tod
 02-28 03:24 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\tod
 02-28 03:24 DEBUG  WindowsBackend: windows_language_code=1033
 02-28 03:24 DEBUG  WindowsBackend: windows_language=English
 02-28 03:24 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
 02-28 03:24 DEBUG  WindowsBackend: bootloader=xp
 02-28 03:24 DEBUG  WindowsBackend: system_drive=Drive(C: hd 3016.00390625 mb free ntfs)
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(C: hd 3016.00390625 mb free ntfs)
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(D: hd 13766.1601563 mb free ntfs)
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(E: hd 14399.6054688 mb free ntfs)
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(G: hd 0.0 mb free )
 02-28 03:24 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
 02-28 03:24 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
 02-28 03:24 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
 02-28 03:24 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
 02-28 03:24 DEBUG  WindowsBackend: keyboard_id=67699721
 02-28 03:24 DEBUG  WindowsBackend: keyboard_layout=us
 02-28 03:24 DEBUG  WindowsBackend: keyboard_variant=
 02-28 03:24 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
 02-28 03:24 DEBUG  CommonBackend: locale=en_US.UTF-8
 02-28 03:24 DEBUG  WindowsBackend: total_memory_mb=1021.96875
 02-28 03:24 DEBUG  CommonBackend: Searching ISOs on USB devices
 02-28 03:24 DEBUG  CommonBackend: Searching for local CDs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 02-28 03:24 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 02-28 03:24 INFO   root: Running the uninstaller...
 02-28 03:24 INFO   CommonBackend: This is the uninstaller running
 02-28 03:24 DEBUG  WindowsFrontend: __init__...
 02-28 03:24 DEBUG  WindowsFrontend: on_init...
 02-28 03:24 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\tod\LOCALS~1\Temp\pyl146.tmp\translations, languages=['en_US', 'en']
 02-28 03:24 INFO   WindowsFrontend: Operation cancelled
 02-28 03:24 DEBUG  WindowsFrontend: frontend.quit
 02-28 03:24 DEBUG  WindowsFrontend: frontend.on_quit
 02-28 03:24 DEBUG  root: application.on_quit
 02-28 03:24 INFO   root: sys.exit
 03-01 00:31 INFO   root: === wubi 9.10ubuntu1 rev160 ===
 03-01 00:31 DEBUG  root: Logfile is c:\docume~1\tod\locals~1\temp\wubi-9.10ubuntu1-rev160.log
 03-01 00:31 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
 03-01 00:31 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\data
 03-01 00:31 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\bin\7z.exe
 03-01 00:31 DEBUG  CommonBackend: Fetching basic info...
 03-01 00:31 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
 03-01 00:31 DEBUG  CommonBackend: platform=win32
 03-01 00:31 DEBUG  CommonBackend: osname=nt
 03-01 00:31 DEBUG  CommonBackend: language=en_US
 03-01 00:31 DEBUG  CommonBackend: encoding=cp1252
 03-01 00:31 DEBUG  WindowsBackend: arch=amd64
 03-01 00:31 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\data\isolist.ini
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
 03-01 00:31 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
 03-01 00:31 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
 03-01 00:31 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
 03-01 00:31 DEBUG  WindowsBackend: Fetching host info...
 03-01 00:31 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
 03-01 00:31 DEBUG  WindowsBackend: windows version=xp
 03-01 00:31 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
 03-01 00:31 DEBUG  WindowsBackend: windows_sp=Service Pack 3
 03-01 00:31 DEBUG  WindowsBackend: windows_build=2600
 03-01 00:31 DEBUG  WindowsBackend: gmt=-5
 03-01 00:31 DEBUG  WindowsBackend: country=US
 03-01 00:31 DEBUG  WindowsBackend: timezone=America/New_York
 03-01 00:31 DEBUG  WindowsBackend: windows_username=tod
 03-01 00:31 DEBUG  WindowsBackend: user_full_name=tod
 03-01 00:31 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\tod
 03-01 00:31 DEBUG  WindowsBackend: windows_language_code=1033
 03-01 00:31 DEBUG  WindowsBackend: windows_language=English
 03-01 00:31 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
 03-01 00:31 DEBUG  WindowsBackend: bootloader=xp
 03-01 00:31 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2891.47265625 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(C: hd 2891.47265625 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(D: hd 13766.1484375 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(E: hd 14399.5976563 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(G: hd 0.0 mb free )
 03-01 00:31 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
 03-01 00:31 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
 03-01 00:31 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
 03-01 00:31 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
 03-01 00:31 DEBUG  WindowsBackend: keyboard_id=67699721
 03-01 00:31 DEBUG  WindowsBackend: keyboard_layout=us
 03-01 00:31 DEBUG  WindowsBackend: keyboard_variant=
 03-01 00:31 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
 03-01 00:31 DEBUG  CommonBackend: locale=en_US.UTF-8
 03-01 00:31 DEBUG  WindowsBackend: total_memory_mb=1021.96875
 03-01 00:31 DEBUG  CommonBackend: Searching ISOs on USB devices
 03-01 00:31 DEBUG  CommonBackend: Searching for local CDs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 03-01 00:31 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:31 INFO   root: Running the uninstaller...
 03-01 00:31 INFO   CommonBackend: This is the uninstaller running
 03-01 00:31 DEBUG  WindowsFrontend: __init__...
 03-01 00:31 DEBUG  WindowsFrontend: on_init...
 03-01 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
 03-01 00:31 INFO   root: Received settings
 03-01 00:31 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylB.tmp\translations, languages=['en_US', 'en']
 03-01 00:31 DEBUG  TaskList: # Running tasklist...
 03-01 00:31 DEBUG  TaskList: ## Running Backup ISO...
 03-01 00:31 DEBUG  TaskList: ## Finished Backup ISO
 03-01 00:31 DEBUG  TaskList: ## Running Remove bootloader entry...
 03-01 00:31 ERROR  WindowsBackend: Cannot find bcdedit
 03-01 00:31 DEBUG  WindowsBackend: undo_bootini C:
 03-01 00:31 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2891.47265625 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: undo_bootini D:
 03-01 00:31 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 13766.1484375 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: undo_bootini E:
 03-01 00:31 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 14399.5976563 mb free ntfs)
 03-01 00:31 DEBUG  WindowsBackend: undo_bootini G:
 03-01 00:31 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 0.0 mb free )
 03-01 00:31 DEBUG  WindowsBackend: undo_bootini H:
 03-01 00:31 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 0.0 mb free )
 03-01 00:31 DEBUG  TaskList: ## Finished Remove bootloader entry
 03-01 00:31 DEBUG  TaskList: ## Running Remove target dir...
 03-01 00:31 DEBUG  CommonBackend: Deleting C:\ubuntu
 03-01 00:31 ERROR  TaskList: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 Traceback (most recent call last):
   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
   File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
   File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
   File "\lib\shutil.py", line 142, in rmtree
 OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 03-01 00:31 DEBUG  TaskList: # Cancelling tasklist
 03-01 00:31 DEBUG  TaskList: # Finished tasklist
 03-01 00:31 ERROR  root: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 Traceback (most recent call last):
   File "\lib\wubi\application.py", line 56, in run
   File "\lib\wubi\application.py", line 122, in select_task
   File "\lib\wubi\application.py", line 177, in run_uninstaller
   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
   File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
   File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
   File "\lib\shutil.py", line 142, in rmtree
 OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 03-01 00:32 INFO   root: === wubi 9.10ubuntu1 rev160 ===
 03-01 00:32 DEBUG  root: Logfile is c:\docume~1\tod\locals~1\temp\wubi-9.10ubuntu1-rev160.log
 03-01 00:32 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
 03-01 00:32 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\data
 03-01 00:32 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\bin\7z.exe
 03-01 00:32 DEBUG  CommonBackend: Fetching basic info...
 03-01 00:32 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
 03-01 00:32 DEBUG  CommonBackend: platform=win32
 03-01 00:32 DEBUG  CommonBackend: osname=nt
 03-01 00:32 DEBUG  CommonBackend: language=en_US
 03-01 00:32 DEBUG  CommonBackend: encoding=cp1252
 03-01 00:32 DEBUG  WindowsBackend: arch=amd64
 03-01 00:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\data\isolist.ini
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
 03-01 00:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
 03-01 00:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
 03-01 00:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbookRemix-i386
 03-01 00:32 DEBUG  WindowsBackend: Fetching host info...
 03-01 00:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
 03-01 00:32 DEBUG  WindowsBackend: windows version=xp
 03-01 00:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
 03-01 00:32 DEBUG  WindowsBackend: windows_sp=Service Pack 3
 03-01 00:32 DEBUG  WindowsBackend: windows_build=2600
 03-01 00:32 DEBUG  WindowsBackend: gmt=-5
 03-01 00:32 DEBUG  WindowsBackend: country=US
 03-01 00:32 DEBUG  WindowsBackend: timezone=America/New_York
 03-01 00:32 DEBUG  WindowsBackend: windows_username=tod
 03-01 00:32 DEBUG  WindowsBackend: user_full_name=tod
 03-01 00:32 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\tod
 03-01 00:32 DEBUG  WindowsBackend: windows_language_code=1033
 03-01 00:32 DEBUG  WindowsBackend: windows_language=English
 03-01 00:32 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
 03-01 00:32 DEBUG  WindowsBackend: bootloader=xp
 03-01 00:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 2890.92578125 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(C: hd 2890.92578125 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(D: hd 13766.1484375 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(E: hd 14399.5976563 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(G: hd 0.0 mb free )
 03-01 00:32 DEBUG  WindowsBackend: drive=Drive(H: hd 0.0 mb free )
 03-01 00:32 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
 03-01 00:32 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
 03-01 00:32 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Remix
 03-01 00:32 DEBUG  WindowsBackend: keyboard_id=67699721
 03-01 00:32 DEBUG  WindowsBackend: keyboard_layout=us
 03-01 00:32 DEBUG  WindowsBackend: keyboard_variant=
 03-01 00:32 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
 03-01 00:32 DEBUG  CommonBackend: locale=en_US.UTF-8
 03-01 00:32 DEBUG  WindowsBackend: total_memory_mb=1021.96875
 03-01 00:32 DEBUG  CommonBackend: Searching ISOs on USB devices
 03-01 00:32 DEBUG  CommonBackend: Searching for local CDs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu Netbook Remix CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu Netbook CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
 03-01 00:32 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
 03-01 00:32 INFO   root: Running the uninstaller...
 03-01 00:32 INFO   CommonBackend: This is the uninstaller running
 03-01 00:32 DEBUG  WindowsFrontend: __init__...
 03-01 00:32 DEBUG  WindowsFrontend: on_init...
 03-01 00:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
 03-01 00:32 INFO   root: Received settings
 03-01 00:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\tod\LOCALS~1\Temp\pylC.tmp\translations, languages=['en_US', 'en']
 03-01 00:32 DEBUG  TaskList: # Running tasklist...
 03-01 00:32 DEBUG  TaskList: ## Running Backup ISO...
 03-01 00:32 DEBUG  TaskList: ## Finished Backup ISO
 03-01 00:32 DEBUG  TaskList: ## Running Remove bootloader entry...
 03-01 00:32 ERROR  WindowsBackend: Cannot find bcdedit
 03-01 00:32 DEBUG  WindowsBackend: undo_bootini C:
 03-01 00:32 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 2890.92578125 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: undo_bootini D:
 03-01 00:32 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 13766.1484375 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: undo_bootini E:
 03-01 00:32 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 14399.5976563 mb free ntfs)
 03-01 00:32 DEBUG  WindowsBackend: undo_bootini G:
 03-01 00:32 DEBUG  WindowsBackend: undo_configsys Drive(G: hd 0.0 mb free )
 03-01 00:32 DEBUG  WindowsBackend: undo_bootini H:
 03-01 00:32 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 0.0 mb free )
 03-01 00:32 DEBUG  TaskList: ## Finished Remove bootloader entry
 03-01 00:32 DEBUG  TaskList: ## Running Remove target dir...
 03-01 00:32 DEBUG  CommonBackend: Deleting C:\ubuntu
 03-01 00:32 ERROR  TaskList: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 Traceback (most recent call last):
   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
   File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
   File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
   File "\lib\shutil.py", line 142, in rmtree
 OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 03-01 00:32 DEBUG  TaskList: # Cancelling tasklist
 03-01 00:32 DEBUG  TaskList: # Finished tasklist
 03-01 00:32 ERROR  root: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 Traceback (most recent call last):
   File "\lib\wubi\application.py", line 56, in run
   File "\lib\wubi\application.py", line 122, in select_task
   File "\lib\wubi\application.py", line 177, in run_uninstaller
   File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
   File "\lib\wubi\backends\common\backend.py", line 643, in remove_target_dir
   File "\lib\wubi\backends\common\utils.py", line 313, in rm_tree
   File "\lib\shutil.py", line 142, in rmtree
 OSError: [Errno 22] Invalid argument removing C:\ubuntu\disks\root.disk
 
``` So, that is where I am at now.  Any help at all, or even a point in the right direction would be greatly appreciated.  Thank you in advance.
 

 PS
 If I am posting in the wrong place, please forgive me and point me to the right spot.  I am entirely new to all this.  Thank you again.

---

### Post by nothingspecial on 2010-03-01
I know nothing of windows but I would try installing ubuntu again to which ever partition you tried first.

Boot up the cd

Go applications > terminal and type

```
sudo fdisk -l
```

You should have 3(or more if you have a recovery) partitions

one will be listed Linux swap/ solaris and one will be labled linux, any others will be listed ntfs

Make a note of each partitions /dev/sd??

Also type ```
df -h
```
to check you have enough room on the larger linux partition for ubuntu. About 10 gigs is fine.

Then go through the install process and when you get to the partitioning bit, choose manual (advanced)

Look back to the partitions you noted before.

Do not touch the windows partition.

Right click on the larger linux partition and choose change (or whatever they call it these days)

Choose use as ext4 journaling file system

Check the format partition box

Select a mount point of /

Double check you have done this to the correct partition and not the windows one

Then click install (or apply, or whatever it says)

---

### Post by Silent Warrior on 2010-03-01
<Never mind, I came too late. :)>

---

### Post by OrangeCrate on 2010-03-01
> **disintergrator said:**
> Hello,                                                     2/28/10
 

** I am new to Ubuntu, and I really do not know where to start.**  I have been toying with the idea of insalling some version of Linux on a pc for the last decade, and have been thinking more specifically, reading about, and doing some general research here and there about Ubuntu over the last year or two.  That is what I finally decided on.  I only wish I had thought of keeping a log of my progress sooner than now.   
 
<snip>
 

 PS
 If I am posting in the wrong place, please forgive me and point me to the right spot.  I am entirely new to all this.  Thank you again.

Start here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Regarding a dual boot, specifically here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

To gain a great basic understanding of Ubuntu, see here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

And then, read this (just to be sure that you know what you're getting into with Linux):

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Good luck.

:)

---

### Post by underquark on 2010-03-01
> **Silent Warrior said:**
> <Never mind, I came too late. :)>Never had that complaint before.

---

### Post by disintergrator on 2010-03-01
> **nothingspecial said:**
> I know nothing of windows but I would try installing ubuntu again to which ever partition you tried first.

Boot up the cd

Go applications > terminal and type

```
sudo fdisk -l
```You should have 3(or more if you have a recovery) partitions

one will be listed Linux swap/ solaris and one will be labled linux, any others will be listed ntfs

Make a note of each partitions /dev/sd??

Also type ```
df -h
```to check you have enough room on the larger linux partition for ubuntu. About 10 gigs is fine.

Then go through the install process and when you get to the partitioning bit, choose manual (advanced)

Look back to the partitions you noted before.

Do not touch the windows partition.

Right click on the larger linux partition and choose change (or whatever they call it these days)

Choose use as ext4 journaling file system

Check the format partition box

Select a mount point of /

Double check you have done this to the correct partition and not the windows one

Then click install (or apply, or whatever it says)


This is basically an update:
I am about to try another install of it.  But first, I tried to get back on the Ubuntu side, and after choosing Ubuntu Netbook to go it returned the following error message:
```
Windows could not start because the following file is missing
or corrupt:
<Windows root>\system32\hal.dll .
Please reinstall a copy of the above file.
```
So I then booted back into XP and tried uninstalling it again, and it worked.  But there is one thing I'd like to do before installing Ubuntu again, and that is re-partitioning my hd.  It now is partitioned into 5 hard drives, 2 of which are not in use (the 2 that the middle Ubuntu installation created).  I'd like to redistribute those back to the other 3, and use the third one I created in XP'x installation for Ubuntu.  Right now I am looking for an application that will help me do that.  I am thinking about Partition Wizard.  Does anyone know a bit about these types of programs, and care to give me their recommendations?

---

### Post by disintergrator on 2010-03-01
> **OrangeCrate said:**
> Start here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

Regarding a dual boot, specifically here:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

To gain a great basic understanding of Ubuntu, see here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

And then, read this (just to be sure that you know what you're getting into with Linux):

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Good luck.

:)

Thank you.  Those are some informative links.  I admit I haven't read everything there, but they have been bookmarked for later use.  Thank you, again.

---

### Post by nothingspecial on 2010-03-01
Boot the live cd

In the menu go system > administration > gparted

delete the 2 partitions and grow the third partition into the free space.

Make sure it is the ext3/4 partitions you qare messing with.

---

### Post by disintergrator on 2010-03-01
> **nothingspecial said:**
> Boot the live cd
In the menu go system > administration > gparted
delete the 2 partitions and grow the third partition into the free space.
Make sure it is the ext3/4 partitions you qare messing with.

Ok.  A question before I start, and do something I shouldn't.  
Under XP the drives show up as follows:
```
C: Local Disk 48.8GB
D: Local Disk 41.6 GB
E: Local Disk 41.1 GB
G: Local Disk
H: Local Disk
```C: is where XP resides.  D: is where the shared media folder resides.  E: is the partition I made during the XP installation for a Linux.  However, I have already formatted it with a NTFS and now realize that it was wrong to do that, and therefore probably needs to be repartitioned.  XP recognizes that G: and H: are there, but gives me no properties or details on them, I assume because these are Linux partitions that XP might not be able to read.

I booted with the live CD and went into GParted, and it shows the following:
     ```
/dev/sda1     ntfs             48.83 GB     boot
/dev/sda2     extended         62.95 GB     lba     
/dev/sda5     ntfs             41.66 GB 
/dev/sda7     ext4              6.81 GB
/dev/sda8     linux-swap      368.65 MB
/dev/sda6     ntfs             14.13 GB
 unallocated                    7.84 GB
```I attempted to delete sda7, but that returned the following error message:
```
Unable to delete /dev/sda7!
Please unmount any logical partitions having 
a number higher than 7.
OK
```From what I can tell, that message just told me to delete sda8, which is the linux-swap drive, and you didn't really say anything about deleting that, so I will await further instructions here.

But seeing as how I now no longer need E: (41 GB), I assume it is ok to mess with sda5.  And will now attempt to delete it.  Ok.  In trying that, it returns a very similar error message:
```
Unable to delete /dev/sda5!
Please unmount any logical partitions having 
a number higher than 5. 
OK
```Ok.  Now I think I am stuck, and will await further help.  Thank you again.

---

### Post by OrangeCrate on 2010-03-01
> **disintergrator said:**
> Thank you.  Those are some informative links.  I admit I haven't read everything there, but they have been bookmarked for later use.  Thank you, again.

You're welcome.

:)

---

### Post by disintergrator on 2010-03-01
Update:
Was playing with GParted, and accidentally deleted the wrong drive.  Not the XP drive, but the storage drive.  Am thinking about reformatting altogether.  XP first, and then Ubuntu.

---

### Post by Silent Warrior on 2010-03-01
That's probably easiest. I think the message about having to unmount a partition before deleting sda5 can be dealt with, though, but I'm not sure how - I don't want to give bad advice about this, so I'll keep my peace.

underquark: You're a nasty little man. :P

---

### Post by disintergrator on 2010-03-03
> **Silent Warrior said:**
> That's probably easiest. I think the message about having to unmount a partition before deleting sda5 can be dealt with, though, but I'm not sure how - I don't want to give bad advice about this, so I'll keep my peace.

underquark: You're a nasty little man. :P


Ok.  Sorry for the time involved in waiting.  It has been a rough past couple of days.  I am still a new parent, and still getting used to that.  

Also, it seems yesterday I spent the entire day on my laptop doing last minute things in order to help with a safe recovery from the reformat.  I did manage to get XP Pro back on here, but it came with a few added extras (one of my own desire) that I wasn't expecting to encounter.  

Before reinstalling, I read up a little bit on Media Direct, and realized how much I missed having the capability of using that program directly without having to go thru the motions of booting up any operating system to get to it, so I thought why not?  Put that thing back on here, and see if we can't give it a go again.  If I get tired of it, I can always reformat again at a later time.  So I put that on, and it got to the last part and told me to go ahead and install my operating system, and when I was done with that, put the MD cd back in to finish installing.  So I started to install XP Pro.  I got to a point where it was going to take over 30 min or so, and I took a nap.  My wife then took over, and she got thru the time and naming the computer.  Right after she named it, the percentage jumped from 39% left to 23% left, and then she set it down, and after about 2 minutes, it cut off.  Now my laptop has been having some overheating problems, so I bet that is the culprit here.  Anyway, she let it cool down for about 5 min, then turned it back on, and did NOT load from cd, but just let it go on in to XP.  When she got there, it said Setup will start over.  It started up at 39% left, and turned off again almost immediately.  And that is where she left it, and I got to it the next morning.  When I woke up the laptop was off. and when I turned it on, it welcomed me to continue the installation of XP, so I completed it.  Then I started with the drivers, and replacing programs (from [www.download.com]("http://www.download.com")), and Windows Updates.  I think I finally got most of it back the way I want it, including Media Direct.  The only bad thing though, is that somewhere along the way I picked up a Trojan.  And I have had a particularly bad time with Trojans in general over 2 other peoples computers that came to me for help in dealing with them, as you can read about 
**************[_here_.]("http://www.cybertechhelp.com/forums/search.php?searchid=3055229")  ****link has been edited and should work now
The first thread is my case with this pc, and the next 2 threads are similar cases I had with my roommates pc, and my father's pc.  The fourth thread is from when I tried installing Ubuntu on here the other week.**********************************************************************    I so want to go ahead and install Netbook on here now, but first I need to make sure these trojans are no longer on here, and I will get help with that at [www.cybertechhelp.com]("http://www.cybertechhelp.com") .  Once I am done with that, I want to defrag the pc, and then make a SAFE restore point, and then I will install.  I just want to take a few precautions, so I will keep you updated.


The ****denote where I edited.

---

### Post by disintergrator on 2010-03-06
Well, I am having it looked into at CTH, and if you'd like to follow along with what they are advising me to do with the laptop, here is the [link]("http://www.cybertechhelp.com/forums/private.php?do=showpm&pmid=108688").

---

### Post by disintergrator on 2010-03-07
Alrite, think I am about to get the all-clear from them, so tonite, I will run all my scans, then defrag and create a new restore point.  After that, I will get onto installing Ubuntu.

---

### Post by disintergrator on 2010-03-10
The following is an excerpt from [this thread ]("http://www.cybertechhelp.com/forums/showthread.php?t=206680&page=2")at CyberTechHelp.  It explains my current status, and a little bit more.  Feel free to read the [thread ]("http://www.cybertechhelp.com/forums/showthread.php?t=206680&page=2")as well.  As to now, I am kinda stuck.  See below:

> **Jaytee said:**
> Thats cool, I agree with you as I felt the same way a few years ago for a couple of years. An easy option is to dual boot then you have your safety net of a familiar system and the "lets try and see how it goes" system. My own experience was a transition (after a few lumps in the middle) from the proprietary to open source.
Yep, that is about where I am now.  I have opened my eyes to open source programs, and am trying to use more everywhere I see fit.  I now use OpenOffice instead of MS Office, and I repalced my Nero with Infrascan, but have only used it so far to burn this one live cd.  I don't know if it is open source or not, but I am now trying to manage my Ipod with Media Monkey instead of Itunes.  I also use VLC and and a few others that are not coming to mind at the moment.  I have started to use them more lately because I heard somewhere that in doing so, it can actually aid in ones transition from an OS like Windows to some flavors of Linux.  
I now have the laptop dual booting XP and Ubuntu Netbook (and triple booting, if you count Media Direct, that is).  Yet another strange occurence, to me, anyway, on this installation.  The first time I installed Ubuntu on here, it was xUbuntu, and it recognized my WiFi right out of the box, and I was online right after installation.  The next time, a couple weeks later, it was Ubuntu Netbook and it didnt have WiFi right out of the box, but it notified my of drivers to be installed, and after doing that, it was fine.  Then once it got online, it said there were some updates for Ubuntu itself, so I tried to get them, and that was when everything started to go downhill lol.  Well, that was a couple weeks ago at most, and now here I am.  Similar problem.  This time it just isnt notifying me of nothing, and I do not really know where to go to initiate it myself.  
> **Jaytee said:**
> I seldom use the MS product except to test some thing. I have become very comfortable with the Linux operating system. However it is not a competition so if you are satisfied with Windows there is nothing forcing you to change...:)
I know I do not have to change from Windows.  And I am comfortable with it...but to a point.  There are a lot of places I see where it could be better.  I think what attracts me to Linux is the fact that it is almost infinitely more customizable than any MS OS.  I know you would need to learn a hell of a lot before being able to turn a Linux flavor into your own fully-custoimized-to-your-own-interest-OS, but that is something I am interested in at least trying, to give it a shot, if nothing else.  I really just want to learn and know more about Linux.  I don't really look at it as a competition, but more as a learning experience.  I know that one of a few different things will happen: whether it is a few months or years down the road, eventually I will come out on the other end predominantly a MS user, predominantly a Linux user, or what I actually hope for most at the moment, someone who is in-between, and comfortable enough in either environment, maybe depending on the task.  Anyway, that is my thoughts.

---

### Post by disintergrator on 2010-03-11
I see one problem now.  When I boot with the live cd, once I get it up, it says something about restricted drivers, and shows drivers to be installed.  But I try them, and only one will install, the Broadcom driver.  Ive got a cd of all the dell drivers for this laptop, if that will help, but it is about 2 years old or so, the cd, that is.
But what I dont understand is why does that come up when I boot from the cd, and not when I actually boot into Ubuntu itself?

---

### Post by disintergrator on 2010-03-13
well, looks like Dell is gonna take the laptop back yet again....look to see what the overheating problem is....then possibly send it back to me yet again with vista on it....annd recomending me to stay with vista, or at least just one OS.  if i cant install side by side os's, aint there apps that will run another os  inside your current one....i.e. running Vista, open a program where u can run xp and ubuntu?  something like that?  i think i heard a friend of mine talk about the one they use at work called Virtual Machine.  anyone know anything about that app, or can recomend another similar app?  or your own advice to anything to do with my situation here.  All feedback is welcome and considered.
Thank you.

---

### Post by disintergrator on 2010-03-15
This is a copy of the first email I sent to the Dell manager who is handling my case.  I am gonna send these just to keep you updated, and also to consider any advice you may have.

[QUOTE=Myself]http://www.cybertechhelp.com/forums/search.php?searchid=3060969

The above is a link to all topics created by me at [www.cybertechhelp.com](www.cybertechhelp.com).  This is where I go for computer help when I can not afford the outrageous prices others charge to work on them.  As you can see, I have been a member there for quite a while, and have started quite a few different threads....and all but two or three of them are in regards to one of the many Dells I have came in contact with, whether they are my own pcs, my families, or my friends.  A few of them were actually put together by me, either physically or on your website, but under the owners name.  I have brought Dell a good bit a business through my family and friends.  If you value your business with us, as well as your business with all other customers, I would advise you guys to treat me right this time.  Make sure whatever they do, actually works this time.  There is no reason that running 2 operating systems should overheat a pc, especially since only one os can run at a time, and as I stated before, this problem has happened more often when the pc has had only one os on it, whether that os was Vista, XP, or Ubuntu.  ****e...this thing is overheating again.  Will get back to this email later. 

I am currently scanning the laptop for any infections, and then I will Clean Disk, then Defragment, then reformat, and finally reinstall Vista and Media Direct.  Once I am done with that, I will rescan again, then install drivers and updates.  Once that is completed, I will rescan again, and start to install everything back.  Once I am done there, I will rescan again, and then Clean Disk and defrag again.  I will keep you updated with these processes by email. 

I am doing it this way because recently, in reformatting and reinstalling, 4 different times on 3 separate computers over the past 2 months, I have encountered various infection problems (viruses, viruts, rootkits, etc) shortly after a reformat and reinstall.  And after the r & r, all I did was put in drivers from your site, or where I had the backed up to disk, did Windows updates, and installed my current lineup of programs (most of which come from [www.download.com](www.download.com)), which your techs will see what I have on there once I get Vista up and running.  You can read about my experience with my roommate's Dimension 3000 here, or my experience with my father's Dimension 2400 here, or my experience with this XPS M1330 here.  This and this are links to my help in installing Ubuntu on this laptop, the first one from [www.cybertechhelp.com](www.cybertechhelp.com) and the second one from the Ubuntu Forums.  Dammit....overheating once again.

And if you check, I SHOULD still have warranty on this laptop, and this should NOT be a special case as your rep told me today on chat.  Because the last time this happened about a year ago, I went ahead and purchased the warranty (at a price of three to four-hundred something dollars) as long as it would last...the complete 5 year one, and it goes out in 2012.  Not sure what month, but I know the year is 2012.  Are you telling me that now Dell shows I have no warranty at all on my system?   How you respond to this email, as well as how many problems arise with my pc after it is returned to me, hinges the decision as to if I will EVER buy a Dell product again, and whether or not I should still advise those I know to go with Dell products or not.  At least the last manager I spoke to about this problem tried to buy me off with a gift certificate lol.

Sorry it took so long to get this email to you, but this machine is being really touchy at the moment.  It has already cut off 3 times while writing this email to you, and the only programs I have open are Avast, Firefox, a-Squared, and Speedfan (in which all temps are over 79C now).  Anyway, I will update you asap.

tod   

PS
You said there were drivers for Windows 7 for this laptop.  Any chance you can return it to me with that instead of Vista on there?  I have not played with that OS yet, but Ive heard its leaps and bounds better than Vista. [/QUOTE]

I have not had a reply yet, other than his automatic away from desk till monday auto-reply.  The next is mainly just notifying him that its still overheating.

[QUOTE=Myself]
Ok.  I just finished running all of my cleaners.  When I say cleaners, I am referring to the following, usually done in the following order:

ATF Cleaner
Malwarebytes Antimalware
a-Squared
Avast
Glary Utilities
TFC

I got through most of them last night, and most came up clean, except for the registry cleaner (Glary) and the 2 temp file cleaners (ATF & TFC).  I had one problem with Avast however, but it was nothing new, really.  After finishing a scan with Avast, I realized that Avast would allow me to do a bootscan, so that it can scanned before XP opens and from what I have heard can catch more there than in a regular scan.  Well, I chose to run the bootscan, and while that and that ALONE was running, NOT XP or UBUNTU or ANYTHING else, it overheated once again and cut itself off.  I let it cool down for a few minutes, and then tried it again, and it went through fine and found nothing.  I am now about to reformat and put Vista and Media Direct back on here.  I do have to go out of town tomorrow, so I do not know how much I will get done.  But I will keep you updated.
[/QUOTE]

And in putting Vista back on here, I have ran into a few more problems, and that is basically the topic of the next email.  I swear, not only me, but I swear even this laptop does NOT WANT vista BACK ON HERE!! lol

[QUOTE=Myself]Well, I took out my instructions on reinstalling Media Direct and Vista that were shipped with my laptop, just to make sure I had it as close as possible to the way it was when I received it.  But, as usual, I ran into problems.  I first put the Media Direct cd in, and it 'prepared' my hard disk for the installation.  I assume that what it means by this is that it wiped out the Ubuntu and XP installations, because when I tried to boot afterward, it would not let me into ANY OS.  So I continued with the Vista installation.  I got to the part where it says Copying files... and it flew through that in a second, and then it was at the part where it says Extracting files, and it never goes beyond 0%, and returns the following error:
Windows cannot install required files. The file may be corrupt or missing. Make sure all files required for installation are available, and restart the installation. Error code0x80070017.
I did a seach for it on Google, and found quite a few people having the same problem, for what looked like to me a variety of reasons.  I tried one thing I saw mentioned.  I went to the Dell site, and downloaded the SATA hd drivers to a flash drive in order to upload them during the Vista installation.  But when I got to that part, Vista did not recognize the files at all.  I even took out my old Dell Drivers & Utilities disk that came with it, and none of them would work either.  I have now just got XP back on it, and am going to attempt to install Vista on it, by opening the Vista cd up while XP is already running, i.e. an upgrade.  Well, I will post back with results.
[/QUOTE]

Well, that is where I am at now.  About to get on that pc, and try to install Vista while in XP.  Wish me luck, I guess.  Boy I will be glad when I can install the OS of my choice.

---

