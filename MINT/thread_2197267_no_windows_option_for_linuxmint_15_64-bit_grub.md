---
title: "no windows option for linuxmint 15 64-bit grub"
date: 2014-01-03
forum: MINT
---

### Post by brentiebuntu on 2014-01-03
Hello!

I've tried to install boot repair on my linuxmint 15 64bit to repair my missing windows os option in grub menu. I got directly here since maybe this forum could provide solution even if I'm using mint (due to its active members).
Here is result I've got from the boot repair:

[http://paste.ubuntu.com/6682686/](http://paste.ubuntu.com/6682686/)

Please help me because this windows OS i had on my computer is not mine, it was purchased by our office.

---

### Post by deadflowr on 2014-01-03
You seem to be missing a partition.
(normally /dev/sda1 is first)
Along with that, your missing the first 100MB of space.
(your partition table says it starts at something like 108MB on /dev/sda2)

Don't know the fix, but maybe [Fixparts]("http://www.rodsbooks.com/fixparts/") might help

---

### Post by lisati on 2014-01-03
*Thread moved to **Other OS/Distro Support**.*

---

### Post by coffeecat on 2014-01-03
Since the missing sda1 partition that deadflowr mentions was about 100MB in size, I'd put serious money on that once being the Windows 7 boot (SYSTEM) partition. There are no /bootmgr or /Boot/BCD Windows boot files/folders in your C: partition which is sda2 - which is why the grub menu does not have a Windows option.

I very much doubt that boot repair would be able to fix this. You need either to be able to restore the missing sda1 partition or repair the sda2 boot sector such that it can boot without a separate boot partition.

For the first, I would suggest [testdisk]("http://www.cgsecurity.org/wiki/TestDisk"). I don't think fixparts will help to restore a deleted partition, athough you could try.

If that doesn't work and you want to try the second, you would need a Microsoft Windows 7 install DVD and use one of the repair options. The OEM manufacturer's recovery DVDs are unlikely to have this repair option, unfortunately.

By the way, if you do use testdisk to recover the missing sda1 partition, you need to be aware of a potential bug that might affect you. I don't know whether testdisk still has this bug, but this was true a couple of years ago. You have an extended partition, and in some cases testdisk would adjust the partition table reference to this so that the end sector was recorded as beingoutside the physical limit of the disc. This didn't affect the functionality of any installed operating systems, but confused some partitioning apps such as gparted. Fortunately, the fix is easy: fixparts! You may not run into this problem but it is as well to be forewarned.

---

