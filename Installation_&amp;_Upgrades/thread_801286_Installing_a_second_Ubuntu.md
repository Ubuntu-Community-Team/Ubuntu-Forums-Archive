---
title: "Installing a second Ubuntu"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by LeoSolaris on 2008-05-20
I made a second instance of Ubuntu on a logical partition. No big deal to do, but now I have an issue. I tweaked my original Grub a good deal, so I opted to not reinstall Grub with the new installation. Now I am not sure how to add the new installation to the existing Grub list.

Leo

P.S. The first Ubuntu is 8.04 32-bit, and the second, newer one, is 8.04 64-bit. Both are using their respective default kernels.
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5411    43463826    7  HPFS/NTFS
/dev/sda2            5412       12050    53327767+  83  Linux
/dev/sda4           12051       19457    59496727+   5  Extended
/dev/sda5           19073       19457     3092481   82  Linux swap / Solaris
/dev/sda6           12051       13266     9767457   83  Linux
/dev/sda7           13267       15561    18434556   83  Linux

Partition table entries are not in disk order

```

Solved:  I found [this site. ]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst")Ok, I am a bit dense today apparently. I had this saved in my favorites folder (it is looking full... I should trim it) back when I was learning about Grub splash imagery and modification.

---

