---
title: "No HDD detected"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by sknagesh on 2010-12-28
I have Mint 9 installed on a 120GB, WD SATA HDD. Now I want to install Ubuntu 10.10 on this HDD. Downloaded i386 desktop image and created a bootable USB stick with the image. System boots fine but installer do not detect My HDD. It only lists my USB drive. Even Gparted donot detect the drive. Typing sudo fdisk -l also lists only my USB Drive.

Can any one Help me install Ubuntu on to this system.

Thanks
SKN

---

### Post by dino99 on 2010-12-28
and Mint is running smootly ? what if you check the hardware from Mint ?

sudo update-pciids && update-usbids

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

on my system the SATA are set on AHCI into bios, and i've declare the boot hdd as the first one

---

### Post by sknagesh on 2010-12-28
Yes mint is running smoothly. I will try the command in mint and report back.

Regards

SKN

---

### Post by sknagesh on 2010-12-28
Still No luck. Can Any one help me

SKN

---

