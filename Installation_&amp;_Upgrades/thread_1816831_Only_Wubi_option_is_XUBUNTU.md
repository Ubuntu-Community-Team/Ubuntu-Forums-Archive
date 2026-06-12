---
title: "Only Wubi option is XUBUNTU"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by jfbooth on 2011-08-02
Objective:  Do a Windows/Wubi install of Ubuntu 11.4 to a notebook running Windows XP SP3.

When I download/run the Windows Installer, the only Linux option is XUBUNTU.  Isn't there suppose to be a list of Remix, Kubuntu, Ubuntu, etc, etc in the drop down box?

Thanks in advance.

---

### Post by raja.genupula on 2011-08-02
was it mixed dvd of ubuntu ?

---

### Post by jfbooth on 2011-08-02
> **raja.genupula said:**
> was it mixed dvd of ubuntu ?

Thank you for your reply.

No .. no DVD involved.  It is a WUBI (Windows Installer) install.

If I understand it, WUBI allows me to install "Ubuntu" inside Windows.  I have used it before (Wubi).  Until now, the drop down box listed different "Ubuntus" .. like Xubuntu, Kubuntu, Ubuntu Remix, Ubuntu .. and I could choose the one I want to install.  Then the one I want is downloaded and installed.  This installer download only offers XUBUNTU.

---

### Post by raja.genupula on 2011-08-04
may its developed only for XUBUNTU:D

---

### Post by jfbooth on 2011-08-04
> **raja.genupula said:**
> may its developed only for XUBUNTU:D

Maybe.  There are references 'all over' the 'Net that Wubi allows other versions though.

In fact, a month or so ago, I installed Wubi/Ubuntu 11.04 on a new W7 notebook.

I'm not sure what is going on .. something vastly different about Wubi from a short while ago .. in that (now) it only offers XUBUNTU (see attachment). 

I cannot find any 'documentation' that it has been changed either.

---

### Post by bcbc on 2011-08-04
Do you have a Xubuntu CD in your CD/DVD drive?

Otherwise, post the log file: %temp%\wubi-11.04-rev211.log

---

### Post by jfbooth on 2011-08-04
Thank you (all) for the replies.

> **bcbc said:**
> Do you have a Xubuntu CD in your CD/DVD drive?

I THINK I have it figured out.  I have XUBUNTU .iso on Drive F.  Looks like Wubi is finding THAT.  I renamed it to .iso.foo and tried WUBI again and this time I get ALL the options.

Apparently Wubi looks for .iso files and lets you choose which IF ANY you have.  If you have NONE, then you get the option of installing any of the entire list.  I did not know Wubi works this way.  Thought it downloaded whatever distro I choose FROM Wubi with no regard for existing .isoS.

[Quote}Otherwise, post the log file: %temp%\wubi-11.04-rev211.log[/QUOTE]

