---
title: "Help with removing windows xp please"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by colvirk on 2009-12-08
Hello all. 

I have been researching some online to try and remove my windows xp partition from my computer. My ultimate goal would be to remove the NTFS partition and expand my Ubuntu partition to take up all of the hard drive (along with a swap partition). I ran the command I saw in a similar post (sudo fdisk -lu) and here's the output:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   159410159    79705048+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       220842720   234435599     6796440    c  W95 FAT32 (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3       159412995   220829489    30708247+   5  Extended
/dev/sda5       159413058   163413179     2000061   82  Linux swap / Solaris
/dev/sda6       163413243   220829489    28708123+  83  Linux

/dev/sda2 is a recovery partition I would like to keep to easily convert back to winxp if I need to. I installed Ubuntu 1) to try it out and 2)to backup some important files. These files are now on the Ubuntu partition which is why I am trying to go this method instead of removing the entire partition and starting over. 

I am not a very experienced linux user and need some hand holding here if someone has the time. Thanks all in advance!

---

### Post by MelDJ on 2009-12-08
hi
see: [https://help.ubuntu.com/community/HowToRemoveWindows](https://help.ubuntu.com/community/HowToRemoveWindows)

---

