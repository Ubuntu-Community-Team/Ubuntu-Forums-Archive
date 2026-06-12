---
title: "Dual boot, ubuntu with full encrypt-missing partitions (have I lost everything?)"
date: 2014-08-01
forum: Installation &amp; Upgrades
---

### Post by palo3 on 2014-08-01
Hello thank you for your time....
I have installed windows 7 ultimate 64 bit on one(A) partition. After installing windows I have installed ubuntu (I had already installed ubuntu 13 so I have selected to fully remove old 13 and install 14.04 with full encrypt). Ubuntu 13 was installed on 3 separated partitions(BCD).... 
And I need to recover the last partition(E) where I have only documents and photos... (not OS or any programs)

I can only boot Ubuntu from live CD...(tried some tutorials and failed....)  when I open hard drive (after entering password) I cant see any of my documents or partitions...
I need only partition(E)....


Output when running: sudo fdisk -l


 ```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/mapper/luks-6e8a6d2b-d329-4676-a886-332730ca3a5f: 999.4 GB, 999408271360 bytes
255 heads, 63 sectors/track, 121504 cylinders, total 1951969280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/luks-6e8a6d2b-d329-4676-a886-332730ca3a5f doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-root: 991.4 GB, 991399247872 bytes
255 heads, 63 sectors/track, 120530 cylinders, total 1936326656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 7998 MB, 7998537728 bytes
255 heads, 63 sectors/track, 972 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table


```

---

### Post by oldfred on 2014-08-01
Auto install with LVM either encrypted or not is always a full drive install. So all partitions are erased and entire hard drive is converted to LVM.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

fdisk is only for MBR(msdos) partitions. So it also looks like you installed in UEFI mode or else drive would not normally be converted to gpt partitioning. 
Post this:
sudo parted -l

If you want to preserve partitions you must use Something Else install option.

If data is valuable, you may be able to recover some of the data with lots of effort. First try testdisk to see if it can see old partitions and deeper search to see if it can find files.
If testdisk does not work, then recourse is drive scanners that just look at drive for anything that is a file. Do not know if encryption just encrypts your new data, or converted entire drive which would mean noting is recoverable.  Any time you use encryption you must have extremely good and consistent backup procedures.

      
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS

      [/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

      
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)

     
    [URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by palo3 on 2014-08-01
Thank you for reply

sudo parted -l
```

Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size   File system  Name  Flags
 1      1049kB  538MB   537MB  fat32              boot
 2      538MB   794MB   256MB  ext2
 3      794MB   1000GB  999GB


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 7999MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  7999MB  7999MB  linux-swap(v1)


Error: /dev/mapper/luks-6e8a6d2b-d329-4676-a886-332730ca3a5f: unrecognised disk
label

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 

```

And I am going to try testdisk

---

### Post by oldfred on 2014-08-01
You show standard UEFI LVM install. 
Inside your sda3 physical partition are the LVM partitions which you can only edit with LVM tools.

---

