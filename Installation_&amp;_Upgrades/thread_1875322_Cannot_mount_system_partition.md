---
title: "Cannot mount system partition"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by maloo83 on 2011-11-04
I think I have killed my system partition (which sadly also contains my personal data): When starting my computer all I see is "error: unknown filesystem" and a grub rescue promt. Here is what I did: I booted a Ubuntu-Live-System via USB while my regular Ubuntu 11.10 system was in hibernate.

Now when I run fdisk -l from within the live system, this is what I see:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      401624      200781   de  Dell Utility
/dev/sda2   *      401625    56612976    28105676    7  HPFS/NTFS/exFAT
/dev/sda3        56614910   488396799   215890945    5  Extended
/dev/sda5        56614912   470808575   207096832   83  Linux
/dev/sda6       470810624   488396799     8793088   82  Linux swap / Solaris

```Now when I try to mount sda5 or sda3 using "sudo mount -r -t ext4 /dev/sdaX /mnt", I get: wrong fs type, bad option, bad superblock, missing codepage or helper program, or other error" and dmesg contains the following:
```

[ 5925.202725] EXT4-fs (sda5): VFS: Can't find ext4 filesystem
[ 6025.811834] attempt to access beyond end of device
[ 6025.811843] sda3: rw=0, want=4, limit=2
[ 6025.811852] EXT4-fs (sda3): unable to read superblock

```I'm totally desperate, is there anything I can try to recover my data?

Thanks in advance,
 M

---

### Post by darkod on 2011-11-04
You can try TestDisk (you can download and run it in the live mode).
But first read carefully the manual on their page, and if you have any doubts ASK FIRST BEFORE DOING ANYTHING! :)
It can save your partition, but just as easy it can destroy it. Personally I never needed to use it, but people report excellent results.

sda3 can not be mounted, that is just the extended partition. But getting an error when trying to mount sda5 is not good.

PS. Forgot the testdisk link: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by maloo83 on 2011-11-04
Thanks a lot for the pointer to TestDisk. I installed it an ran it in analyze mode, this is what it returned:
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 346 GB / 322 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                16335  44 30 42117 137  4  414193664
  Linux                16338 157 12 42120 249 49  414193664
  Linux                16340 167 20 42123   4 57  414193664


[ Continue ]
EXT4 Large file Sparse superblock Recover, 212 GB / 197 GiB

```and the next page was
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    24 254 63     401562 [DellUtility]
P HPFS - NTFS             25   0  1  3523 254 63   56211435 [OS]
L Linux                11514   1  1 12507 254 63   15968547        <-- selected row
L Linux Swap           29306 154 33 30401 254 63   17597506



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT4 Large file Sparse superblock Recover, 8175 MB / 7797 MiB

```

Edit: Here are the results of a "deep analysis" run:
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    24 254 63     401562 [DellUtility]
D HPFS - NTFS             25   0  1  3523 254 63   56211435 [OS]
D HPFS - NTFS             25   0  1 30400 254 63  487990440 [OS]
D HFS                   1960 133  9  1981 254 63     345043 [      B]
D HFS                   1964 238 46  1983 254 63     306261 [      F]
D HFS                   1982   1  1  2002 254 63     337302 [      ^F]
D Linux                11514   1  1 12507 254 63   15968547
D Linux Swap           29306 154 33 30401 254 63   17597506



```
I did not create any HFS partitions, so something must be really messed up. But is there anything I can try to recover files from the system partition? E.g. take the options **write** or **fix mbr**?

Thanks a lot,
 M


Thanks,
 Maloo

---

