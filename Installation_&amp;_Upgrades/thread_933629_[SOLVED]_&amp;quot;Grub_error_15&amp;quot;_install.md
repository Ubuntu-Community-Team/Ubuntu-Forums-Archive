---
title: "[SOLVED] &amp;quot;Grub error 15&amp;quot; install didnt finish."
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by markers on 2008-09-29
Hey guys. Just tried installing Hardy on my old PC and am having a problem. While I was trying to install Hardy on the PC everything was going fine until it stopped and said that there was no more room left on the HDD I was installing it to.
I have XP also installed on the computer but I cant access it anymore because it doesn't boot to the OS selection screen. All I get is the GRUB error 15. Any one have any suggestions on how to boot to XP so that I can wipe the HDD?

---

### Post by Sef on 2008-09-29
From the Live CD:

```
sudo fdisk -l
```small L  that will tell us your partitions.  Paste the results here.

---

### Post by markers on 2008-09-29
```
Disk /dev/sda: 10.1 GB, 10141286400 bytes
255 heads, 63 sectors/track, 1232 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x554ba1b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1232     9896008+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 2192 MB, 2192891392 bytes
255 heads, 63 sectors/track, 266 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf15d0ecd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         247     1983996   83  Linux
/dev/sdb2             248         266      152617+   5  Extended
/dev/sdb5             248         266      152586   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

```

I thought that I would be able to install Ubuntu on a low end PC?

---

### Post by markers on 2008-09-30
Solved my problem. Used livecd and was able to clean the HDD with the unfinished installation of Hardy through **gparted**.

---

