---
title: "XP Install on SDA1, Ubuntu on HDA1, grub issue booting XP"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Urinemachine on 2007-06-06
Hey guys - for the longest time I have had to switch boot order for my disks in my BIOS because having XP on my SATA drive SDA1, and Ubuntu on my HDA1, Grub will not successfully load the windows partition.  If I make the SATA the first boot device, XP loads.  If I make the PATA HDA1 drive the boot devices, Grub/Ubuntu loads but if I choose Windows XP from the list, it will not load, probably because its not referencing the right disk for the XP partition.  Anyone help?

---

### Post by eddieb on 2007-06-06
You can't do it. Grub won't work on two different media. I have spent the last couple of weeks trying to get it to work. I have read numerous writeups from different Linux sites and no-one has come up with the solution.

---

