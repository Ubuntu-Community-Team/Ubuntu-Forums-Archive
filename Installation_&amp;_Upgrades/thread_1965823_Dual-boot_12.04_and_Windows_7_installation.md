---
title: "Dual-boot 12.04 and Windows 7 installation"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by duranl on 2012-04-26
I'm trying to dual-boot 12.04 and Windows 7.  However, when I boot from the Ubuntu CD to install it, I only have the options to "install inside Windows 7", "replace Windows 7 with Ubuntu" or "something else".

Is there a way to install Ubuntu 12.04 so it can dual-boot instead of running inside of Windows?

Computer: HP Pavilion dv6-6c12nr

---

### Post by darkod on 2012-04-26
Yes, but HP are idiots and ship their laptops with all four partitions used. That is why the option "along side windows" is missing because a fifth partition can't be created.

You need to delete one partition. DO NOT touch the small system reserved partition, it has win7 boot files on it and you can not delete it.

The choice is between the HP_TOOLS partition or the restore partition. Or both.

With the software on the laptop you should be able to create a set of restore DVDs and in that case you don't need the restore partition any more. If in future you want to restore to factory setup, you can use the DVDs.

In any case, you will probably need to shrink the main win7 partition to make space for ubuntu. Do that with windows Disk Management, not with the slider in the ubuntu installer. Shrink it in windows and reboot it few times because it can be confused after the shrink sometimes.
Then you can start the ubuntu install.

---

### Post by duranl on 2012-04-26
I may have just screwed myself.  Before reading your post, I tried to create another partition to use the "do something else" option and install it like that.  This made my drive dynamic.  Is there anyway to reverse this without having to restore the entire hard drive to the factory setting?  I did not create any restore points.



Yes, I know I'm being stupid.  I will try to stop that.

---

### Post by darkod on 2012-04-26
Yes, there is, but I don't have bookmarked the tools.

There was one like Partition Wizard or similar (not Partition Magic). Try google for how to convert back to basic disk without data loss.

---

### Post by oldfred on 2012-04-26
I saved some links. Besure to have good back ups. Microsoft's offical policy is to backup, totally erase drive and restore data. They make it easy to go one way but not the other.

Best to delete the empty partition(s) you created, or the conversions may make incorrect logical partitions.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

Used EASEUS Partition Master -  free version includes conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)

---

### Post by duranl on 2012-04-27
Made the recovery discs which took a long time.  Installed EASEUS Partition Manager and used that to make the drive basic and remove the HP_Tools and Recovery partitions.  This program is amazing!  Afterward, booted off of the Ubuntu 12.04 cd to install and the option to install alongside Windows was there.  Everything worked out.  Thanks!

---

### Post by oldfred on 2012-04-27
Glad you got it working.

If you did not make a Windows repair cd or USB flash, you should do that also. It is always best to have repairCDs or liveCDs of the current version of every operating system you have installed. With Ubuntu you have the liveCD or USB you used to install.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

