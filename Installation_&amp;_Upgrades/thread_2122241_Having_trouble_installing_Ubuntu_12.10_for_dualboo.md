---
title: "Having trouble installing Ubuntu 12.10 for dualboot with Windows 7"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by AJ4 on 2013-03-04
So I downloaded Ubuntu 12.10 to a dvd, restarted the computer and started the installation. But when I got to the screen where the tutorial told me I should be presented with the option 'Install Ubuntu alongside Windows 7' it only says 'replace Windows' (which I do NOT want to do) or 'Something else'. So, like the newbie I am I followed a separate guide for installing it using the 'something else' involving partitioning the hard drive. It told me to change the mbs of the /dev/sda Windows was on, which would show up as free space after, which I would partition and install Ubuntu on. Instead, it says 'unusable' and back on windows my OS_Install (C:) drive has shrunk to 102 GB from about 180. Is this reversible, and if so, how? And how can I install Ubuntu once and for all without screwing up my system. Also, I tried installing it from Windows with wubi but it froze 3/4 of the way through at 'almost finished copying files'. Please help, and know that I am fairly new to this. I have a msi laptop with a 64-bit OS, if it helps.

---

### Post by JLeon85 on 2013-03-04
You should still see that space in the partition manager on Windows, and you can make a partition out of it there. I would defragment the whole drive first though.  

Also, I would recommend going with the 32-bit version of the Ubuntu Secure Remix for a dual-boot setup. It might save you lot of headaches.

[http://sourceforge.net/p/linux-secure/wiki/Home/](http://sourceforge.net/p/linux-secure/wiki/Home/)

---

### Post by arpanaut on 2013-03-04
Usually if the install alongside option is not there it is an indication that you have used up the 4 primary partition limit of bios based systems.
Many OEM's use all 4 by default, so you would need to delete one of the partitions to have the ability to make a new partition for Ubuntu.

Be careful if using Win disk management, because if you try to make more than 4 partitions there it will convert  the disks to dyamic disks which is a Windows only format and Linux will not be able to use the disk at all.

> Also, I would recommend going with the 32-bit version of the Ubuntu  Secure Remix for a dual-boot setup. It might save you lot of headaches.
Why, not an issue these days, use 32 bit on 32 bit systems, 64 bit on 64 bit systems, a few years ago this was true, not anymore.

@OP Boot into the live cd/usb and select "try" to get to a live session and in a terminal (ctrl+alt+t) copy and paste
```
sudo fdisk -lu
``` then copy and past the result back here so we can see how your system is partitioned.

Added info check info in this post: [http://ubuntuforums.org/showthread.php?t=1743331&p=10739560&viewfull=1#post10739560](http://ubuntuforums.org/showthread.php?t=1743331&p=10739560&viewfull=1#post10739560)

---

### Post by JLeon85 on 2013-03-04
> **arpanaut said:**
>  Why, not an issue these days, use 32 bit on 32 bit systems, 64 bit on 64 bit systems, a few years ago this was true, not anymore.

I don't know, I thought it was still an issue. All I can say is I'm running 32 bit Lubuntu on a 64 bit system, and it has been by far the most stable Linux installation I've ever had.

---

### Post by AJ4 on 2013-03-04
Okay, I think I see what you mean. There are four primary partitions, but I haven't really gone into Windows disk management so hopefully they aren't dynamic. Here's what I got:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xda22e49b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    25167871    12582912   27  Hidden NTFS WinRE
/dev/sda2   *    25167872    25372671      102400   27  Hidden NTFS WinRE
/dev/sda3        25372672   240216421   107421875    7  HPFS/NTFS/exFAT
/dev/sda4       387749888   625139711   118694912    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 

How do I know which partition to delete? And, well, how? Thanks for the help.

---

### Post by oldfred on 2013-03-04
Often the vendor tools is just a small partition and does not do much. Or it is easy to back or copy into Windows partition. If you really want it then you can also create a small partition of the same size in the extended partition as a logical. Some have reported that it still works. 

Best to use Windows to shrink Windows NTFS partition & reboot several times so it can run chkdsk and make other fixes to its new size. Then you can install Ubuntu. If you only want / (root) and swap it will just auto install to the unallocated space. But if you want a separate /home and a separate NTFS shared data partition you will need to use manual partitioning to choose sizes, formats and what is mounted in each partition.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]http://forums.techarena.in/guides-tutorials/1114725.htm
      [/URL]
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
[URL="http://forums.techarena.in/guides-tutorials/1114725.htm"]
[/URL]

---

### Post by AJ4 on 2013-03-04
Sorry, but I'm not sure I'm following you. Which is vendor tools? Per the instructions of a guide I believe I shrunk /dev/sda3 (in Ubuntu) which resulted in about 70 gb unallocated memory. I have rebooted since then and found no changes. Do I need to delete a partition and create a new one from the unallocated disk space?

---

### Post by oldfred on 2013-03-04
Have you rebooted Windows after its shrink. Better to do changes to NTFS partitions in Windows with Windows disk tools, but not use Windows to create any partitions. Windows has to run chkdsk and other repairs after a resize and gparted usually works, but better to use Windows as some have had issues.

Yes, you only can have four primary partitions. So you have to delete one. Then you can create a new extended partition which is a primary but special as it can hold an unlimited number of logical partitions. Windows only boots from primary partitions, but Linux works just fine from logicals.

       [URL="https://help.ubuntu.com/community/WindowsDualBoot"]https://help.ubuntu.com/community/WindowsDualBoot

[/URL]
 Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendors that have used 4 primary partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

[URL="https://help.ubuntu.com/community/WindowsDualBoot"]
[/URL]

---

