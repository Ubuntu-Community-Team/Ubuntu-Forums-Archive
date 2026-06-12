---
title: "Need help for custom partitioning!"
date: 2016-07-20
forum: Installation &amp; Upgrades
---

### Post by jijibu on 2016-07-20
Hello, I have Sony laptopo with UEFI support and Windows installed. C: and D: disks, with important information on D:. I want to erase C: and install Ubuntu on it. Please, tell me which parameters should I use in `something else` to create partition for Ubuntu with UEFI boot, while keeping D: disk untouched and automatically mounted on startup.

---

### Post by yancek on 2016-07-20
Boot the Ubuntu installation DVD/flash drive and select the "Try Ubuntu" option.  When it boots to the Desktop, open a terminal and enter this command:  sudo fdisk -l(Lower Case Letter L in the command)  This will output device and partition information in Linux terminology so post it here.  You need to select the correct partition to format so you don't overwrite your data partition.

---

### Post by oldfred on 2016-07-21
Unless you have Windows best not to keep a NTFS partition. 
You can only run chkdsk from Windows, not Linux and Windows NTFS will need chkdsk periodically or when it gets corrupted.

Many that delete Windows later find one application or game and want to re-install Windows. Best then to have a full back up that you can restore.

At the very least if you erase Windows make the Windows repair flash drive, so you can run repairs on the NTFS partition.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[URL="http://www.runtime.org/driveimage-xml.htm"]http://www.runtime.org/driveimage-xml.htm

      [/URL]
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)
Manually create repair flash, shows files & locations
[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools) 
    [URL="http://www.runtime.org/driveimage-xml.htm"]
[/URL]

---

### Post by jijibu on 2016-07-21
I know how to use custom partitioning, but need advice in some partitions, how much for EFI boot, root, swap (4GB ram, choosing 4 GB, no need for more swap) etc.

---

### Post by oldfred on 2016-07-21
Partitioning is very personal depending on what you want.
I find even my optimal scheme is not so good a few years later.

System will not let me post all my typical links. 
Most are in link in my signature below.

---

### Post by mook765 on 2016-07-24
one partition for root ( 25 to 30 GB for x 64 should do it )
one Partition for swap ( 4GB is ok for your system )
one partition for home ( size up to you, i don't know how much space is available on your harddrive )
that's it...
don't forget to backup your system as well as your data first...

---

