---
title: "Problems dual booting ubuntu 13.04 windows 8 (64bit)"
date: 2013-07-14
forum: Installation &amp; Upgrades
---

### Post by yichentohjoel on 2013-07-14
i have a laptop wtih a nvidia video card and an intel integrated graphics card i decided to use a bootable usb stick to install ubuntu alongside windows 8 (my computer came with windows 7)  unfortunately when i clicked install alongside windows 8 it crashed and restarted. here is my boot info
 [http://paste.ubuntu.com/5873243/](http://paste.ubuntu.com/5873243/)

---

### Post by oldfred on 2013-07-14
Your partitions are showing as SFS which in Windows is dynamic partitions. That does not work with Linux and does not even work with some Windows repair tools. It uses some sort of logical partitioning as an overlay over the physical partitions. Usually that happens if you try to create more than the four allowed primary partitions in Windows. Better to create an extended partition with many logical partitions.

Windows official policy is to back everything up erase drive, repartition and restore data. But even with some of the third party tools you need to have all you data backed up. 

          Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")
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

---

