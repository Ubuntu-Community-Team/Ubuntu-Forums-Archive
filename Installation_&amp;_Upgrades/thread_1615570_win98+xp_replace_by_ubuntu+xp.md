---
title: "win98+xp replace by ubuntu+xp"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by Annuhkeh on 2010-11-07
Hello,
Since a few weeks, I'm using a Ubuntu 8.04 live cd on my old computer, which is a dual-boot of win98 and winxp. I want to delete the win98 and replace it by Ubuntu, cause my parents want to use the xp-installation. But the question is, can I install Ubuntu on the first two partitions of my harddisk, because every manual says that you have to install Ubuntu on empty space at the end of the disk? And if so, how can I do that?
Thanks a lot!

---

### Post by mörgæs on 2010-11-07
Hi, welcome to the forum.

If you boot the live CD (I would go for 10.04 or 10.10), you can run Gparted and delete the Win 98 partition(s). 

After that you can install Ubuntu in the empty space.

---

### Post by Annuhkeh on 2010-11-07
Okay, but does the bootloader then recognize the xp-partition as a bootable disk?

---

### Post by sikander3786 on 2010-11-07
> **Annuhkeh said:**
> Okay, but does the bootloader then recognize the xp-partition as a bootable disk?
I don't think so. I assume that Windows98 is installed on the C: drive and XP on some other say D: but the boot files for XP in my opinion, will be on the C: drive which after deletion, will make XP unbootable. I think you should format the Windows98 drive, fixmbr for XP so you are actually able to boot from it and then install Ubuntu which then should pick up XP for dual booting.

---

