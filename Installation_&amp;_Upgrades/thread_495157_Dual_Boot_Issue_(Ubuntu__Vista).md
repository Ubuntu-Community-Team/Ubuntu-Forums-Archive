---
title: "Dual Boot Issue (Ubuntu / Vista)"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Skrypt on 2007-07-07
Ok, here's where I'm at:

I had Vista installed on my Primary (D:, /dev/hda ntfs) and just partitioned my Secondary (C:, /dev/hdb). I've made a 100MB swap partition and a 9899MB (/dev/hdb1 ext3) partition with Ubuntu on the Secondary. When asked, I installed the grub into the MBR on the Primary but when I booted there was no boot option for Ubuntu.

As for PC specs:
AMD Athlon 64 3400+ 2.21 GHz
MSI K8 Neo Platinum (nVidia nForc3 250Gb)
Corsair 512x2MB DDR400 XMS w/ Heat Spreader
PNY GeForce 6800 Ultra 256MB DDR3

I'm installing from the LiveDVD-AMD64.2007.0 Installer.

Any ideas?

---

### Post by Pumalite on 2007-07-07
If you have one hard drive and you are talking about partitions: you have to partition within Vista before install. If you have two hard drives: go to BIOS and invert the boot order. See what happens and report back.

---

### Post by Skrypt on 2007-07-08
2 Hard drives.

When the boot sequence is changed in BIOS, I get a screen that endlessly produces "GRUB GRUB GRUB GRUB _ " and continues writing.

---

### Post by Pumalite on 2007-07-08
Try Super Grub:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by taylorsnow on 2007-07-08
try dropping Microsoft all the way.... Vista is power hungry and im sure we will see soon not to secure. 2008 is the year that Linux will gain Power...

---

### Post by Pumalite on 2007-07-08
That too.

---

### Post by Skrypt on 2007-07-08
ty. Super Grub will work but I can't set it up to boot without the CD. Maybe some more tinkering is in order.

Now... if only I can figure out how to load the GUI.

---

