---
title: "Kubuntu Install w/SATA"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by magikx21 on 2007-11-13
I have ran Kubuntu 7.4 x64 and 7.10 x64 on my one pc for awhile but recently I replaced my IDE hard drive with an SATA one and cannot get Kubuntu to install. With both 7.4 and 7.10 I install the OS using the live cd and change the grub location to sdb1. When I reboot though grub pops up then says error file not found with both installs. How do I get this working?

---

### Post by magikx21 on 2007-11-15
Alright solved, when I told it to install grub on hd0 it was actually putting it on the wrong harddrive but then when I told it to use hd2 grub would load but would not load the OS. The trick for me was to tell it hd2 then edit the grub menu changing it to hd0.

---

