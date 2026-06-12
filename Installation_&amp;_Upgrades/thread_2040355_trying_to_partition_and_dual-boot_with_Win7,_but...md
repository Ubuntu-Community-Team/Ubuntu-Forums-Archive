---
title: "trying to partition and dual-boot with Win7, but..."
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by MagicalGirl on 2012-08-10
Hi!
I just bought a laptop for college, which came with Windows 7 and 750GB of hard drive space, and I'd like to dual-boot it with Ubuntu. I'm trying to partition because I understand that that's how you have two OS's on one hard drive.
The computer came with four partitions already:
SYSTEM_DRV, which is a "Healthy (System, Active, Primary Partition)," 
Windows7_OS, which is a "Healthy (Boot, Page File, Crash Dump, Primary Partition),"
"LENOVO, which is a "Healthy (Primary Partition),"
and a nameless one which is a "Healthy (OEM Partition)." 
At the advice of one of my friends, I shrank Windows7_OS and intended to make that space into a new partition for Ubuntu.
The Ubuntu installer lists this space as "unusable." Windows Disk Manager simply calls it "unallocated," and offers to let me turn it into a New Simple Volume, then warns me that this will "convert the selected basic disk(s) to dynamic disk(s)," and I "will not be able to start installed operating systems from any volume on the disk(s) (except the current boot volume)." Then it tells me there's not enough space.
Am I not allowed to have more than four partitions? Should I have told Disk Manager to format the volume? (It only offers me NTFS and exFAT.)
Apparently I'm supposed to get an Install Ubuntu Alongside Your Previous Operating System option when I start, but I just get an Erase Your Disk And Install Ubuntu Instead option and Something Else.
Besides crying, what should I try?
Thank you!

---

### Post by oldfred on 2012-08-11
The MBR(msdos) partitioning only allows 4 primary partitions. That goes back to the original hard drive on a PC in the 1980's. They soon realized that is not enough and you can make one of the 4 primaries an extended partition that then can hold many logical partitions. But if you use all 4 then you cannot make the extended.

Do not use Windows to create dynamic partitions. That is a one-way conversion, does not work with LInux and does not work with all the Windows repair tools.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

A lot of the discussion is for HP but all vendors seem to do the same thing. 

Best to make backups and a Windows repairCD.

Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)


The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

