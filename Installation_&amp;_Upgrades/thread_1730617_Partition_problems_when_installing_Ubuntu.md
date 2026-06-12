---
title: "Partition problems when installing Ubuntu"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by Lauryca on 2011-04-16
I want to install Ubuntu on a 30 Gb partition. I attached the structure of hard drive under Win 7 and under Ubuntu instalation program. Why the 30 Gb partition in invisible under Ubuntu instalation program,  and how could I install Ubuntu on it?

---

### Post by coffeecat on 2011-04-16
It looks as though you have tried to create a fifth primary partition from within Windows and since this is impossible in an mbr partition table, Windows will convert all the partitions into so-called dynamic ones. This is a Windows-only standard and can be a real problem.

To see if this is so, boot up the Ubuntu live CD and open a terminal (Applications > Administration). Post the output of this command:

```
sudo fdisk -lu
```Please enclose the output between [noparse] ```
 and 
```[/noparse] tags for legibility.

---

### Post by Lauryca on 2011-04-16
```
  ubuntu@ubuntu:~$ sudo fdisk -lu
   
   
   
  Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
   
  255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
   
  Units = sectors of 1 * 512 = 512 bytes
   
  Sector size (logical/physical): 512 bytes / 512 bytes
   
  I/O size (minimum/optimal): 512 bytes / 512 bytes
   
  Disk identifier: 0xf96c7e30
   
   
   
     Device Boot      Start         End      Blocks   Id  System
   
  /dev/sda1              63        2047         992+  42  SFS
   
  Partition 1 does not end on cylinder boundary.
   
  /dev/sda2   *        2048      206847      102400   42  SFS
   
  Partition 2 does not end on cylinder boundary.
   
  /dev/sda3          206848   209715199   104754176   42  SFS
   
  /dev/sda4       209715200  1953523119   871903960   42  SFS
   
   
   
  Disk /dev/sdb: 8086 MB, 8086617600 bytes
   
  255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
   
  Units = sectors of 1 * 512 = 512 bytes
   
  Sector size (logical/physical): 512 bytes / 512 bytes
   
  I/O size (minimum/optimal): 512 bytes / 512 bytes
   
  Disk identifier: 0x91f72d24
   
   
   
     Device Boot      Start         End      Blocks   Id  System
   
  /dev/sdb1   *          63    15794174     7897056    b  W95 FAT32
   
  Partition 1 has different physical/logical endings:
   
       phys=(982, 254, 63) logical=(983, 36, 12)
   
  ubuntu@ubuntu:~$ 


```
I know that to convert a dynamic to a basic disk I have to loode all the information on the hard drive.

If I install Ubuntu on an existing partition the instalation program won't erase my existing data?

---

### Post by coffeecat on 2011-04-16
Yes SFS = dynamic partition, which is a problem.

I have no experience of dynamic partitions, so the best advice I can give you is in oldfred's post #5 in this thread:

[http://ubuntuforums.org/showthread.php?t=1727673](http://ubuntuforums.org/showthread.php?t=1727673)

As a general principle, you need to be using the Gparted partitioner on the Ubuntu live CD to set up Linux partitions. Three main reasons. This would avoid this dynamic disc problem; you need Gparted to create partitions with Linux fileystems (Windows cannot do that); and Gparted is so much more flexible for setting up extended and logical partitions, which are a far better solution than dynamic partitions to the four primary partition limit in a MBR partition table.

It looks as though you had four primary partitions on your HD originally. This is not uncommon, especially with HP machines, and the only real workaround when you want to install Linux is to delete one primary partition and replace it with an extended partition.

Hopefully, someone with experience of dealing with dynamic partitions will post, but in the meantime you might find this link informative:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by oldfred on 2011-04-16
I do not have any experience in converting. And any conversion like this from some window unique proprietary system has risks. Be sure to have good backups.

I would delete the empty partition using windows, so then you only have 4, which still is an issue. Testdisk may work since the remaining partition look in sequence so they may be recoverable back to basic.

How full are your partitions and can you at least temporarily move data off. You will need to delete one more partition to make it an extended partition. In the extended partition you can make many logical partitions and copy your other data back if you desire.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)


Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)

---

### Post by Lauryca on 2011-04-17
I solved the problem - this message is written under Ubuntu. This is how I did it.

First I merged partiton E and H - from Windows 7 capture.
Then I used  MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk. It worked - I also did back-up of al my data.
I also used Partition Wizard to set an existing partition logical instead of primary and  then I created a new primary partition for Ubuntu. The last step was installing Ubuntu.

Thanks for help. So you can recommend MiniTool Partition Wizard Professional Edition 5.2 for converting dynamic disks to basic disks without loss of data.

---

### Post by coffeecat on 2011-04-17
> **Lauryca said:**
> First I merged partiton E and H - from Windows 7 capture.
Then I used  MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk. It worked - I also did back-up of al my data.
I also used Partition Wizard to set an existing partition logical instead of primary and  then I created a new primary partition for Ubuntu. The last step was installing Ubuntu.

Thanks for posting this. Most people on this forum would  use Gparted as their partitioner of choice (I guess) and therefore wouldn't have experience of dynamic disks and how to convert them back. This is very useful.

I'm glad you've solved the problem, and have successfully installed Ubuntu. Good luck!

---

