---
title: "wan't reboot after upgrade."
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by x-calibur on 2010-03-06
Hi, 

After i upgraded my ubuntu via ```
aptitude upgrade
```
I am not abble to reboot anymore. 

When booting I get the following message:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I use ubuntu 9.10 Karmic wich uses grub2 as bootloader. 
So editing the menu.lst file will not work for me. 

When I boot from the grub boot menu (holding shift at boot) i can't boot from 
Linux 2.6.31-20-generic-pea
but I can boot from
Linux 2.6.31-19-generic-pea

I run ubuntu as a single operating system from a software raid, using two sata discs on md0

Who can help me on this issue...

P.s. this is my first post, so I hope I can provide the right information.

---

### Post by x-calibur on 2010-03-07
Is there a way to make the .19 version the default boot?

---

