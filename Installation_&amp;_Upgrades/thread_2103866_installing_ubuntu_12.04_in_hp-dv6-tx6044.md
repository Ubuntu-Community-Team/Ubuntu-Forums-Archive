---
title: "installing ubuntu 12.04 in hp-dv6-tx6044"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2013-01-11
My friend was trying to install ubuntu in dual boot with windows in his laptop mentioned above. But he got in some problem and had to stop it. Now his windows has also crashed and so he is not able to boot into his pc. i will try to recover it through the boot-repair software. But earlier to that he had tried to install ubuntu many times but it only showed a blank screen and it told that there are missing drivers. Why is this so? I've also tried to install ubuntu in laptops of my friends, but sometimes it doesn't installs at all.
Any specific reasons for it? The specs of the laptop of my friend is:
cpu: intel i5 2nd gen
ram: ddr3 4gb
hdd: 500gb
graphics card: ati radeon ddr5 1 gb HD64 series.

---

### Post by oldfred on 2013-01-11
Is this a newer Windows 7, Some were installed in UEFI mode, but do not have the secure boot issues that Windows 8 has.

Are you installing 64 bit version? Is system an UltraBook? That has Intel SRT which uses RAID (somehow??) and that causes issues. 
Did you create partitions in Windows? That will convert partitions to dynamic or SFS which does not work with Linux and does not always work right with Windows repair tools.

Best to post link BootInfo report.

---

### Post by malakar.subhendu on 2013-01-11
Thanks for the reply. For the answers:
He had the pre-installed version of windows 7 and had updated it.
Yes it was 64-bit OS. 
No it was not an ultrabook.
don't know about the intel SRT or RAID part
He had created partitions in windows and had made it dynamic.
Can it be repaired by the boot-repair software?
How to get the bootinfo report as it is not possible to boot in the machine although he can run the linux mint-13 through live cd. Anything can be done now?

---

### Post by oldfred on 2013-01-11
Dynamic is a problem. Microsoft's official solution is a full backup, erase & repartition & restore data. But some third party Windows tools may convert. But you really need to be back to no more than four partitions.
The free versions seem to be converted to only the paid version may work with conversion of dynamic. Other software sites may have the older free version.

         Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.

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

   Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)


Another new issue
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

