---
title: "Root vs Rootnoverify"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by Pandora on 2005-09-21
My question pertains to the choice in default GRUB options for booting windowsxp. I've read the GRUB documentation and I'm still confused. I want to know why ubuntu has chosen to setup GRUB by default with the **root** option rather than the **rootnoverify** option for my windowsXP install. Is there any advantages or disadvantages to changing to rootnoverify?

Windows xp is on the primary partition on my hard disk. I've tried both root and rootnoverify and both work. I'm just curious as to why.

Thanx for your help...and my apologies if this thread has been started in the wrong forum.

---

### Post by Xian on 2005-09-21
Rootnoverify is similar to root, but it does not attempt to mount the partition. This is useful for when an OS is outside of the area of the disk that GRUB can read, but setting the correct root device is still desired.

---

