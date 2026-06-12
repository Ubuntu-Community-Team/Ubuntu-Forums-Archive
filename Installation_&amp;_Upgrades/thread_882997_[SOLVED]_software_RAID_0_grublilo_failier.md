---
title: "[SOLVED] software RAID 0 grub/lilo failier"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by carbon-14 on 2008-08-07
I was trying to install Ubuntu 8.04 on a friends machine using the alternate install CD. I setup both drives (Identical 500 GB) for RAID configured a RAID 0 and formated the new md0 to ext3. everything seems to go fine until it tries to install grub. It then says Fatal Error, so I tried LILO which says fatal error 1. When you try to boot GRUB starts to load then encounters a error 21. Does anyone know what is up?

---

### Post by carbon-14 on 2008-10-02
Well if anyone else has this problem the issue was I was had to make a /boot partition off the RAID array in order to boot.

---

