---
title: "GRUB problems"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by j_koch06 on 2008-08-27
I am totally new to linux...I had my hd partitioned into 2.. drive one for os and the other for my pics/mp3's ect.then i partitioned the 0s into 2 so i could designate one for swap drive and the other for ubunto.. I try to install ubuntu and get a grub hd0 error (fatal error) when its about 95% done...here is a copy of the fdisk
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfde6fde6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         608     4883728+   7  HPFS/NTFS
/dev/sda2             609        9729    73264432+   f  W95 Ext'd (LBA)
/dev/sda5            1148        9729    68934883+   7  HPFS/NTFS
/dev/sda6             609        1147     4329454+  82  Linux swap / Solaris

Partition table entries are not in disk order

any help i would appreciate it...again i am totally new so you will have to spell everything out for me =/:confused:

---

### Post by VMC on 2008-08-27
You can delete that swap partition and have ubuntu use free space. It will create the swap and Linux partitions automatically. Notice that you don't have a Linux partition.

---

### Post by caljohnsmith on 2008-08-27
For a "standard" Ubuntu installation, you need to have two partitions: one for the Ubuntu root system and one for swap space. Since sda2 is an extended partition, you can create virtually as many logical partition within sda2 as you want; since you all ready have a swap partition created, just create another logical partition within sda2 for Ubuntu. Then when you go through the installer, mount the Ubuntu partition on "/" (i.e. root) when it gives you that choice. If you need more details/info feel free to ask; many people in these forums are really good with installation questions.

---

### Post by j_koch06 on 2008-08-29
will doing the free space delete my files on my large partition?

---

