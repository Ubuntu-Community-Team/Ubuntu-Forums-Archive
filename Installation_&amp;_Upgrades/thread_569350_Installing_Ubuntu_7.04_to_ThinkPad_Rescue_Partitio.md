---
title: "Installing Ubuntu 7.04 to ThinkPad Rescue Partition"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by dmunc on 2007-10-06
Hello all,

I'm ready to move beyond the live CD and install Ubuntu, if possible. I unfortunately have to keep Windows (damn proprietary academic software!)...

I've researched installing directly to the "rescue and recovery" partition without much luck (most others wish to delete it entirely). I don't really need it (I can have the entire hard disk reimaged rather easily on-campus should something go wrong), so it seems like it would be a good place to install without having to change my "C" and "D" partitions (which I'd rather not do!).

Here is my partition summary in the Ubuntu install:

/dev/sda1    ntfs    12037 11500
/dev/sda2    ntfs    18084 17800
/dev/sda4    fat32    9885   4900

If I format the third partition and install there, since it's supposedly a "hidden partition" will it give me a boot option at startup, or not work at all? I'm really new to all this and greatly appreciate your assistance.

Thanks,
Dan

---

### Post by chrisxp on 2007-10-08
presuming sda1 and sda2 are your c and d windows partitions, then sda4 is the recovery.. i dont know if it being 'hidden' is an issue but it shouldnt really, install ubuntu on that one, and grub will be installed, so when you turn on the computer you can choose between windows or ubuntu :)

---