```
08-02 11:50 INFO   root: === wubi 11.04 rev211 ===
08-02 11:50 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-02 11:50 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\BM7R1EB5\\wubi[1].exe"']
08-02 11:50 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\data
08-02 11:50 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\bin\7z.exe
08-02 11:50 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-02 11:50 DEBUG  CommonBackend: Fetching basic info...
08-02 11:50 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\BM7R1EB5\wubi[1].exe
08-02 11:50 DEBUG  CommonBackend: platform=win32
08-02 11:50 DEBUG  CommonBackend: osname=nt
08-02 11:50 DEBUG  CommonBackend: language=en_US
08-02 11:50 DEBUG  CommonBackend: encoding=cp1252
08-02 11:50 DEBUG  WindowsBackend: arch=amd64
08-02 11:50 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\data\isolist.ini
08-02 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 11:50 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 11:50 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 11:50 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 11:50 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 11:50 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 11:50 DEBUG  WindowsBackend: Fetching host info...
08-02 11:50 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 11:50 DEBUG  WindowsBackend: windows version=xp
08-02 11:50 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 11:50 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 11:50 DEBUG  WindowsBackend: windows_build=2600
08-02 11:50 DEBUG  WindowsBackend: gmt=-6
08-02 11:50 DEBUG  WindowsBackend: country=US
08-02 11:50 DEBUG  WindowsBackend: timezone=America/Chicago
08-02 11:50 DEBUG  WindowsBackend: windows_username=Owner
08-02 11:50 DEBUG  WindowsBackend: user_full_name=Owner
08-02 11:50 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-02 11:50 DEBUG  WindowsBackend: windows_language_code=1033
08-02 11:50 DEBUG  WindowsBackend: windows_language=English
08-02 11:50 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-02 11:50 DEBUG  WindowsBackend: bootloader=xp
08-02 11:50 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46561.7304688 mb free ntfs)
08-02 11:50 DEBUG  WindowsBackend: drive=Drive(C: hd 46561.7304688 mb free ntfs)
08-02 11:50 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-02 11:50 DEBUG  WindowsBackend: drive=Drive(F: hd 429034.433594 mb free ntfs)
08-02 11:50 DEBUG  WindowsBackend: uninstaller_path=None
08-02 11:50 DEBUG  WindowsBackend: previous_target_dir=None
08-02 11:50 DEBUG  WindowsBackend: previous_distro_name=None
08-02 11:50 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 11:50 DEBUG  WindowsBackend: keyboard_layout=us
08-02 11:50 DEBUG  WindowsBackend: keyboard_variant=
08-02 11:50 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 11:50 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 11:50 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-02 11:50 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 11:50 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-02 11:50 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-02 11:50 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 11:50 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 11:50 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-02 11:50 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 11:50 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 11:50 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-02 11:50 DEBUG  CommonBackend: Searching for local CDs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Ubuntu Netbook CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 11:50 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:50 INFO   root: Running the installer...
08-02 11:50 DEBUG  WindowsFrontend: __init__...
08-02 11:50 DEBUG  WindowsFrontend: on_init...
08-02 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\translations, languages=['en_US', 'en']
08-02 11:50 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl47.tmp\translations, languages=['en_US', 'en']
08-02 11:51 INFO   WindowsFrontend: Operation cancelled
08-02 11:51 DEBUG  WindowsFrontend: frontend.quit
08-02 11:51 DEBUG  WindowsFrontend: frontend.on_quit
08-02 11:51 DEBUG  root: application.on_quit
08-02 11:51 INFO   root: sys.exit
08-02 11:54 INFO   root: === wubi 11.04 rev211 ===
08-02 11:54 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-02 11:54 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\BM7R1EB5\\wubi[2].exe"']
08-02 11:54 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\data
08-02 11:54 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\bin\7z.exe
08-02 11:54 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-02 11:54 DEBUG  CommonBackend: Fetching basic info...
08-02 11:54 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\BM7R1EB5\wubi[2].exe
08-02 11:54 DEBUG  CommonBackend: platform=win32
08-02 11:54 DEBUG  CommonBackend: osname=nt
08-02 11:54 DEBUG  CommonBackend: language=en_US
08-02 11:54 DEBUG  CommonBackend: encoding=cp1252
08-02 11:54 DEBUG  WindowsBackend: arch=amd64
08-02 11:54 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\data\isolist.ini
08-02 11:54 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 11:54 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 11:54 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 11:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 11:54 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 11:54 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 11:54 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 11:54 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 11:54 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 11:54 DEBUG  WindowsBackend: Fetching host info...
08-02 11:54 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 11:54 DEBUG  WindowsBackend: windows version=xp
08-02 11:54 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 11:54 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 11:54 DEBUG  WindowsBackend: windows_build=2600
08-02 11:54 DEBUG  WindowsBackend: gmt=-6
08-02 11:54 DEBUG  WindowsBackend: country=US
08-02 11:54 DEBUG  WindowsBackend: timezone=America/Chicago
08-02 11:54 DEBUG  WindowsBackend: windows_username=Owner
08-02 11:54 DEBUG  WindowsBackend: user_full_name=Owner
08-02 11:54 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-02 11:54 DEBUG  WindowsBackend: windows_language_code=1033
08-02 11:54 DEBUG  WindowsBackend: windows_language=English
08-02 11:54 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-02 11:54 DEBUG  WindowsBackend: bootloader=xp
08-02 11:54 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46591.0625 mb free ntfs)
08-02 11:54 DEBUG  WindowsBackend: drive=Drive(C: hd 46591.0625 mb free ntfs)
08-02 11:54 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-02 11:54 DEBUG  WindowsBackend: drive=Drive(F: hd 429031.238281 mb free ntfs)
08-02 11:54 DEBUG  WindowsBackend: uninstaller_path=None
08-02 11:54 DEBUG  WindowsBackend: previous_target_dir=None
08-02 11:54 DEBUG  WindowsBackend: previous_distro_name=None
08-02 11:54 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 11:54 DEBUG  WindowsBackend: keyboard_layout=us
08-02 11:54 DEBUG  WindowsBackend: keyboard_variant=
08-02 11:54 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 11:54 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 11:54 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-02 11:54 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 11:54 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-02 11:54 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-02 11:54 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 11:54 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 11:54 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-02 11:54 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 11:54 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 11:54 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-02 11:54 DEBUG  CommonBackend: Searching for local CDs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Ubuntu Netbook CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 11:54 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 11:54 INFO   root: Running the installer...
08-02 11:54 DEBUG  WindowsFrontend: __init__...
08-02 11:54 DEBUG  WindowsFrontend: on_init...
08-02 11:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\translations, languages=['en_US', 'en']
08-02 11:54 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl48.tmp\translations, languages=['en_US', 'en']
08-02 11:55 INFO   WindowsFrontend: Operation cancelled
08-02 11:55 DEBUG  WindowsFrontend: frontend.quit
08-02 11:55 DEBUG  WindowsFrontend: frontend.on_quit
08-02 11:55 DEBUG  root: application.on_quit
08-02 11:55 INFO   root: sys.exit
08-02 12:14 INFO   root: === wubi 11.04 rev211 ===
08-02 12:14 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-02 12:14 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\WJFJ9CNQ\\wubi[1].exe"']
08-02 12:14 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\data
08-02 12:14 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\bin\7z.exe
08-02 12:14 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-02 12:14 DEBUG  CommonBackend: Fetching basic info...
08-02 12:14 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\WJFJ9CNQ\wubi[1].exe
08-02 12:14 DEBUG  CommonBackend: platform=win32
08-02 12:14 DEBUG  CommonBackend: osname=nt
08-02 12:14 DEBUG  CommonBackend: language=en_US
08-02 12:14 DEBUG  CommonBackend: encoding=cp1252
08-02 12:14 DEBUG  WindowsBackend: arch=amd64
08-02 12:14 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\data\isolist.ini
08-02 12:14 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 12:14 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 12:14 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 12:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 12:14 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 12:14 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 12:14 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 12:14 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 12:14 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 12:14 DEBUG  WindowsBackend: Fetching host info...
08-02 12:14 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 12:14 DEBUG  WindowsBackend: windows version=xp
08-02 12:14 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 12:14 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 12:14 DEBUG  WindowsBackend: windows_build=2600
08-02 12:14 DEBUG  WindowsBackend: gmt=-6
08-02 12:14 DEBUG  WindowsBackend: country=US
08-02 12:14 DEBUG  WindowsBackend: timezone=America/Chicago
08-02 12:14 DEBUG  WindowsBackend: windows_username=Owner
08-02 12:14 DEBUG  WindowsBackend: user_full_name=Owner
08-02 12:14 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-02 12:14 DEBUG  WindowsBackend: windows_language_code=1033
08-02 12:14 DEBUG  WindowsBackend: windows_language=English
08-02 12:14 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-02 12:14 DEBUG  WindowsBackend: bootloader=xp
08-02 12:14 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46590.9101563 mb free ntfs)
08-02 12:14 DEBUG  WindowsBackend: drive=Drive(C: hd 46590.9101563 mb free ntfs)
08-02 12:14 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-02 12:14 DEBUG  WindowsBackend: drive=Drive(F: hd 429028.230469 mb free ntfs)
08-02 12:14 DEBUG  WindowsBackend: uninstaller_path=None
08-02 12:14 DEBUG  WindowsBackend: previous_target_dir=None
08-02 12:14 DEBUG  WindowsBackend: previous_distro_name=None
08-02 12:14 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 12:14 DEBUG  WindowsBackend: keyboard_layout=us
08-02 12:14 DEBUG  WindowsBackend: keyboard_variant=
08-02 12:14 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 12:14 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 12:14 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-02 12:14 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 12:14 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-02 12:14 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-02 12:14 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 12:14 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 12:14 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-02 12:14 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 12:14 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 12:14 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-02 12:14 DEBUG  CommonBackend: Searching for local CDs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Ubuntu Netbook CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 12:14 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:14 INFO   root: Running the installer...
08-02 12:14 DEBUG  WindowsFrontend: __init__...
08-02 12:14 DEBUG  WindowsFrontend: on_init...
08-02 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\translations, languages=['en_US', 'en']
08-02 12:14 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl49.tmp\translations, languages=['en_US', 'en']
08-02 12:14 INFO   WindowsFrontend: Operation cancelled
08-02 12:14 DEBUG  WindowsFrontend: frontend.quit
08-02 12:14 DEBUG  WindowsFrontend: frontend.on_quit
08-02 12:14 DEBUG  root: application.on_quit
08-02 12:14 INFO   root: sys.exit
08-02 12:15 INFO   root: === wubi 11.04 rev211 ===
08-02 12:15 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-02 12:15 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\WJFJ9CNQ\\wubi[2].exe"']
08-02 12:15 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\data
08-02 12:15 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\bin\7z.exe
08-02 12:15 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-02 12:15 DEBUG  CommonBackend: Fetching basic info...
08-02 12:15 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\WJFJ9CNQ\wubi[2].exe
08-02 12:15 DEBUG  CommonBackend: platform=win32
08-02 12:15 DEBUG  CommonBackend: osname=nt
08-02 12:15 DEBUG  CommonBackend: language=en_US
08-02 12:15 DEBUG  CommonBackend: encoding=cp1252
08-02 12:15 DEBUG  WindowsBackend: arch=amd64
08-02 12:15 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\data\isolist.ini
08-02 12:15 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 12:15 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 12:15 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 12:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 12:15 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 12:15 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 12:15 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 12:15 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 12:15 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 12:15 DEBUG  WindowsBackend: Fetching host info...
08-02 12:15 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 12:15 DEBUG  WindowsBackend: windows version=xp
08-02 12:15 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 12:15 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 12:15 DEBUG  WindowsBackend: windows_build=2600
08-02 12:15 DEBUG  WindowsBackend: gmt=-6
08-02 12:15 DEBUG  WindowsBackend: country=US
08-02 12:15 DEBUG  WindowsBackend: timezone=America/Chicago
08-02 12:15 DEBUG  WindowsBackend: windows_username=Owner
08-02 12:15 DEBUG  WindowsBackend: user_full_name=Owner
08-02 12:15 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-02 12:15 DEBUG  WindowsBackend: windows_language_code=1033
08-02 12:15 DEBUG  WindowsBackend: windows_language=English
08-02 12:15 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-02 12:15 DEBUG  WindowsBackend: bootloader=xp
08-02 12:15 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46590.7773438 mb free ntfs)
08-02 12:15 DEBUG  WindowsBackend: drive=Drive(C: hd 46590.7773438 mb free ntfs)
08-02 12:15 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-02 12:15 DEBUG  WindowsBackend: drive=Drive(F: hd 429026.769531 mb free ntfs)
08-02 12:15 DEBUG  WindowsBackend: uninstaller_path=None
08-02 12:15 DEBUG  WindowsBackend: previous_target_dir=None
08-02 12:15 DEBUG  WindowsBackend: previous_distro_name=None
08-02 12:15 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 12:15 DEBUG  WindowsBackend: keyboard_layout=us
08-02 12:15 DEBUG  WindowsBackend: keyboard_variant=
08-02 12:15 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 12:15 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 12:15 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-02 12:15 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 12:15 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-02 12:15 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-02 12:15 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 12:15 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 12:15 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-02 12:15 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 12:15 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 12:15 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-02 12:15 DEBUG  CommonBackend: Searching for local CDs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Ubuntu Netbook CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 12:15 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 12:15 INFO   root: Running the installer...
08-02 12:15 DEBUG  WindowsFrontend: __init__...
08-02 12:15 DEBUG  WindowsFrontend: on_init...
08-02 12:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\translations, languages=['en_US', 'en']
08-02 12:15 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl4A.tmp\translations, languages=['en_US', 'en']
08-02 12:34 INFO   WindowsFrontend: Operation cancelled
08-02 12:34 DEBUG  WindowsFrontend: frontend.quit
08-02 12:34 DEBUG  WindowsFrontend: frontend.on_quit
08-02 12:34 DEBUG  root: application.on_quit
08-02 12:34 INFO   root: sys.exit
08-02 22:46 INFO   root: === wubi 11.04 rev211 ===
08-02 22:46 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-02 22:46 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\EIY31TNY\\wubi[1].exe"']
08-02 22:46 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\data
08-02 22:46 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\bin\7z.exe
08-02 22:46 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-02 22:46 DEBUG  CommonBackend: Fetching basic info...
08-02 22:46 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\EIY31TNY\wubi[1].exe
08-02 22:46 DEBUG  CommonBackend: platform=win32
08-02 22:46 DEBUG  CommonBackend: osname=nt
08-02 22:46 DEBUG  CommonBackend: language=en_US
08-02 22:46 DEBUG  CommonBackend: encoding=cp1252
08-02 22:46 DEBUG  WindowsBackend: arch=amd64
08-02 22:46 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\data\isolist.ini
08-02 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-02 22:46 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-02 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-02 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-02 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-02 22:46 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-02 22:46 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-02 22:46 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-02 22:46 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-02 22:46 DEBUG  WindowsBackend: Fetching host info...
08-02 22:46 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-02 22:46 DEBUG  WindowsBackend: windows version=xp
08-02 22:46 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-02 22:46 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-02 22:46 DEBUG  WindowsBackend: windows_build=2600
08-02 22:46 DEBUG  WindowsBackend: gmt=-6
08-02 22:46 DEBUG  WindowsBackend: country=US
08-02 22:46 DEBUG  WindowsBackend: timezone=America/Chicago
08-02 22:46 DEBUG  WindowsBackend: windows_username=Owner
08-02 22:46 DEBUG  WindowsBackend: user_full_name=Owner
08-02 22:46 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-02 22:46 DEBUG  WindowsBackend: windows_language_code=1033
08-02 22:46 DEBUG  WindowsBackend: windows_language=English
08-02 22:46 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-02 22:46 DEBUG  WindowsBackend: bootloader=xp
08-02 22:46 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46593.2890625 mb free ntfs)
08-02 22:46 DEBUG  WindowsBackend: drive=Drive(C: hd 46593.2890625 mb free ntfs)
08-02 22:46 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-02 22:46 DEBUG  WindowsBackend: drive=Drive(F: hd 428801.191406 mb free ntfs)
08-02 22:46 DEBUG  WindowsBackend: uninstaller_path=None
08-02 22:46 DEBUG  WindowsBackend: previous_target_dir=None
08-02 22:46 DEBUG  WindowsBackend: previous_distro_name=None
08-02 22:46 DEBUG  WindowsBackend: keyboard_id=67699721
08-02 22:46 DEBUG  WindowsBackend: keyboard_layout=us
08-02 22:46 DEBUG  WindowsBackend: keyboard_variant=
08-02 22:46 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-02 22:46 DEBUG  CommonBackend: locale=en_US.UTF-8
08-02 22:46 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-02 22:46 DEBUG  CommonBackend: Searching ISOs on USB devices
08-02 22:46 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-02 22:46 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-02 22:46 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 22:46 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-02 22:46 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-02 22:46 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 22:46 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-02 22:46 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-02 22:46 DEBUG  CommonBackend: Searching for local CDs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Ubuntu Netbook CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-02 22:46 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-02 22:46 INFO   root: Running the installer...
08-02 22:46 DEBUG  WindowsFrontend: __init__...
08-02 22:46 DEBUG  WindowsFrontend: on_init...
08-02 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\translations, languages=['en_US', 'en']
08-02 22:46 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl8E.tmp\translations, languages=['en_US', 'en']
08-02 22:46 INFO   WindowsFrontend: Operation cancelled
08-02 22:46 DEBUG  WindowsFrontend: frontend.quit
08-02 22:46 DEBUG  WindowsFrontend: frontend.on_quit
08-02 22:46 DEBUG  root: application.on_quit
08-02 22:46 INFO   root: sys.exit
08-04 11:28 INFO   root: === wubi 11.04 rev211 ===
08-04 11:28 DEBUG  root: Logfile is c:\docume~1\owner\locals~1\temp\wubi-11.04-rev211.log
08-04 11:28 DEBUG  root: sys.argv = ['main.pyo', '--exefile="F:\\Temporary Internet Files\\Content.IE5\\4BTU60RS\\wubi[1].exe"']
08-04 11:28 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\data
08-04 11:28 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\bin\7z.exe
08-04 11:28 DEBUG  WindowsBackend: startup_folder=C:\Documents and Settings\All Users\Start Menu\Programs\Startup
08-04 11:28 DEBUG  CommonBackend: Fetching basic info...
08-04 11:28 DEBUG  CommonBackend: original_exe=F:\Temporary Internet Files\Content.IE5\4BTU60RS\wubi[1].exe
08-04 11:28 DEBUG  CommonBackend: platform=win32
08-04 11:28 DEBUG  CommonBackend: osname=nt
08-04 11:28 DEBUG  CommonBackend: language=en_US
08-04 11:28 DEBUG  CommonBackend: encoding=cp1252
08-04 11:28 DEBUG  WindowsBackend: arch=amd64
08-04 11:28 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\data\isolist.ini
08-04 11:28 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
08-04 11:28 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
08-04 11:28 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
08-04 11:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
08-04 11:28 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
08-04 11:28 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
08-04 11:28 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
08-04 11:28 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
08-04 11:28 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
08-04 11:28 DEBUG  WindowsBackend: Fetching host info...
08-04 11:28 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
08-04 11:28 DEBUG  WindowsBackend: windows version=xp
08-04 11:28 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
08-04 11:28 DEBUG  WindowsBackend: windows_sp=Service Pack 3
08-04 11:28 DEBUG  WindowsBackend: windows_build=2600
08-04 11:28 DEBUG  WindowsBackend: gmt=-6
08-04 11:28 DEBUG  WindowsBackend: country=US
08-04 11:28 DEBUG  WindowsBackend: timezone=America/Chicago
08-04 11:28 DEBUG  WindowsBackend: windows_username=Owner
08-04 11:28 DEBUG  WindowsBackend: user_full_name=Owner
08-04 11:28 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Owner
08-04 11:28 DEBUG  WindowsBackend: windows_language_code=1033
08-04 11:28 DEBUG  WindowsBackend: windows_language=English
08-04 11:28 DEBUG  WindowsBackend: processor_name=AMD Turion(tm) 64 X2 Mobile Technology TL-60
08-04 11:28 DEBUG  WindowsBackend: bootloader=xp
08-04 11:28 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46307.0234375 mb free ntfs)
08-04 11:28 DEBUG  WindowsBackend: drive=Drive(C: hd 46307.0234375 mb free ntfs)
08-04 11:28 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
08-04 11:28 DEBUG  WindowsBackend: drive=Drive(F: hd 428474.949219 mb free ntfs)
08-04 11:28 DEBUG  WindowsBackend: uninstaller_path=None
08-04 11:28 DEBUG  WindowsBackend: previous_target_dir=None
08-04 11:28 DEBUG  WindowsBackend: previous_distro_name=None
08-04 11:28 DEBUG  WindowsBackend: keyboard_id=67699721
08-04 11:28 DEBUG  WindowsBackend: keyboard_layout=us
08-04 11:28 DEBUG  WindowsBackend: keyboard_variant=
08-04 11:28 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
08-04 11:28 DEBUG  CommonBackend: locale=en_US.UTF-8
08-04 11:28 DEBUG  WindowsBackend: total_memory_mb=893.97265625
08-04 11:28 DEBUG  CommonBackend: Searching ISOs on USB devices
08-04 11:28 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  WindowsBackend:   extracting .disk\info from F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  Distro:   parsing info from str=Xubuntu 11.04 "Natty Narwhal" - Release i386 (20110427)
08-04 11:28 DEBUG  Distro:   parsed info={'name': 'Xubuntu', 'subversion': 'Release', 'version': '11.04', 'build': '20110427', 'codename': 'Natty Narwhal', 'arch': 'i386'}
08-04 11:28 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-04 11:28 DEBUG  Distro:   checking Ubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  Distro: wrong name: Xubuntu != Ubuntu
08-04 11:28 DEBUG  Distro:   checking Ubuntu Netbook ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  Distro: wrong name: Xubuntu != Ubuntu Netbook
08-04 11:28 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-04 11:28 DEBUG  Distro:   checking Kubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  Distro: wrong name: Xubuntu != Kubuntu
08-04 11:28 DEBUG  Distro:   checking Xubuntu ISO F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 INFO   Distro: Found a valid iso for Xubuntu: F:\xubuntu-11.04-desktop-i386.iso
08-04 11:28 DEBUG  CommonBackend: Searching for local CDs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Ubuntu Netbook CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
08-04 11:28 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
08-04 11:28 INFO   root: Running the installer...
08-04 11:28 DEBUG  WindowsFrontend: __init__...
08-04 11:28 DEBUG  WindowsFrontend: on_init...
08-04 11:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\translations, languages=['en_US', 'en']
08-04 11:28 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Owner\LOCALS~1\Temp\pyl125.tmp\translations, languages=['en_US', 'en']
08-04 11:29 INFO   WindowsFrontend: Operation cancelled
08-04 11:29 DEBUG  WindowsFrontend: frontend.quit
08-04 11:29 DEBUG  WindowsFrontend: frontend.on_quit
08-04 11:29 DEBUG  root: application.on_quit
08-04 11:29 INFO   root: sys.exit

```

Viewing the log tipped me off as to the problem, so I thank you for your reply .. it solved the thread.

---

