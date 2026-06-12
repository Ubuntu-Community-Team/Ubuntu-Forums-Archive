---
title: "Hardy install freezes"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by raejae on 2008-07-31
I'm trying to install Hardy on a new machine I just built. When I get to the point where it asks me to choose a locale right after it finishes booting, it freezes. I'm using Hardy AMD64 version.

System hardware:
AMD Athlon X2 4800+
MSI K9A2 790FX motherboard
2GB DDR2-1066 RAM
500GB SATA hard drive
ATI Radeon 3870

Any ideas?

---

### Post by Pumalite on 2008-07-31
Try the Alternate CD

---

### Post by raejae on 2008-08-01
OK, I get through the install fine using the alt cd, now it freezes on the progress bar when trying to boot.

---

### Post by Pumalite on 2008-08-01
See if you can boot a Knoppix Live CD and post:
sudo fdisk -lu
cat /boot/grub/menu.lst (from appropriate partition)

---

### Post by Pumalite on 2008-08-01
If you are able to boot it; edit menu.lst and remove 'quiet splash' so you can see where it gets stuck

---

