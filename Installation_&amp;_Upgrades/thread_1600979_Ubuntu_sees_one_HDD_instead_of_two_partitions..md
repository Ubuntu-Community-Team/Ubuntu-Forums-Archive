---
title: "Ubuntu sees one HDD instead of two partitions."
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by kilinu5889 on 2010-10-19
OK, so I decided to go and install ubuntu 10.10 today. I have two partitions on my HDD. Ubuntu only sees one HDD, and not the two partitions. I get no option to dual boot vista and ubuntu at all. It is only format and use the entire disk, or install manually. I go into gparted and all ubuntu sees is one unformatted HDD. But vista sees two partitions. I have all of my media on one partition. I REALLY don't want to go and format the entire drive to lose my things. Is there a work around for this? I have no access to any other PC.

---

### Post by Mark Phelps on 2010-10-19
You're right to be nervous ...

You should first go into Vista and use the Disk Management utility to shrink the Vista partition to make room for Ubuntu.  Leave the space unallocated -- don't format it.

Then, reboot from the Ubuntu CD, run it in LiveCD Mode (Select Try, not Install), open up the Partition Editor, and see if it sees the partitions and unallocated space.

OR ... you could just open a terminal from inside Ubuntu and enter "sudo fdisk -lu" (that's a lowercase L, not a one), and post the results back here.

If you don't see the partitions and free space using these, there is a more serious problem to be addressed -- and forcing an installation runs the risk of wiping out your Vista stuff.

---

### Post by kilinu5889 on 2010-10-19
Alright, this is what I get when I ran that command.

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbdb47ee7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   351535103   175766528    7  HPFS/NTFS
/dev/sda2       351535104   488392703    68428800    7  HPFS/NTFS

Disk /dev/sdb: 16.0 GB, 16001036288 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31252024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ad5f

```

---

### Post by srs5694 on 2010-10-19
The problem is that the disk seems to have once been used with a GUID Partition Table (GPT) -- perhaps on a Mac or if you experimented with GPT for some reason -- and then re-used as a Master Boot Record (MBR) disk by a utility that doesn't understand or care about the GPT data. The end result is something with a valid MBR and mostly (but not quite) valid GPT data, thus confusing some partitioning tools and OSes.

The solution is to wipe out the stray GPT data. You can do this with my [GPT fdisk (gdisk or sgdisk).](http://www.rodsbooks.com/gdisk/) The easiest way is in sgdisk, but you'll need to download the Debian package for your architecture from the program's [Sourceforge page](http://sourceforge.net/projects/gptfdisk/files/) and install it in the Ubuntu live CD. You can then use sgdisk:

```

sudo sgdisk --zap /dev/sda

```

Be sure to use --zap, not --zap-all, and be sure to specify the correct disk -- /dev/sda (not /dev/sdb, unless the drive ID changes; and not /dev/sda1 or /dev/sda2). The program will display warnings about corrupt partition tables. You can ignore them.

Alternatively, you can use gdisk, either from the Ubuntu CD, or by using the Windows version from a Windows boot. (Be sure to run it as the Administrator, and the drive will probably be [noparse]"0:"[/noparse].) It'll complain about the corrupt data and ask whether to use MBR or GPT. Either is OK. Type "x" to enter the experts' menu, then type "z" to "zap" (destroy) the GPT data. Confirm this selection, but ***do not let it erase the MBR*** when it asks you whether to do this.

---

### Post by kilinu5889 on 2010-10-19
Alright, thanks alot. it worked! Kudos to you!

---

