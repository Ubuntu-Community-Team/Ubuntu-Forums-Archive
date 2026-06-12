---
title: "from dual to single boot"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by nlz on 2008-02-20
I want to switch from my dual boot XP - Ubuntu to a single boot Ubuntu. In order to do this i have a few questions.

Is there a nice graphical drive partitioner/formatter? I want to add more space to /home and /

Now i have my linux on a partition, windows on a partition and a drive with music. In order to share the music drive it is now fusblk, but i want it to be ext3, if possible without deleting everything, how?

How should i change the boot menu, i guess something with menu.lst, but i don't want to be obliged to choose in the beginning.

thanks

---

### Post by dstew on 2008-02-20
> Is there a nice graphical drive partitioner/formatter? You can use gparted from an Ubuntu Live CD boot, or make a [bootable gparted disk]("http://gparted-livecd.tuxfamily.org/").> In order to share the music drive it is now fusblk, but i want it to be ext3I don't think you can change the format of a drive without deleting the data. The exception might be ext2 to ext3. But I don't know much about fusblk.> How should i change the boot menu, i guess something with menu.lstThere is a good chance you will have to both reinstall grub and edit the menu.lst file, but those are not hard to do. If Ubuntu is your first partition, you might not have to change anything, but if it is your second partition, and if it becomes your first by deleting XP, then you will probably have to reinstall grub. We can help you with that. In fact, why don't you go ahead and post the output of```
sudo fdisk -l
```Then we can predict what will happen.

---

### Post by logos34 on 2008-02-20
> **nlz said:**
> I want to switch from my dual boot XP - Ubuntu to a single boot Ubuntu. In order to do this i have a few questions.

Is there a nice graphical drive partitioner/formatter? I want to add more space to /home and /

/ and /home must be unmounted before you can resize.  You'll have to work from the [Gparated Live cd.]("http://gparted.sourceforge.net/livecd.php")


> Now i have my linux on a partition, windows on a partition and a drive with music. In order to share the music drive it is now fusblk, but i want it to be ext3, if possible without deleting everything, how?
nope, can't do it without transferring everything off and reformatting as ext3.  (fuseblk means ntfs-3g mounted)


> 
How should i change the boot menu, i guess something with menu.lst, but i don't want to be obliged to choose in the beginning.

yes, remove windows entry from menu.lst.  See[ this page]("http://users.bigpond.net.au/hermanzone/p15.htm") for more info.

EDIT: somebody beat me to it

---

### Post by nlz on 2008-02-21
Thanks a lot, i'm now downloading the gparted liveCD

The Grub page is really informative, things will work out this way!

Just for the info:
Linux is on my first partition, as you can see:

> beton@robotniq:~$ sudo fdisk -l
[sudo] password for beton:

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69f807c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021       11918    87538185    f  W95 Ext'd (LBA)
/dev/sda3           11919       12040      979965   82  Linux swap / Solaris
/dev/sda4           12041       12161      971932+  83  Linux
/dev/sda5            1021       10945    79722531    7  HPFS/NTFS
/dev/sda6           10946       11918     7815591   83  Linux
beton@robotniq:~$ 


now i'm thinking about how to design my new parition. I have about 80 GB. Now i have

root 7,3GB
swap 1,1 GB
home rest

I'm thinking about making the root a bit bigger but keep the rest as it is.
i think i recall someone who made a separate partition for /var, is this usefull?

thanks

---

### Post by housam on 2008-02-21
> **nlz said:**
> 
I'm thinking about making the root a bit bigger but keep the rest as it is.
i think i recall someone who made a separate partition for /var, is this usefull?


You can read more about various types of partitions [[COLOR="Red"]here[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/index.htmlt").

---

### Post by dstew on 2008-02-21
> Linux is on my first partition, as you can see:From your fdisk output, it seems that Linux is on either your fourth or sixth partition.

---

### Post by nlz on 2008-02-22
> **dstew said:**
> From your fdisk output, it seems that Linux is on either your fourth or sixth partition.

thanks, you're right. XP was my first installation. After i formatted the windows i'll edit menu.lst (YES).

thanks

---

### Post by nlz on 2008-02-22
> **dstew said:**
> From your fdisk output, it seems that Linux is on either your fourth or sixth partition.

thanks, you're right. XP was my first installation. After i formatted the windows partition (YES) i'll edit menu.lst .

thanks

---

### Post by nlz on 2008-02-24
hmmmmz, two SDA's are on one partition. Which means effectively that my / and my NFTS music disk are on one extended partition. When i delete the NFTS's one, i can only add the free space to my / and not to /home!

I think i will just backup my files and setup with aptoncd and then just reinstall. Fresh start is good once in a while..

---

