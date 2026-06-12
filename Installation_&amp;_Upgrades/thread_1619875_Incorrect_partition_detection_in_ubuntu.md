---
title: "Incorrect partition detection in ubuntu"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Shishant on 2010-11-12
Hello,


I bought the new harddisk so for dual boot installed win7 1st and now ubuntu but ubuntu is not detecting my harddisk correctly.

This is screenshot of win7 [http://i52.tinypic.com/v83nyp.png](http://i52.tinypic.com/v83nyp.png) which is actual harddisk partitions (j: is usb drive)


Volume I: (exFat) is where I am planning to install ubuntu, I had fromatted it to exFat hoping if ubuntu detects it.

This is what detected by ubuntu:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8177cf6

Device Boot Start End Blocks Id System
/dev/sda1 1 1 1014+ 42 SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 1 13 102400 42 SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3 13 26122 209715200 42 SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4 26122 121602 766942936 42 SFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 4043 MB, 4043284480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000ac20

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1018 3944719 c W95 FAT32 (LBA)
```

---

### Post by ezsit on 2010-11-12
> Volume I: (exFat) is where I am planning to install ubuntu, I had fromatted it to exFat hoping if ubuntu detects it.

If you created and formatted a partition as FAT, then Ubuntu will not see a place to install. Delete the partition and leave the space as unpartitioned. Ubuntu installer will then see some free space to install into.

Also, I notice all your drives are "dynamic" except for J:. Dynamic drives may give Linux headaches, but I since all I ever use is "basic" drives, I am not sure.

Last item: you will need at least two partitions for Linux, one for / and one for swap. / is the root filesystem and swap is for virtual memory, like Windows swapfile.

Do yourself a favor and read up on partitioning before you go further:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by Shishant on 2010-11-12
I deleted partitions G: F: I: and kept them as unallocated space through computer management in win7 and boot to ubuntu but still its same as earlier

[IMG]http://i53.tinypic.com/25ioy9l.png[/IMG]

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8177cf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        1014+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13       26122   209715200   42  SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           26122      121602   766942936   42  SFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 4043 MB, 4043284480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000ac20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3944719    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

---

### Post by oldfred on 2010-11-12
SFS is still the issue. It is a windows only partition scheme.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

---

### Post by Shishant on 2010-11-12
A whole harddisk is converted to basic and not just a partition so there is a data loss because whole harddisk is rebuilt thats what I found searching net, so maybe in future when ubuntu has a support for dynamic disk I will use it, but still will surely miss ubuntu a lot.

---

### Post by srs5694 on 2010-11-12
> **Shishant said:**
> A whole harddisk is converted to basic and not just a partition so there is a data loss because whole harddisk is rebuilt thats what I found searching net, so maybe in future when ubuntu has a support for dynamic disk I will use it, but still will surely miss ubuntu a lot.

As oldfred wrote, the [Partition Wizard](http://www.partitionwizard.com/) software is supposed to be able to do this conversion non-destructively. Like oldfred, though, I've never used this software myself, so I can't promise it'll work as advertised.

Also, it's my understanding that Linux does understand Windows dynamic disks; however, I don't know if it's possible to install Linux on a Windows dynamic disk. I don't know if GParted or other partitioning tools can do anything with dynamic disks. Even if it is possible to install Linux on a dynamic disk, I wouldn't recommend doing it, since it's a Windows non-standard, and there are (AFAIK) no Linux utilities for doing low-level maintenance on the volume structures.

---

### Post by freshmeat20 on 2011-01-19
Is there anything like partition wizard that works for linux? would gparted do?

---

### Post by srs5694 on 2011-01-19
AFAIK, no Linux software will convert Windows "dynamic disks" (SFS partitions) into regular MBR partitions.

---

