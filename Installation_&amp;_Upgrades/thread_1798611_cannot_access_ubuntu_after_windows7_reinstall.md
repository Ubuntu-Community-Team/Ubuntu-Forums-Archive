---
title: "cannot access ubuntu after windows7 reinstall"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by abu46 on 2011-07-06
hi guys :)

i had ubuntu 10.10 installed after windows 7 installation, but today i had to reinstall windows 7 (surprise surprise)

now windows has overwritten the grub boot menu and i cannot access my ubuntu installation

i have a live ubuntu dvd from which i booted but it dosent load my previous ubuntu installation and instead shows option for try ubuntu or install it

how can i reinstall grub boot menu and access my ubuntu installation?

---

### Post by Rubi1200 on 2011-07-06
As you already know, GRUB was overwritten by the Windows bootloader.

The simplest method is to boot with the LiveCD, choosing to try not install, and then reinstall GRUB to the MBR:
[https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files](https://help.ubuntu.com/community/Grub2#Copy%20LiveCD%20Files)

---

### Post by abu46 on 2011-07-07
thanks a lot:P
worked liked a charm

---

### Post by Rubi1200 on 2011-07-07
No problem, you are more than welcome :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

