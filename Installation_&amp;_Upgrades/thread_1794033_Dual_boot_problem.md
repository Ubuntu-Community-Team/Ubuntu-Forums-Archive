---
title: "Dual boot problem"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by sysone on 2011-06-30
I made a NTFS partition and installed my old XP for a dual boot. 
The result was that computer started only Windows.  So I used a live USB with Lucid and followed instructions to install Grub 2.
Now computer only starts Ubuntu.
How do I get the dual boot screen at startup?

fdisk -l gave:
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12693   101956491    7  HPFS/NTFS
/dev/sda2           12694       12901     1664001    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda3           12901       25058    97655808   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda5           12694       12901     1664000   82  Linux swap / Solaris

---

### Post by dino99 on 2011-06-30
partition 2 & 3 does not end on boundaries, so run fsck to fix these partitions, from a livecd

sudo fsck /dev/sdax (where x is the faulty partition number)

then : sudo grub-mkconfig && sudo upgrade-grub

---

### Post by sysone on 2011-06-30
I got this :
$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

sudo fsck /dev/sda3
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda3: clean, 186603/6111232 files, 3881343/24413952 blocks

sudo grub-mkconfig && sudo upgrade-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?). (I did mount the partition)

Thank you very much

---

### Post by sysone on 2011-06-30
I also tried sda5:

$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5

---

