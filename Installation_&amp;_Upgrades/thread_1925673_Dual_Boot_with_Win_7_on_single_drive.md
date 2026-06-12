---
title: "Dual Boot with Win 7 on single drive"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by waseembaraskar on 2012-02-14
HI, every1 out there,

I am new to ubuntu. I had used ubuntu 9.10 & 10.0 version as the free CD provide by Canonical.
I thanks to them as they introduced me to new Linux os.

Now I have facing problem with Dual boot.
I have **Win 7** as primary OS & I want to install **Ubuntu Ultimate** *edition* **2.3** on D drive. When I first attempt to do this it had erased my all data from E & F drive. I have following Drive stucture.
C:\ ________Win 7________25GB________    (4GB free space)
D:\                          ________         ________40GB   ________(All free).
E:\           ________Movies_______    50GB________(10gb free)               
F:\           ________software______ 53gb    ________(12 gb).

I want to install Ubuntu on D: drive only. I want to use both OS to use.Please guide me to how to do this.
Please excuse me for my poor english.

Thanx.

---

### Post by darkod on 2012-02-15
The first thing you should do is forget the word "drive". Windows did a very bad thing that started using it, and it created a great confusion because that word has two meanings. It can refer to a Hard Disk Drive, which is the physical disk, or in windows it can be simply a partition on a disk and it's called also drive C, drive D, etc. Instead it's much better and clear to use "disk" for a hdd and "partition" for a partition on the hdd.

Is your D a partition of 40GB? Is it NTFS partition?

If it is, linux does not install on ntfs. You will need to open Disk Management in win7, and delete the D partition. Leave the space unpartitioned.

Then start the ubuntu installation and install into the unpartitioned space. It will create the partitions needed. If you want more control and you feel up to it, you can install with the manual method and create partitions yourself.

The similar would apply if D is a separate hard disk. Delete the ntfs partition on it, and install ubuntu into the unpartitioned space.

---

### Post by fantab on 2012-02-15
I would suggest that you first back up E:\ and F:\ and then using Windows Disk Management utility DELETE D: E: & F: 

You will now have 143 GB unallocated space.

Recreate Partitions D: 50 GB Movies and E: 53 GB Software and leave the remaining 40 GB unallocated.

Boot with Ubuntu LiveCD and choose to Install. When you reach to STEP - Allocate Disk Space select "Something Else" option (to specify partitions manually). 


[LIST=1]
[*]Select the unallocated space 40 GB and create an **EXTENDED PARTITION**.
[*]Create a** LOGICAL** Partition- 36-38 GB. Format with File system **EXT4** and use "**/**" as mount point.
[*]From the remaining 4-2 GB you will create **LINUX SWAP** Partition.
[/LIST]
When installing **GRUB** Boot Loader Select **/dev/sda**(only) as device to install it.


Even if you choose to follow[COLOR=Navy] darkod'[/COLOR]s suggestion remember to create a SWAP partition to avoid any inconvenience later.


For more info on Dual Boot with windows read**[ HERE]("http://members.iinet.net.au/%7Eherman546/p24.html")**.
For safe partitioning use **[GPARTED LiveCD]("http://gparted.sourceforge.net/livecd.php")**.

---

### Post by darkod on 2012-02-15
> **fantab said:**
> 

[LIST=1]
[*]Select the unallocated space 40 GB and create an **EXTENDED PARTITION**.
[/LIST]


Does this option exist?

If I remember correctly the only options are primary or logical when creating a new partition. Then the extended is created automatically to include all logical partitions inside it.

If we say create extended partition, which is not exactly true (it never says extended anywhere), new users might get easily confused that they are missing something.

---

### Post by varunendra on 2012-02-16
> **darkod said:**
> Does this option exist?
I never use the Ubuntu installer's default disk management tool, so can't say about it. As for gparted, which is included on the live cd/usb and the recommended tool to do partitioning,** YES the option to create 'Extended Partition' does exist.** You can create 'logical' partitions inside it later- in further steps. This gives a better control over space allocation to the current and future partitions.

However, I don't recommend putting an OS partition in the last of any drive, since read/write performance of such partitions are typically very low compared to the partitions created in the beginning of disks. Of course this applies to only traditional hard disk drives which have moving platters inside, not SSD's which are basically RAM cards with persistence.

Usually, it is always recommended to put operating systems in the beginning of a drive, and compressed data, like 'movies', in the last. However, I think (but am not sure) it is presumed in this recommended that the 'compressed data' would be less frequently used than the rest of data on a computer. So for the OP, I think the last partition should contain whatever he is going to use least frequently. As such, I think the method suggested by *darkod *'should' be most optimal. But there's a catch-

If the other two partitions (E and F) are also primary ones, then the default partitioner may behave unexpectedly. Because it would try to create a swap partition as well (I'm not sure though), which would be impossible unless both root and swap partitions are created as logical ones inside and extended partition. Either this, or the swap would be completely omitted or created as a 'file'. Both these situations may compromise functionality/performance of swap.

It should be noted though that none of these issues (which are not very serious anyway) would arise IF the other two partitions are already logical ones.


@*waseembaraskar*,
For best advise, please boot into a live Ubuntu session, and run and post the output of
```
sudo fdisk -l
```
This will tell us everything about your current partition layout.

---

### Post by waseembaraskar on 2012-02-17
Thanks,
I will try on saturday,
If something goes wrong i'll post here.

thanx once again . .

---

### Post by waseembaraskar on 2012-02-24
Hey guys hi,

finally i installed Ultimate Edition of ubuntu (2.7).

i am posting disk status after installing 
please post ur suggestion if you have one.

> 
baraskarlinux@baraskar-laptop:~$ sudo fdisk -l -s

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x182a1829

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3350    26908843+   7  HPFS/NTFS
/dev/sda2            3351        9259    47459328    7  HPFS/NTFS
/dev/sda3            9259       16653    59390976    7  HPFS/NTFS
/dev/sda4           16653       19458    22529025    5  Extended
/dev/sda5           16653       19093    19599360   83  Linux                                                                               
/dev/sda6           19093       19458     2928640   82  Linux swap / Solaris
baraskarlinux@baraskar-laptop:~$ 



thankx guys once agian.

---

