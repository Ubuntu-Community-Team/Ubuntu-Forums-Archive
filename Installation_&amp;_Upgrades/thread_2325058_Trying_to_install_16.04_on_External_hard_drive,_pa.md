---
title: "Trying to install 16.04 on External hard drive, partition alignment error"
date: 2016-05-18
forum: Installation &amp; Upgrades
---

### Post by dhruv7 on 2016-05-18
I'm an ubuntu newbie, trying to install Ubuntu 16.04 onto an external hard drive, and I'm running the installer off a bootable flash drive. When I reach the stage where I have to create new partitions for the / and swap, i remove all the current partitions from the drive and make space only for the / and swap. When I click continue, I get this error message "The partition /dev/sdb1 assigned to / starts at an offset of 3584 bytes from the minimum alignment for this disk, which may lead to very poor performance.   Since you are formatting this partition, you should correct this problem now by realigning the partition, as it will be difficult to change later. To do this, go back to the main partitioning menu, delete the partition, and recreate it in the same position with the same settings. This will cause the partition to start at a point best suited for this disk."
Whether or not I choose to Go Back or Continue, It takes me back to the partitioning screen and I can't move forward. I read somewhere about how this has something to do with sector sizes on the hard drive, but I couldn't understand how to resolve it. How do I align the partition correctly/resolve this issue?

---

### Post by ubfan1 on 2016-05-18
Try a starting block for the partition at 2048 if the default is 512.  I suppose a start of 4096 would be good too.  What start block does fdisk -l /dev/sdx list?

---

### Post by oldfred on 2016-05-18
UEFI or BIOS based system? Or then really gpt or MBR partitioning.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
sudo parted /dev/sda unit s print

---

### Post by dhruv7 on 2016-05-19
fdisk -l /dev/sdb gives me:
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt


How would I go about changing the starting block for the partition?

---

### Post by ubfan1 on 2016-05-19
Use gdisk instead of fdisk for gpt disks.  Then you should get a partition list with start/ends.  There are tools to move/resize partitions, but If you don't have anything of value on the disk (anywhere on the disk), you can just use gdisk to delete the old ones and make new partitions.

---

