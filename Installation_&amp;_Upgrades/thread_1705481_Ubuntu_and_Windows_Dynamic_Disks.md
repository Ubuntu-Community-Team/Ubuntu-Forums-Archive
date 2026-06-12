---
title: "Ubuntu and Windows Dynamic Disks"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by vincix on 2011-03-12
I can't seem to be able to install Ubuntu Desktop 10.10 after converting my disks to dynamic (in Windows 7) in order to mirror some partitions. I have two hdds, one of 1TB and the other of 500GB. In order to mirrror one partition of about 400GB i had to convert both disks to dynamic. The problem now is that Ubuntu isn't able to distinguish between the partitions and can't identify free space either. The entire 1TB hdd (on which I left some 50GB free space) is seen as a single partition.

Any suggestions to this problem?

Thanks

---

### Post by oldfred on 2011-03-12
No.

Windows dynamic disks are a big problem to anything other than windows and even some windows tools do not work with dynamic disks.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)
To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it. 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by srs5694 on 2011-03-12
If you're using features like mirroring, I'd be even more wary of using TestDisk to convert from "dynamic" to "basic" format.

Your easiest and safest solution at this point is probably to add a new hard disk for Linux.

---

### Post by oldfred on 2011-03-12
+1 on srs5694's suggestion for another drive.

Windows official policy is to back up entire drive and erase it. Then create new 'basic' partitions.  

You have two drives converted. So it will be difficult to convert back and there is always some risk modifying partitions.

---

