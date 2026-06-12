---
title: "armada 7400 and partitioning..."
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by nikku_neko on 2007-12-14
i've recently rescued an old compaq armada from someome's basement and am about to resuscitate with xubuntu 6.06.  with a pII processor, 128mb ram and a dvd drive, what tinkerer could resist?

i have, however, fallen into an area of uncertainty with this laptop, and i'm looking for anyone with experience in this field:  because apparently rather than booting from a chip on the motherboard, it uses a weird GUI bootload that is partitioned somewhere on the harddrive.  when i tried to delete everything except for that partition and install the bootloader there, Xubuntu did not recognise/find it.


my question is:would it be safe to completely clear and reformat the drive during installation and place GRUB on a boot partition instead of on the MBR (or where the MBR would normally be)?

anyone have experience with this?

---

### Post by nikku_neko on 2007-12-14
just an update on my situation now that i've returned from work:

i ran the fdisk command in the ms-dos prompt and it showed only one partition, the 28GB FAT32 partition on which windows currently resides.  no proof of a 16MB boot partition.

i re-ran GPartED and got the same result. only one 28GB partition detected.

this is very baffling.  maybe i should just write xubuntu and see what happens?

---

