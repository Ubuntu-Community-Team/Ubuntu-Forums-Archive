---
title: "Dual Boot: Windows &amp; Ubuntu. How to Increase Windows partition?"
date: 2023-08-25
forum: Installation &amp; Upgrades
---

### Post by flyingsolo on 2023-08-25
My dual boot win/ubuntu has been working great for years (I think I set it up ~3y ago?) but now my windows partition is getting full and needs to be expanded (the data partition). I originally gave ~150GB to windows and 350 to ubuntu.
How do I expand the windows data partition without impacting the ubuntu installation? 
Thanks.

---

### Post by flyingsolo on 2023-08-25
gparted has the ubuntu partition following the windows data partition. If I expand the windows one, can it disrupt the ubuntu partition? I don't wish to lose anything on the ubuntu partition.

---

### Post by oldfred on 2023-08-25
Before doing anything make full backups of both systems and all data.

Use gparted or other Linux tools to change Linux partitions. Partitions must be unmounted, so use live installer in live mode.
Use Windows tools to change NTFS partitions.

Note that a move can take a long time, especially if overlapping and/or lots of data.
Any interruption will totally corrupt data and your backup is the only recourse.

---

### Post by yancek on 2023-08-26
If Ubuntu is contiguous with your windows partitions and you expand it, it will definitely create problems for you.  Do you have any free/unallocated space?  I would suggest you post the output of the command:  sudo fdisk -l  as it will list your partitions and sectors so we can see exactly what you have.  If there is unallocated space on the drive, you could go into windows and create another partition there.

---

### Post by flyingsolo on 2023-08-26
Thanks @oldfred and @yancek for both your suggestions and below is the output from sudo fdisk -l

Originally I wasn't using Windows for much but I since have used it mainly for Adobe Lightroom and the photo collection has grown to require more space. I could delete a load of stuff from Win partition but I've found it difficult to  clearly analyze what's mainly taking the space. 
So, I think my options are: 
1. find room in the existing partition
2. expand the Windows partition (hence, my question and post here)
3. install a second bootable drive in the computer (desktop that I built) on which to put the Windows or Ubuntu OS and keep them separately.

I'm open to thoughts on which might be the best process to follow, considering which is least likely to go wrong.


```
Disk /dev/loop0: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 9.57 MiB, 10039296 bytes, 19608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 9.56 MiB, 10027008 bytes, 19584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 118.23 MiB, 123973632 bytes, 242136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 118.23 MiB, 123973632 bytes, 242136 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 55.64 MiB, 58339328 bytes, 113944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 55.66 MiB, 58368000 bytes, 114000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by oldfred on 2023-08-26
You are only showing loop devices which are all your snaps. Those are not drives.
Post results of fdisk without snaps/loop devices.

---

### Post by flyingsolo on 2023-08-28
Sorry, I was rushing out to a wedding yesterday!
I think this is the info you wanted.

> Disk /dev/nvme0n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk model: Samsung SSD 970 EVO Plus 500GB          
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F300D8C0-CDBD-49B4-B804-F6ABDA4F9E1B

Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1085439   1083392   529M Windows recovery environment
/dev/nvme0n1p2 1085440   1288191    202752    99M EFI System
/dev/nvme0n1p3 1288192   1320959     32768    16M Microsoft reserved
/dev/nvme0n1p4 1320960 300933119 299612160 142.9G Microsoft basic data


Disk /dev/sda: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors
Disk model: TOSHIBA HDWE140 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: D60B89FE-0DEA-4981-83AB-93870EF46E48

Device       Start        End    Sectors  Size Type
/dev/sda1       34      32767      32734   16M Microsoft reserved
/dev/sda2    32768    1083391    1050624  513M EFI System
/dev/sda3  1083392 7814035455 7812952064  3.6T Linux filesystem

Partition 1 does not start on physical sector boundary.


---

### Post by yancek on 2023-08-28
I don't see a problem.  You initially indicated that you wanted to increase the size of the windows partition and wanted to know if it would affect Ubuntu.  The fdisk output shows they are on different physical drives.  fdisk shows a 450GB SSD with windows and nearly 70% is not used at the end of the drive.  If you look at the top of the fdisk output, it shows the total sectors and adding up the sectors used on the partition shows 300933119 sectors used which is about 30% of the drive.  Partition 4 is the largest partition and should be your windows partition so go into Disk Management on windows and increase it.

If you modify the EFI partition on the windows drive it might create problems but since you have a separate EFI partition on the Ubuntu drive, that should not be a problem.

---

### Post by flyingsolo on 2023-08-30
thanks yancek,
I was surprised myself to see the two OS's were on separate drives as I don't remember doing that when I built this 3 y ago. I also can't understand why I would have left so much unallocated space on the Win drive.

So can I simply use gparted to expand the MS basic data partition into the unallocated space? The ubuntu install should be 'safe' on its own drive.

---

### Post by oldfred on 2023-08-30
Only use Windows tools for modifying NTFS partitions.
While gparted often can do it, sometimes Windows issues cause problems and users blame gparted.

---

### Post by yancek on 2023-08-31
Use windows Disk Management as suggested by oldfred and when you finish, reboot into windows and run chkdsk to be sure no problems.  GParted should be able to do it but it is always better to use windows tools on a windows filesystem as pointed out above.

---

