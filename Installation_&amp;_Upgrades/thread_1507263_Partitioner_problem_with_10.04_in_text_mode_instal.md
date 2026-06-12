---
title: "Partitioner problem with 10.04 in text mode install"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by kabal4u on 2010-06-11
Because of various errors and problems with the installation I finally tried to do it in Text mode. However when I reach the part with partitioning my drives the Partitioner always gets stuck at 33%. Tried it over few times, different options, normal install just in case, but no results. Here are some screenshots, a bit improvised though...

[http://img38.imagefra.me/img/img38/6/6/11/kabal4u/f_1cnw37ua2kqm_46426ed.jpg]("http://img38.imagefra.me/img/img38/6/6/11/kabal4u/f_1cnw37ua2kqm_46426ed.jpg")

[http://img37.imagefra.me/img/img37/6/6/11/kabal4u/f_1cnw37ua2kpm_10af64b.jpg]("http://img37.imagefra.me/img/img37/6/6/11/kabal4u/f_1cnw37ua2kpm_10af64b.jpg")

No matter what options i choose for the partitioner I'm always stuck here.

After that it seems I'll be left with two options, a netboot or updating my BIOS to be able to boot from USB drives. Which, are going to be a bit too much for my knowledge and skills.

I would greatly appreciate if someone can refer me to a clear guide how to partition my second hard drive ( I have curently 2 drives one is 80GB partitioned into C: and D: with WinXP in C, and the second drive 160GB that is no longer visible in Windows ) if of course the problem is there?!?

Any other suggestions are also welcomed!?! :confused:

Thank you in advance for your time.

---

### Post by dino99 on 2010-06-11
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by kabal4u on 2010-06-11
Thanks a lot. I'll try this immediately. Hope it finally works :/

---

### Post by kabal4u on 2010-06-13
Jeez no luck again. I've read some pretty extensive FAQs on partitioning, wrote the software but I can't boot from the CD.

Well I asked for help on the PartedMagic forum I'll wait for an answer few more days, and eventually I may try to deal with it trough the LVM partitioner in text mode...

I decided to try another approach, install Wubi and than partition my drive, that also failed though O_o

This is the log file, if someone can interpret it?

```
06-13 13:32 DEBUG  CommonBackend: original_exe=E:\wubi.exe
06-13 13:32 DEBUG  CommonBackend: platform=win32
06-13 13:32 DEBUG  CommonBackend: osname=nt
06-13 13:32 DEBUG  CommonBackend: language=bg_BG
06-13 13:32 DEBUG  CommonBackend: encoding=cp1251
06-13 13:32 DEBUG  WindowsBackend: arch=i386
06-13 13:32 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\data\isolist.ini
06-13 13:32 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-13 13:32 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-13 13:32 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-13 13:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-13 13:32 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-13 13:32 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-13 13:32 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-13 13:32 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-13 13:32 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-13 13:32 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-13 13:32 DEBUG  WindowsBackend: Fetching host info...
06-13 13:32 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-13 13:32 DEBUG  WindowsBackend: windows version=xp
06-13 13:32 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-13 13:32 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-13 13:32 DEBUG  WindowsBackend: windows_build=2600
06-13 13:32 DEBUG  WindowsBackend: gmt=2
06-13 13:32 DEBUG  WindowsBackend: country=US
06-13 13:32 DEBUG  WindowsBackend: timezone=America/New_York
06-13 13:32 DEBUG  WindowsBackend: windows_username=Kaal Atan
06-13 13:32 DEBUG  WindowsBackend: user_full_name=Kaal Atan
06-13 13:32 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Kaal Atan
06-13 13:32 DEBUG  WindowsBackend: windows_language_code=1026
06-13 13:32 DEBUG  WindowsBackend: windows_language=Bulgarian
06-13 13:32 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.40GHz
06-13 13:32 DEBUG  WindowsBackend: bootloader=xp
06-13 13:32 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30481.7070313 mb free ntfs)
06-13 13:32 DEBUG  WindowsBackend: drive=Drive(C: hd 30481.7070313 mb free ntfs)
06-13 13:32 DEBUG  WindowsBackend: drive=Drive(D: hd 30980.8359375 mb free ntfs)
06-13 13:32 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-13 13:32 DEBUG  WindowsBackend: uninstaller_path=None
06-13 13:32 DEBUG  WindowsBackend: previous_target_dir=None
06-13 13:32 DEBUG  WindowsBackend: previous_distro_name=None
06-13 13:32 DEBUG  WindowsBackend: keyboard_id=67699721
06-13 13:32 DEBUG  WindowsBackend: keyboard_layout=us
06-13 13:32 DEBUG  WindowsBackend: keyboard_variant=
06-13 13:32 DEBUG  CommonBackend: python locale=('bg_BG', 'cp1251')
06-13 13:32 DEBUG  CommonBackend: locale=bg_BG.UTF-8
06-13 13:32 DEBUG  WindowsBackend: total_memory_mb=2046.796875
06-13 13:32 DEBUG  CommonBackend: Searching ISOs on USB devices
06-13 13:32 DEBUG  CommonBackend: Searching for local CDs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Ubuntu Netbook CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Kubuntu Netbook CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Xubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp is a valid Mythbuntu CD
06-13 13:32 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-13 13:32 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-13 13:32 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
06-13 13:32 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-13 13:32 DEBUG  Distro: wrong arch: i386 != amd64
06-13 13:32 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-13 13:32 INFO   Distro: Found a valid CD for Ubuntu: E:\
06-13 13:32 INFO   root: Running the CD menu...
06-13 13:32 DEBUG  WindowsFrontend: __init__...
06-13 13:32 DEBUG  WindowsFrontend: on_init...
06-13 13:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:32 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1C.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:32 INFO   root: CD menu finished
06-13 13:32 DEBUG  CommonBackend: Showing info
06-13 13:32 DEBUG  root: application.quit
06-13 13:32 DEBUG  WindowsFrontend: frontend.quit
06-13 13:32 DEBUG  WindowsFrontend: frontend.on_quit
06-13 13:32 DEBUG  root: application.on_quit
06-13 13:32 INFO   root: sys.exit
06-13 13:33 INFO   root: === wubi 10.04 rev189 ===
06-13 13:33 DEBUG  root: Logfile is c:\docume~1\kaalat~1\locals~1\temp\wubi-10.04-rev189.log
06-13 13:33 DEBUG  root: sys.argv = ['main.pyo', '--exefile="E:\\wubi.exe"']
06-13 13:33 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\data
06-13 13:33 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\bin\7z.exe
06-13 13:33 DEBUG  CommonBackend: Fetching basic info...
06-13 13:33 DEBUG  CommonBackend: original_exe=E:\wubi.exe
06-13 13:33 DEBUG  CommonBackend: platform=win32
06-13 13:33 DEBUG  CommonBackend: osname=nt
06-13 13:33 DEBUG  CommonBackend: language=bg_BG
06-13 13:33 DEBUG  CommonBackend: encoding=cp1251
06-13 13:33 DEBUG  WindowsBackend: arch=i386
06-13 13:33 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\data\isolist.ini
06-13 13:33 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
06-13 13:33 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
06-13 13:33 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
06-13 13:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
06-13 13:33 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
06-13 13:33 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
06-13 13:33 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
06-13 13:33 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
06-13 13:33 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
06-13 13:33 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
06-13 13:33 DEBUG  WindowsBackend: Fetching host info...
06-13 13:33 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
06-13 13:33 DEBUG  WindowsBackend: windows version=xp
06-13 13:33 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
06-13 13:33 DEBUG  WindowsBackend: windows_sp=Service Pack 2
06-13 13:33 DEBUG  WindowsBackend: windows_build=2600
06-13 13:33 DEBUG  WindowsBackend: gmt=2
06-13 13:33 DEBUG  WindowsBackend: country=US
06-13 13:33 DEBUG  WindowsBackend: timezone=America/New_York
06-13 13:33 DEBUG  WindowsBackend: windows_username=Kaal Atan
06-13 13:33 DEBUG  WindowsBackend: user_full_name=Kaal Atan
06-13 13:33 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Kaal Atan
06-13 13:33 DEBUG  WindowsBackend: windows_language_code=1026
06-13 13:33 DEBUG  WindowsBackend: windows_language=Bulgarian
06-13 13:33 DEBUG  WindowsBackend: processor_name=                Intel(R) Celeron(R) CPU 2.40GHz
06-13 13:33 DEBUG  WindowsBackend: bootloader=xp
06-13 13:33 DEBUG  WindowsBackend: system_drive=Drive(C: hd 30481.3242188 mb free ntfs)
06-13 13:33 DEBUG  WindowsBackend: drive=Drive(C: hd 30481.3242188 mb free ntfs)
06-13 13:33 DEBUG  WindowsBackend: drive=Drive(D: hd 30980.8359375 mb free ntfs)
06-13 13:33 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
06-13 13:33 DEBUG  WindowsBackend: uninstaller_path=None
06-13 13:33 DEBUG  WindowsBackend: previous_target_dir=None
06-13 13:33 DEBUG  WindowsBackend: previous_distro_name=None
06-13 13:33 DEBUG  WindowsBackend: keyboard_id=67699721
06-13 13:33 DEBUG  WindowsBackend: keyboard_layout=us
06-13 13:33 DEBUG  WindowsBackend: keyboard_variant=
06-13 13:33 DEBUG  CommonBackend: python locale=('bg_BG', 'cp1251')
06-13 13:33 DEBUG  CommonBackend: locale=bg_BG.UTF-8
06-13 13:33 DEBUG  WindowsBackend: total_memory_mb=2046.796875
06-13 13:33 DEBUG  CommonBackend: Searching ISOs on USB devices
06-13 13:33 DEBUG  CommonBackend: Searching for local CDs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Ubuntu Netbook CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Kubuntu Netbook CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Xubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp is a valid Mythbuntu CD
06-13 13:33 DEBUG  Distro:     does not contain C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
06-13 13:33 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
06-13 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-13 13:33 DEBUG  Distro:   parsing info from str=Ubuntu 10.04 LTS "Lucid Lynx" - Release i386 (20100429)
06-13 13:33 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '10.04', 'build': '20100429', 'codename': 'Lucid Lynx', 'arch': 'i386'}
06-13 13:33 DEBUG  Distro: wrong arch: i386 != amd64
06-13 13:33 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
06-13 13:33 INFO   Distro: Found a valid CD for Ubuntu: E:\
06-13 13:33 INFO   root: Running the CD menu...
06-13 13:33 DEBUG  WindowsFrontend: __init__...
06-13 13:33 DEBUG  WindowsFrontend: on_init...
06-13 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:33 INFO   root: CD menu finished
06-13 13:33 INFO   root: Running the CD boot helper...
06-13 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:33 INFO   root: CD boot helper confirmed
06-13 13:33 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\translations, languages=['bg_BG', 'bg']
06-13 13:33 DEBUG  TaskList: # Running tasklist...
06-13 13:33 DEBUG  TaskList: ## Running select_target_dir...
06-13 13:33 INFO   WindowsBackend: Installing into C:\ubuntu
06-13 13:33 DEBUG  TaskList: ## Finished select_target_dir
06-13 13:33 DEBUG  TaskList: ## Running create_dir_structure...
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
06-13 13:33 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
06-13 13:33 DEBUG  TaskList: ## Finished create_dir_structure
06-13 13:33 DEBUG  TaskList: ## Running uncompress_target_dir...
06-13 13:33 DEBUG  TaskList: ## Finished uncompress_target_dir
06-13 13:33 DEBUG  TaskList: ## Running create_uninstaller...
06-13 13:33 DEBUG  WindowsBackend: Copying uninstaller E:\wubi.exe -> C:\ubuntu\uninstall-wubi.exe
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu.ico
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
06-13 13:33 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
06-13 13:33 DEBUG  TaskList: ## Finished create_uninstaller
06-13 13:33 DEBUG  TaskList: ## Running copy_installation_files...
06-13 13:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
06-13 13:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\winboot -> C:\ubuntu\winboot
06-13 13:33 DEBUG  WindowsBackend: Copying C:\DOCUME~1\KAALAT~1\LOCALS~1\Temp\pyl1E.tmp\data\images\Ubuntu.ico -> C:\ubuntu\Ubuntu.ico
06-13 13:33 DEBUG  TaskList: ## Finished copy_installation_files
06-13 13:33 DEBUG  TaskList: ## Running use_cd...
06-13 13:33 DEBUG  TaskList: New task copy_file
06-13 13:33 DEBUG  TaskList: ### Running copy_file...
06-13 13:40 ERROR  TaskList: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-13 13:40 DEBUG  TaskList: # Cancelling tasklist
06-13 13:40 ERROR  root: [Errno 13] Permission denied
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 128, in select_task
  File "\lib\wubi\application.py", line 194, in run_cd_menu
  File "\lib\wubi\application.py", line 120, in select_task
  File "\lib\wubi\application.py", line 217, in run_cd_boot
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\utils.py", line 209, in copy_file
IOError: [Errno 13] Permission denied
06-13 13:40 DEBUG  TaskList: New task check_iso
06-13 13:40 DEBUG  TaskList: ## Finished use_cd
06-13 13:40 DEBUG  TaskList: # Finished tasklist
```

---

### Post by darkod on 2010-06-13
It is unlikely, but did you try to burn a new cd at low speed, not higher than 8x? Also, maybe even downloading new image from torrent (torrent software checks for corruption during download).

---

### Post by kabal4u on 2010-06-13
I've always burn CDs DVDs in lowest speed possible. The DVD I use now was burned on another PC at low speed, I also burned a CD, no matter where or how I burn the CD/DVD it's the same. :/

---

### Post by darkod on 2010-06-13
Boot into live mode with the cd/dvd and in terminal execute:

sudo fdisk -l

What does that say about the disks?

---

### Post by kabal4u on 2010-06-13
I have managed to install Ubuntu through Wubi... without trouble... from one of the first CDs i wrote, however after I select it the loading screen for Ubuntu pops up and freezes. 

I will try to tho what you recommended anyways, because I wanna see will I be able to do anything at all with the boot CD now. So far It wasn't possible for me to install, install trough text mode or try Ubuntu.

Nope the same case, whatever option I choose ( install, try, check disk ) I always end up with the same error there

> Busy Box v1.13.3 ( Ubuntu 1 s1.13.3-1ubuntu11 ) built-in shell (ash) 
Enter "help" for a list of commands
(iniramfs) Unable to find a medium containing a live file system

Which was the initial problem that forced me to seek different solutions. However at least i have made an installation with Wubi, one problem is resolved and the other pops up...

I'll look-up the forums to see if there is a solution to this one...

---

### Post by darkod on 2010-06-13
If live mode (Try Ubuntu) can't work there is probably some hardware incompatibility. Which ever way you install, it won't work. Probably that's why even wubi can't boot up.

You can try to boot with the cd, hit any key while the splash screen is shown, to get a menu displayed. Then hit F6 for advanced option and try Safe Graphics first.

If that doesn't help load live mode, you could try highlighting the Try Ubuntu entry, but hit 'e', not Enter. It should display the booting commands. Move to the end of the line starting with linux and delete quiet splash, add nomodeset. Press Ctrl+X to boot and see if that helped.

Depending which added parameter helped you boot into live mode, there should be way to add it permanently later and the system to work.

---

### Post by kabal4u on 2010-06-13
Yes it probably is the hardware, I've already tried 3-4 Linux distributions. In the end I decided "Well since nothing works, let's make Ubuntu work..."

I have tried most of the options even the ones under F6, however it's always possible that I missed something. I will try all these again, I mean the ones you've suggested.

And of course thanks for the help and your time :)

_Edit:_ the result is the same, it doesn't work <.<

I've edited the line as the instructions provided say, but after the text appears and starts moving at different spots it stops, I can start it again with alt+F4 but after some time it stops again...

for example with the settings you sugested it stops here:

> [ 14.166850] [<c01033ec>] syscall_call +0x7/0xb

_EDIT2_: I'm sick with this... I'll try a previous release Karmic maybe...
3 days and all that's done is nothing O_o

---

### Post by kabal4u on 2010-07-07
Well I managed to accidentally figure out which component caused the problem. My 6-7 year old motherboard crashed totally. Now with the new one running I managed to install xubuntu but I guess any distribution or release can be installed without problems.

Thanks for the suggestions and help so far everyone :)

---

