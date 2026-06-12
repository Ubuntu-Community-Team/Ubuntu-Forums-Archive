---
title: "Grub 0x7 on ext2/3 partition"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by ksmith on 2005-06-05
Hello,

I just tried installing on my amd64 but I couldn't get past the reboot after loading the system from the CD. Grub kept complaining about unknown partition types (Filesystem type unknown, partition type 0x7).

(hd0) is WinXP
(hd1) is Ubuntu with grub

I have my BIOS load hd1 as the boot drive but grub isn't able to move past this. The grub menu.lst appears correct with Ubuntu stuff pointing to (hd1,0) but nadda.

Since my BIOS is loading (hd1) first, does grub treat this as (hd0) even though the drive is IDE0/slave?

Not sure what's up but any advice would be appreciated.

Thanks,
Kyle

---

