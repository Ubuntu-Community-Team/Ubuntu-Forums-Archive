---
title: "Ubuntu not recognising multiple partitions on a pre-populated drive"
date: 2017-04-24
forum: Installation &amp; Upgrades
---

### Post by ihavenoideawhatiamdoing2 on 2017-04-24
Hi, I am trying to install ubuntu as a dual boot on a partitioned secondary drive. However the Ubuntu install wizard doesn't recognise the drive as being partitioned, due to one of the partitions already being full of programs for my main OS (windows) I cannot just overwrite the drive.
Does anyone know how to solve this?

EDIT: I have discovered that this is a dynamic drive, I think this stops me from being able to do this?

---

### Post by wildmanne39 on 2017-04-24
*Thread moved to **Installation & Upgrades**.*

---

### Post by TheFu on 2017-04-24
GPT/MBR partitioning?
How many partitions and what types are they?  Primary, Extended, or Logical?
How much empty space is available on the drive?

A comfortable Linux install needs 2 partitions, a) 15G-25G b) 4G for swap.  This doesn't include storage for much data.
Linux cannot use NTFS for FAT-whatever partition formats. It must have Linux file system formats, ext4 is the default and a good choice for 99% of people today.

So, if you can answer those first 3 questions, we might be able to help.

---

### Post by Geoffrey_Arndt on 2017-04-24
Yes to what the OP said . . . re dynamic drive(s).     Also, if Windows is still set to "fast/quick start" . . . the partitions are not seen and accessible.

Really is best, safest to have Windows on it's own machine, and Linux on it's own (or lacking that option, to run either Linux or Windows in a Virtual Machine (such as Oracle's Virtual Box) . . . OR . . . to install Linux on an external usb SSD (see SanDisk 500 Extreme on Amazon).

---

### Post by oldfred on 2017-04-24
You have to undo the dynamic partitions and restore to basic partitions.

 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005) 
   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

