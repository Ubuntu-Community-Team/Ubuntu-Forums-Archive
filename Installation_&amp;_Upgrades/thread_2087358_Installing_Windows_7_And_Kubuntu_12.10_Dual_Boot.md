---
title: "Installing Windows 7 And Kubuntu 12.10 Dual Boot"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by zenarcher on 2012-11-23
I am trying to install Kubuntu 12.10 in dual boot on a Presario CQ57 laptop.  The laptop is brand new and has Windows 7 installed on it.

When I attempt to install Kubuntu from either the Live CD or the Alternate Install disk, when I reach the partitioning point, the Windows 7 installation does not appear as an option, so I can install the two systems on the same hard drive.  The only options I am given are to use the entire hard drive.  That would delete Windows 7 completely and leave me with just Kubuntu.  The hard drive is 208GB in size, so there is plenty of unused space and I have defragmented Windows.

I tried my Kubuntu 12.04 install disk and have the same situation....the Windows 7 install is not found by the Kubuntu installer.

Can anyone help me out with a way to have both Kubuntu 12.10 and Windows 7 dual boot on the same system?  I have not encountered this issue on any previous dual boot installs.

Thanks,
zenarcher

---

### Post by 2F4U on 2012-11-23
How many partitions do you already have on that system? My guess is that you already have 4 primary partitons, which unfortunately is the maximum.

---

### Post by zenarcher on 2012-11-23
> **2F4U said:**
> How many partitions do you already have on that system? My guess is that you already have 4 primary partitons, which unfortunately is the maximum.

Thanks.  It appears you are correct.  There are the following:

C:                     209.34GB
HP_Tools (E:)               3.96GB
Recovery (D:)               19.38GB
System                 199GB

Would I be able to get rid of one of those primary partitions without destroying Windows 7 and get enough room to do a decent Kubuntu install that you know of?

Thanks,
zenarcher

---

### Post by oldfred on 2012-11-23
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

The only reason for a recovery set of DVDs is if you ever wanted to sell computer and new owner wants Windows. Better to do a full backup after houseclean cruft and shrinking partition. Also Windows repair disk is important.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by zer010 on 2013-02-27
Thank you for all of this great info, oldfred!  I've been running *buntu on a desktop for a few years and I'm quite adept at installing to a secondary drive, especially alongside WinXP.  However when I got my new laptop(specs in sig), I was a little puzzled.

---

