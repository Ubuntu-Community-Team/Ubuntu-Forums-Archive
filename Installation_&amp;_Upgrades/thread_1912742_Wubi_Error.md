---
title: "Wubi Error"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by edskins on 2012-01-21
Hi guys,

I'm trying to install ubuntu 11.10 on the Wubi installer and is coming up with an error (see screenshot). Pretty new at this so would appreciated some help....

Thanks,

---

### Post by sffvba[e0rt on 2012-01-21
Very fuzzy and small... can't really read the error.

But I did manage to see something about checking an error log that was created.  Could you paste its content here for us?


404

---

### Post by edskins on 2012-01-21
The log file is massive so here is the last few lines:



```
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/EDSBE~1/AppData/Local/Temp/pylA101.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]
```

---

### Post by edskins on 2012-01-21
another screenshot...

---

### Post by sffvba[e0rt on 2012-01-21
I am not finding anything specific on this issue.  

I have seen many people advocating downloading the Ubuntu ISO file, as well as the stand alone wubi executable, placing them in the same folder on Windows and then running the executable to install that way.

Not sure if that is required or will even work.

There is a wubi mega-thread, perhaps I could merge your thread with it to accelerate the guru's seeing your problem?


404

---

### Post by bcbc on 2012-01-21
If you're installing on a fat partition (is D: FAT32?) then wubi won't work due to bug [lpbug]882393[/lpbug].

