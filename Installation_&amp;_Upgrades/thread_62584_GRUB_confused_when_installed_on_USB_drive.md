---
title: "GRUB confused when installed on USB drive?"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by comrade_chimp on 2005-09-05
I've been trying to install Ubuntu on a removable drive using the instructions [here](http://www.ubuntuforums.org/showthread.php?t=20522) except that I'd really like to put GRUB on the USB drive (/dev/sdb) as well instead of on the primary drive (dev/hda). My BIOS is bootable from the USB drive (using Advanced Chipset Options -> Boot Disk Priority) so by doing this I should be able to boot Linux by just plugging the drive in or Windows by not doing so.

The install goes fine & it seems happy to put GRUB on the removable drive, but when I try to boot from it I get problems. Basically the GRUB menu comes up okay but if I try to select the Ubuntu option it tells me the drive is not found. Interestingly if I select the Windows option it says it cannot boot because the partition is ext3! This makes me wonder if GRUB has the drives back to front or something. Has anyone managed to get such a setup working & could give me any advice?

---

