---
title: "Partitioning External HD and Install"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by [pl]ice on 2007-09-26
hi guys,
 i need  a hand. I know it's a minor thing, but can't manage :(

 Got external USB HD. I have installed ubuntu on it using 'whole disk' and grub on (hd1). Worked ok.
  Now i partitioned that HD to 5Gb of vfat, swap and the rest ext3 for main install. Grub installed on hd1 again.
   On booting from USB, grub is ok, but when i chose kernel (or safemode one etc) grub says cannot find partition, and thats it. Ubuntu is fully installed on the HD, checked it.
   I edited the menu.lst in grub, and tried all partitions for the menu, without sucess. I'm not sure where the problem is. 
any idea?
thanks!

---

### Post by logos34 on 2007-09-26
> **'[pl]ice said:**
> hi guys,
 i need  a hand. I know it's a minor thing, but can't manage :(

 Got external USB HD. I have installed ubuntu on it using 'whole disk' and grub on (hd1). Worked ok.
  Now i **partitioned that HD to 5Gb of vfat, swap and the rest ext3 for main install. Grub installed on hd1 again.**
   On booting from USB, grub is ok, but when i chose kernel (or safemode one etc)** grub says cannot find partition,** and thats it. Ubuntu is fully installed on the HD, checked it.
   I edited the menu.lst in grub, and tried all partitions for the menu, without sucess. I'm not sure where the problem is. 
any idea?
thanks!

If that's the order of the partitions

1. fat32
2. swap
3. root

then menu.lst 'root' line should read (hd0,2).  You say it was working before so you must have changed the root from hd1 to hd0 (you've no doubt seen [this]("http://ubuntuforums.org/showthread.php?t=80811"), post#502).

Not sure why it's giving you trouble the second time around...You can double-check the UUIDs

blkid

or try 'root=/dev/sdx3' format 

Try[ reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by [pl]ice on 2007-09-26
> **logos34 said:**
> If that's the order of the partitions

1. fat32
2. swap
3. root

then menu.lst 'root' line should read (hd0,2).  You say it was working before so you must have changed the root from hd1 to hd0 (you've no doubt seen [this]("http://ubuntuforums.org/showthread.php?t=80811"), post#502).

Not sure why it's giving you trouble the second time around...You can double-check the UUIDs

blkid

or try 'root=/dev/sdx3' format 

Try[ reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351").

hm, no i haven't checked that other post, looking at it now.
  to me ubuntu fond the internal first HD (hd0) as i accidently installed grub there,and it was on the main HD, then it jumps to sdb,
1.root
2fat32
3swap

please correct me, but hd0,2 stands for 1st HD , second partition. 
thus i have tried hd1,1  and did not work
thanks guys!

---

### Post by logos34 on 2007-09-26
grub starts counting at 0, so hd0,2 would actually be the 1st HDD, third partition.

I see root is first partition.  try root (hd0,0) or (hd1,0) --one of them should work.

---

### Post by [pl]ice on 2007-09-27
got it working.
   Went to grub and manually edited on startup which partition, turned out its hd0,5 , bit strange, but it works, and i'm VERY happy.

thanks people!

Polish

---

### Post by logos34 on 2007-09-27
> **'[pl]ice said:**
>  turned out its hd0,5 , bit strange, but it works

must be on a logical partition then...I should have asked you for your fdisk output in the first place

---

### Post by [pl]ice on 2007-09-27
> **logos34 said:**
> must be on a logical partition then...I should have asked you for your fdisk output in the first place

yeh, my mistake too, i have checked the output from /proc/partitions, not fdisk! wrrr
thanks logos34

---

