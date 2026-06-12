---
title: "boot partition for dual boot?"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2011-01-05
I was wondering if having a boot partition is recommended for dual boot installation of Ubuntu 10.04 and Windows 7 and why? Thanks!

---

### Post by drs305 on 2011-01-05
A separate /boot partition is required only in a few cases. One is allowing Grub to boot an OS with a filesystem not supported by G2 (such as btrfs, although that is about to change). Uses of such filesystems need a separate /boot partition formatted as ext2/3/4 to allow Grub2 to boot into the OS.

Another instance where a /boot partition may be necessary is if the user has an old BIOS which cannot recognize the entire disk. Older BIOS could not identify disk space beyond a certain limit (such as 137GB). In that case, the user may have to create a separate /boot partition within the first 137GB of the disk to ensure the BIOS can pass control to the Grub files.

For most users a separate /boot partition is not required, and it certainly isn't necessary for a dual linux/Windows boot. They can't share the same partition and only one can write to the MBR.

As someone who currently has 17 partitions on one of my drives, even I can't justify having a separate boot partition for my setup.

I'll let those who have one for *convenience* explain their reasons.

---

