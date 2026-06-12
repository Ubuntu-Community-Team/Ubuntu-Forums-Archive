---
title: "Dual Booting Encrypted XP with Ubuntu"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by hpprinter100 on 2008-07-12
i have a 500gb HDD i have formatted it into 2 sections and the 1st one i have encrypted with truecrypt , everytime i boot my PC i type in my booting password then windows starts , im guessting the Ubuntu uses grub but i am unsure if i do install ubuntu on the 2nd partition whether Grub will not be able to load the XP boot . So will it work and i will have dual boot XP + Ubuntu?

---

### Post by fiddledeedee on 2008-07-12
My solution:
install grub4dos on a usb pendrive and then boot usb. Frist boot menu entry is to start the emulated truecrypt rescue image. Second boot menu entry to boot kernel/initrd normal ubuntu.

---

