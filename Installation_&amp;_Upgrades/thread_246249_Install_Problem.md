---
title: "Install Problem"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by asus25 on 2006-08-29
Asus A8R32 MVP Deluxe
AMD Opteron 170
Dual HP DVD Burners
4GB OCZ EB PC3200
ASUS Crossfire
ASUS 1900XT

Trying to install and keeps hanging at:

ohci_hcd 0000:00:1c.0: OHCI Host Controller

at splash i added ide=nodma ide=reverse pci=noacpi 
also tried irqpoll

any help would be greatly appreciated. THANKS

---

### Post by asus25 on 2006-08-30
This problem solved!! Disable USB Legacy Support in BIOS. Unfortunately i cannot get to installer due to my 1900xt graphics card. Says unable to start x server.

---

### Post by zxee on 2006-08-30
I'm not familar with that gpu but take a look at your options at the begining installer screen. You should be able to choose framebuffer device or another basic video output.
Also see the install guides here: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