Instead install on an NTFS partition, or use the 11.04 or 10.04 version of Wubi. Find them here: [http://releases.ubuntu.com/11.04/](http://releases.ubuntu.com/11.04/) or here: [http://releases.ubuntu.com/10.04/](http://releases.ubuntu.com/10.04/)

If D: isn't a FAT32 drive, then maybe it didn't completely download the 'preinstalled-image'. Can you post a few lines above what you posted where it states how many bytes were downloaded please? (Or the entire log file).

---

### Post by edskins on 2012-01-23
I have windows 7 currently installed so don't think it would be FAT32? The same error comes up if I also try to install on C drive so don't think it's to do with which drive I want ubuntu on.

More of the log file below:-



```
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 INFO   root: Already installed, running the uninstaller...
01-21 11:51 INFO   root: Running the uninstaller...
01-21 11:51 INFO   CommonBackend: This is the uninstaller running
01-21 11:51 DEBUG  WindowsFrontend: __init__...
01-21 11:51 DEBUG  WindowsFrontend: on_init...
01-21 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\translations, languages=['en_GB', 'en']
01-21 11:51 INFO   root: Received settings
01-21 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\translations, languages=['en_GB', 'en']
01-21 11:51 DEBUG  TaskList: # Running tasklist...
01-21 11:51 DEBUG  TaskList: ## Running Remove bootloader entry....
01-21 11:51 DEBUG  WindowsBackend: Could not find bcd id
01-21 11:51 DEBUG  WindowsBackend: undo_bootini C:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 427571.929688 mb free ntfs)
01-21 11:51 DEBUG  WindowsBackend: undo_bootini D:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 681413.972656 mb free ntfs)
01-21 11:51 DEBUG  WindowsBackend: undo_bootini F:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(F: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: undo_bootini G:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(G: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: undo_bootini H:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(H: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: undo_bootini I:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(I: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: undo_bootini J:
01-21 11:51 DEBUG  WindowsBackend: undo_configsys Drive(J: removable 0.0 mb free )
01-21 11:51 DEBUG  TaskList: ## Finished Remove bootloader entry.
01-21 11:51 DEBUG  TaskList: ## Running Remove target dir....
01-21 11:51 DEBUG  CommonBackend: Deleting C:\ubuntu
01-21 11:51 DEBUG  TaskList: ## Finished Remove target dir.
01-21 11:51 DEBUG  TaskList: ## Running Remove registry key....
01-21 11:51 DEBUG  TaskList: ## Finished Remove registry key.
01-21 11:51 DEBUG  TaskList: # Finished tasklist
01-21 11:51 INFO   root: Almost finished uninstalling
01-21 11:51 INFO   root: Finished uninstallation
01-21 11:51 DEBUG  CommonBackend: Fetching basic info...
01-21 11:51 DEBUG  CommonBackend: original_exe=C:\Users\Ed's Beast\Downloads\wubi.exe
01-21 11:51 DEBUG  CommonBackend: platform=win32
01-21 11:51 DEBUG  CommonBackend: osname=nt
01-21 11:51 DEBUG  WindowsBackend: arch=amd64
01-21 11:51 DEBUG  CommonBackend: Parsing isolist=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\data\isolist.ini
01-21 11:51 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
01-21 11:51 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
01-21 11:51 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
01-21 11:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
01-21 11:51 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
01-21 11:51 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
01-21 11:51 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
01-21 11:51 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
01-21 11:51 DEBUG  WindowsBackend: Fetching host info...
01-21 11:51 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
01-21 11:51 DEBUG  WindowsBackend: windows version=vista
01-21 11:51 DEBUG  WindowsBackend: windows_version2=Windows 7 Home Premium
01-21 11:51 DEBUG  WindowsBackend: windows_sp=None
01-21 11:51 DEBUG  WindowsBackend: windows_build=7601
01-21 11:51 DEBUG  WindowsBackend: gmt=0
01-21 11:51 DEBUG  WindowsBackend: country=GB
01-21 11:51 DEBUG  WindowsBackend: timezone=Europe/London
01-21 11:51 DEBUG  WindowsBackend: windows_username=Ed's Beast
01-21 11:51 DEBUG  WindowsBackend: user_full_name=Ed's Beast
01-21 11:51 DEBUG  WindowsBackend: user_directory=C:\Users\Ed's Beast
01-21 11:51 DEBUG  WindowsBackend: windows_language_code=1033
01-21 11:51 DEBUG  WindowsBackend: windows_language=English
01-21 11:51 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM) i7 CPU         860  @ 2.80GHz
01-21 11:51 DEBUG  WindowsBackend: bootloader=vista
01-21 11:51 DEBUG  WindowsBackend: system_drive=Drive(C: hd 429795.414063 mb free ntfs)
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(C: hd 429795.414063 mb free ntfs)
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(D: hd 681413.972656 mb free ntfs)
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(F: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(G: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(H: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(I: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: drive=Drive(J: removable 0.0 mb free )
01-21 11:51 DEBUG  WindowsBackend: uninstaller_path=None
01-21 11:51 DEBUG  WindowsBackend: previous_target_dir=None
01-21 11:51 DEBUG  WindowsBackend: previous_distro_name=None
01-21 11:51 DEBUG  WindowsBackend: keyboard_id=134809609
01-21 11:51 DEBUG  WindowsBackend: keyboard_layout=gb
01-21 11:51 DEBUG  WindowsBackend: keyboard_variant=
01-21 11:51 DEBUG  WindowsBackend: total_memory_mb=4095.99999905
01-21 11:51 DEBUG  CommonBackend: Searching ISOs on USB devices
01-21 11:51 DEBUG  CommonBackend: Searching for local CDs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 INFO   root: Running the installer...
01-21 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\translations, languages=['en_GB', 'en']
01-21 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\translations, languages=['en_GB', 'en']
01-21 11:51 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=18000MB, distro_name=Ubuntu, language=en_GB, locale=en_GB.UTF-8, username=ed
01-21 11:51 INFO   root: Received settings
01-21 11:51 DEBUG  CommonBackend: Searching for local CD
01-21 11:51 DEBUG  Distro:   checking whether C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
01-21 11:51 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
01-21 11:51 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
01-21 11:51 DEBUG  CommonBackend: Searching for local ISO
01-21 11:51 DEBUG  Distro:   checking Ubuntu ISO C:\Users\Ed's Beast\Downloads\linuxmint-12-gnome-cd-nocodecs-64bit.iso
01-21 11:51 DEBUG  WindowsBackend:   extracting .disk\info from C:\Users\Ed's Beast\Downloads\linuxmint-12-gnome-cd-nocodecs-64bit.iso
01-21 11:51 DEBUG  Distro:   parsing info from str=Linux Mint 12 "Lisa" - Release amd64 (20111120)

01-21 11:51 DEBUG  Distro:   parsed info={'name': 'Linux Mint', 'subversion': 'Release', 'version': '12', 'build': '20111120', 'codename': 'Lisa', 'arch': 'amd64'}
01-21 11:51 DEBUG  Distro: wrong name: Linux Mint != Ubuntu
01-21 11:51 INFO   WinuiPage: appname=wubi, localedir=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\translations, languages=['en_GB', 'en']
01-21 11:51 DEBUG  TaskList: # Running tasklist...
01-21 11:51 DEBUG  TaskList: ## Running select_target_dir...
01-21 11:51 INFO   WindowsBackend: Installing into D:\ubuntu
01-21 11:51 DEBUG  TaskList: ## Finished select_target_dir
01-21 11:51 DEBUG  TaskList: ## Running create_dir_structure...
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
01-21 11:51 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
01-21 11:51 DEBUG  TaskList: ## Finished create_dir_structure
01-21 11:51 DEBUG  TaskList: ## Running create_uninstaller...
01-21 11:51 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Ed's Beast\Downloads\wubi.exe -> D:\ubuntu\uninstall-wubi.exe
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 11.10-rev245
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
01-21 11:51 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
01-21 11:51 DEBUG  TaskList: ## Finished create_uninstaller
01-21 11:51 DEBUG  TaskList: ## Running create_preseed_diskimage...
01-21 11:51 DEBUG  TaskList: ## Finished create_preseed_diskimage
01-21 11:51 DEBUG  TaskList: ## Running get_diskimage...
01-21 11:51 DEBUG  TaskList: New task download
01-21 11:51 DEBUG  TaskList: ### Running download...
01-21 11:51 DEBUG  downloader: downloading [http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz](http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz) > D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz
01-21 11:51 DEBUG  downloader: Download start filename=D:\ubuntu\disks\ubuntu-11.10-wubi-amd64.tar.xz, url=http://releases.ubuntu.com/11.10/ubuntu-11.10-wubi-amd64.tar.xz, basename=ubuntu-11.10-wubi-amd64.tar.xz, length=507143012, text=None
01-21 11:56 DEBUG  TaskList: ### Finished download
01-21 11:56 DEBUG  downloader: download finished (read 507143012 bytes)
01-21 11:56 DEBUG  TaskList: ## Finished get_diskimage
01-21 11:56 DEBUG  TaskList: ## Running extract_diskimage...
01-21 11:57 DEBUG  TaskList: ## Finished extract_diskimage
01-21 11:57 DEBUG  TaskList: ## Running choose_disk_sizes...
01-21 11:57 DEBUG  WindowsBackend: total size=18000
  root=17744
  swap=256
  home=0
  usr=0
01-21 11:57 DEBUG  TaskList: ## Finished choose_disk_sizes
01-21 11:57 DEBUG  TaskList: ## Running expand_diskimage...
01-21 11:57 ERROR  TaskList: Error executing command
>>command=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/EDSBE~1/AppData/Local/Temp/pylA101.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/EDSBE~1/AppData/Local/Temp/pylA101.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]


01-21 11:57 DEBUG  TaskList: # Cancelling tasklist
01-21 11:57 DEBUG  TaskList: # Finished tasklist
01-21 11:57 ERROR  root: Error executing command
>>command=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/EDSBE~1/AppData/Local/Temp/pylA101.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]

Traceback (most recent call last):
  File "\lib\wubi\application.py", line 58, in run
  File "\lib\wubi\application.py", line 132, in select_task
  File "\lib\wubi\application.py", line 158, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 461, in expand_diskimage
  File "\lib\wubi\backends\common\utils.py", line 66, in run_command
Exception: Error executing command
>>command=C:\Users\ED'SBE~1\AppData\Local\Temp\pylA101.tmp\bin\resize2fs.exe -f D:\ubuntu\disks\root.disk 17744M
>>retval=1
>>stderr=
>>stdout=resize2fs 1.40.6 (09-Feb-2008)
Usage: /cygdrive/c/Users/EDSBE~1/AppData/Local/Temp/pylA101.tmp/bin/resize2fs.exe -f D:/ubuntu/disks/root.disk 17744M [-d debug_flags] [-f] [-F] [-p] device [new_size]
```

---

### Post by edskins on 2012-01-23
Also I have downloaded the image a few times and comes up with the same errors....

---

### Post by bcbc on 2012-01-23
That's not something I've seen before. You can [register that as a bug]("https://bugs.launchpad.net/wubi/+filebug") (attach the log file please), and then use an alternate approach to installing:

Download the CD Desktop ISO and wubi.exe into the same folder. Run wubi from there. Get them from the same location - for 11.10 you can download directly from ubuntu.com or go to:
[http://releases.ubuntu.com/11.10](http://releases.ubuntu.com/11.10)

This will install Wubi but instead of downloading a 'preinstalled' compressed disk image it will use the ISO to run the ubuntu installer and install to the virtual disk directly. (If that makes sense :) )
At any rate that will avoid the need to run resize2fs on Windows. 

PS please also let me know your graphics card type - it won't affect anything - but some cards (nvidia) don't boot without an override option so I hope to avoid you some more hassle if that's the case.

---

