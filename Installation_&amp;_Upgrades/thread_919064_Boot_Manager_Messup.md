---
title: "Boot Manager Messup"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by rapsball4 on 2008-09-13
So I've installed this exact setup many times before and had no problems.  I have a 500GB drive that is just data, and a 750GB drive split into a Vista partition, a swap area, Ubuntu, and more data space.  I've always installed Vista and then when I installed Ubuntu afterwards it put GRUB over the Vista bootloader and it was all fine.  

This time it didn't work.  GRUB didn't go over the Vista manager.  I tried to used EasyBCD to add Ubuntu, but that didn't work either, so I used Super GRUB to put GRUB back on instead of the Vista loader.  But GRUB won't connect to anything, saying that the partition doesn't exist for Ubuntu, and:

"Starting Up...
BOOTMGR is missing
Press Ctrl+Alt+Del to restart"

for trying to load into Vista.

---

