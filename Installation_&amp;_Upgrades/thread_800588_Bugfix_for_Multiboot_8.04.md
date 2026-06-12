---
title: "Bugfix for Multiboot 8.04"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by dvdivx on 2008-05-20
During the install for the bootloader Ubuntu will only list (hd0) not the partition number. Selecting the partition will also not add the partition number you have to add it yourself manually like (hd0,3)(for single hdd, 4th partition). Several bug reports for this. If not added install will fail at 84% with a fatal error for grub and end the install. Found the fix at neosmart.net so don't thank me.
People installing it as a single partition won't notice the problem since the second number isn't needed as they don't have any partitions. If installing grub to root you would have to add (hd0,0).

---

