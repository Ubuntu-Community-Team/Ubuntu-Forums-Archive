---
title: "New swap partition, WIN2K fails to boot."
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by YellowSub on 2005-02-13
Hello everybody, this is my first post here :)

I noticed a bug I can't explain.

Here is my current partitionning:

Disk /dev/hda: 185.2 GB, 185283624960 bytes
255 heads, 63 sectors/track, 22526 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4111    33014488+   c  W95 FAT32 (LBA)
/dev/hda2   *        4112       22464   147420472+  83  Linux

It works well, but as you can see there is no swap partition.

Nevertheless, if I add a new swap partition using fdisk, /dev/hda3, type 82, leaving the /dev/hda1 and /dev/hda2 in the same state, windows 2K fails to boot : famous blue screen while loading.

If I remove the swap partition, win2K loads perfectly.

Any ideas ?

Thanks a lot.

---

