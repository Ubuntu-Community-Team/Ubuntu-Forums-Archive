---
title: "Installing Ubuntu on pre-partitioned External HDD"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by LinearMelee on 2013-07-14
Hey everyone, first post is a newb question so i apologise!

I have one internal hardrive, and due to the way i have built this system (HTPC) i can't add another - even though i have several lying around - and this HDD already has four needed partitions (i beilieve this is the maximum for a NTFS HDD?).

To get around this, i dug up a 1TB External HDD, and thought "Hey i could partition this up and install Ubuntu(<3) on it!".

So basically, with this(img_1) partition setup(where disk 1 is external HDD pre partitioned), can i install ubuntu under this single partition?

Thanks for all answers! Don't be afraid to tell me straight up if installing it on a ext hdd isn't possible, but i'd really like to install it on there so if there is a way, please tell me about it!



IMG_1: [IMG]http://puu.sh/3CVvE.png[/IMG]

---

### Post by oldfred on 2013-07-14
You can install to an external drive and boot from that, if system allows booting from USB drives. Most newer systems do.

But you can install to internal drive by converting one of the 4 primary partitions to an extended partition and then create as many logical partitions as you want inside the extended.

But you have greatly complicated things by creating more than 4 partitions with Windows. It does not use the extended but converts to a proprietary logical partitioning scheme which does not work with Linux. Even if you install Ubuntu to external it will not see the dynamic partitions with Windows.

       
Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

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

---

### Post by LinearMelee on 2013-07-15
Thankyou for such a detailed response! Sorry mine is late, been asleep!

I understand what you're saying however i'm starting to think that it may be easier to shrink my D drive back into my C drive and therefore the Ubuntu(X) drive will be seen as the forth partition. 

Is this a plausible idea? I've literally just woken up so it may be stupid, but thanks for reading.

---

### Post by oldfred on 2013-07-15
The change of d: back into c:'s data may be required so you have a 4th partition to convert to the extended partition, but you have to undo the dynamic partitions to get any Linux to work on your system.

---

