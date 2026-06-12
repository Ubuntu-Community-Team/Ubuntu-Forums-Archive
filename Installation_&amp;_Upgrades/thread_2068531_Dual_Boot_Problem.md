---
title: "Dual Boot Problem"
date: 2012-10-09
forum: Installation &amp; Upgrades
---

### Post by Pamukkale on 2012-10-09
Hi;  I got problem with dual-booting Windows 7 and Ubuntu 12.0.4..I'am trying to install ubuntu but there is no side-by-side option like as tolded on guide.Then i tried to make it manually but Ubuntu sees my hard-disk completely free space.No sign of Windows.Also, i tried another distro and faced by the same thing..What i should do to solve this and dual-boot my computer succesfully?.Thanks.

---

### Post by cipherboy_loc on 2012-10-09
From a terminal on a livecd, post the output of:
```

sudo fdisk -l

```

Have you checked your windows partition for errors lately and/or defragmenter? Also, when you say it detects it as free space, what is "it"? If it is the installer program, try using gparted.


Thanks,
Cipherboy

---

### Post by Pamukkale on 2012-10-09
I installed windows today so i dont think there may be a partition error.Yeah,ubuntu`s installer program sees.Btw, sorry for my english;maybe i cannot explain the matter clearly.I`m learning it new.There is output of your code;



WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x32f78260

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   976771071   488282112    7  HPFS/NTFS/exFAT

---

### Post by darkod on 2012-10-09
As you can see, you have gpt leftovers on the disk. Earlier it had gpt table, you made it msdos with windows but windows doesn't delete the backup gpt table.

That's why linux ignores it, not knowing if it's gpt or msdos disk.

You need to run fixparts which will sort this out for you. Details here:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

There is a version for windows too. It's your choice whether you run it from windows or from ubuntu live mode.

I would prefer ubuntu live mode since it's running from the cd and it needs to fix the hdd so it's better not to run from it.

---

### Post by Pamukkale on 2012-10-09
Problem solved.Many thanks to cipherboy_loc and darkod.

---

