---
title: "Grub will not install in new instalation"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by sasquatchsearcher on 2012-08-04
I just purchased a new HP desktop p7-1227c with AMD quad core A10-5700 with 12 gig of ram, I can install the 64 bit version from live cd but it will not install the grub boot loader, anybody know how i can get a boot loader to work, the computer came with win7 64bit installed in 3 partions a 100 meg system parttition a  large os partioon then a rescue partitions, i disabled the security on mother board but no luck, HELP need this for work

---

### Post by darkod on 2012-08-04
Usually grub2 doesn't install when installing on raid with the live cd.

You can try adding only grub2 after the install (no need to install again), or the Boot-Repair automatic fix. You can also post the bootinfo from Boot-Repair so we can see what is going on and give you more precise advice.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

