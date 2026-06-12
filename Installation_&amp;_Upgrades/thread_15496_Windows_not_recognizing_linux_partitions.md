---
title: "Windows not recognizing linux partitions"
date: 2005-02-15
forum: Installation &amp; Upgrades
---

### Post by b00jah on 2005-02-15
Hello everybody,

I just installed Ubuntu yesterday and everything was going smoothly.  I used Partition Magic to resize one of my NTFS partitions, then I used the Ubuntu installer to point which partition I would like to use as my linux/swap.  

Everything ran great, Grub worked fine.  Until I wanted to use Parition Magic (v8.0) again and it gave me an error saying that "Partition's drive letter cannot be identified".  I checked "My Computer" and it showed only my two NTFS partitions (no swap or linux, even though they work fine and I can see my windows partitions when running Ubuntu).  I ran Disk Management within windows and it showed the drives as "unsigned drives" and would not allow me to specify drive letters to those linux partitions.

I again ran Partition Magic with the /IPE (Ignore Partition Errors) argument, and it showed both the linux and swap paritions as "healthy, unknown drives".  Now, the whole point of me being able to use Partition Magic is so that I can change my "data" parition from NTFS to FAT32 so Ubuntu can use it as well...

Is there any way for me to still assign drive letters to my linux and swap partitions without starting from scratch?  And if I have to start from scratch, what should I do differently?  Thanks, and here is my filesystem if it helps at all:

```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         638     5124703+   7  HPFS/NTFS
/dev/hda2            1257        7296    48516300    f  W95 Ext'd (LBA)
/dev/hda3             639        1256     4964085   83  Linux
/dev/hda5            1288        7296    48267261    7  HPFS/NTFS
/dev/hda6            1257        1287      248944+  82  Linux swap

Partition table entries are not in disk order

```

---

### Post by evangelion on 2005-02-15
Sorry, you're kind of out of luck here.  Windows has no support for any Linux filesystems.  There are a few third party and/or open source programs that will allow you to view and read (maybe write, I'm not sure) to ext2 partitons.  If you use reiserfs there is some shady command line only tool that lets copy files from a resierfs party but you'll have to dig that one up on your own.

[Here](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) is a link to ExploreE2fs, which is an Explorer like tool that lets you read ext2 partitions. Use this at your own peril,  I've never used it before so I can't say that it actually works,  only that it claims to let you see your linux filesystem.

In any case, you'd never need to see anything on your swap partition, it's best just to forget about it and let it do its thing.

For future reference, both operating systems read FAT32 just fine, so you may consider creating a seperate FAT32 partition to store things that you will need to have access to in both operating systems.

---

### Post by bpilgrim1979 on 2005-07-22
I installed a second hdd to my dual boot WinXP and Hoary system.

In gparted I split the new hdd into two logical partitions within one extended partition.  ntfs and ext3.  I added ext3 to fstab, works great.

The problem is that WinXP now says "Healthy (Unknown Partition)".  I can't assign a drive letter, format, etc.

With gparted, I then deleted ntfs and made it a primary partition.  Still no luck.

However, I noticed the flags "lba" on the exiting first hdd fat32 partition that Windows does recognize.

How do I resolve this situation?

---

