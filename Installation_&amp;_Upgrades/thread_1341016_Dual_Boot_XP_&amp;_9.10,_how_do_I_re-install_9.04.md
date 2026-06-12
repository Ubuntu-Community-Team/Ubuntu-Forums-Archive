---
title: "Dual Boot XP &amp; 9.10, how do I re-install 9.04"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by dougsspamaccount on 2009-11-29
Laptop is dual boot, XP and Ubuntu 9.10. Given all the problems with 9.10, I want to re-install 9.04 without "nuking" my XP partiton.   Grub is not the primary loader, XP's loader presents XP or Ubuntu, then grub appears.

There is nothing on the Ubuntu partitions I need, just need to preserve the XP.

Thanks

---

### Post by darkod on 2009-11-29
Well just install 9.04 to the same partition(s) where 9.10 is, selecting Manual Partitioning will allow you to use the existing partitions. Don't forget to check the Format box for / so it deletes 9.10 completely.
At the last screen before clicking Install click on Advanced and there will be option not to install grub. I guess that's what you want. Maybe you will neet to adjust xp bootloader after that but i guess you know how to do that since you are dual booting with windows bootloader.

---

