---
title: "Completely removing Vista from an XP/Vista/Gutsy triple boot"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Gruu on 2008-01-14
I've seen similar threads, but after hearing horror stories about the Vista bootloader, I want to be sure I won't mess anything up.

I have a triple-boot system with XP/Vista/Gutsy. I love XP, and I love Gutsy, but I hate Vista and want to get rid of it. Unfortunately I'm using the Vista bootloader (i.e. when I boots, it boots into Vista's choice thing where I pick XP, Vista, or GRUB).

I want to 
1) completely remove Vista and delete everything on its partition, replacing it with a FAT32 data partition (or anything that XP and Gutsy can both read/write) 
2) switch to GRUB as my primary boot thingy
3) not touch my XP or Gutsy partitions.

Is this possible? Here's the output of 'sudo fdisk -l' (gparted tells me that sda4 is vista and sda3 is unmountable (not sure why, but I've had this problem for a while; it works fine in XP so I've never worried about it).

```

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0baf8c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         131     1052226   82  Linux swap / Solaris
/dev/sda2             132        3264    25165822+  83  Linux
/dev/sda3   *        3265        5370    16916445    7  HPFS/NTFS
/dev/sda4            5371        7476    16916445    7  HPFS/NTFS


```

Thanks!!

---

### Post by Partyboi2 on 2008-01-14
> 1) completely remove Vista and delete everything on its partition, replacing it with a FAT32 data partition (or anything that XP and Gutsy can both read/write)
Gusty can read and write to ntfs file systems
>  2) switch to GRUB as my primary boot thingy
I would suggest using [supergrub]("http://supergrub.forjamari.linex.org/")

---

