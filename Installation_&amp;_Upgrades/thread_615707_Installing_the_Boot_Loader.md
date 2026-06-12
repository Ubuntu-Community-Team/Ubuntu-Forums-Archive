---
title: "Installing the Boot Loader"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by dcahrakos on 2007-11-17
Hi,

im trying to install ubuntu in a seperate partition with Vista already installed. with previous installs of other linux distro's ive avoided installing GRUB to the MBR because I did it once and it make vista unbootable afterwards.

so what I was wondering is this, when installing ubuntu with the live cd installer, and when it gets to where I can change if I want the boot loader installed, and where I want it installed, there is (hd0) if  ubuntu is getting installed into /dev/sda2, would I change that (hd0) to (hd0,1)? if I wanted it to install to the root partition of ubuntu...thats what it seems like to me, since some searching seems to tell me that GRUB starts at 0 for the first partition.

Thanks in Advance.

---

### Post by Pumalite on 2007-11-17
Correct. Make sure you allocated space for Ubuntu with the Vista partitioner.

---

### Post by dcahrakos on 2007-11-17
Thanks, I just had to make sure before I did it, just incase I made Vista unbootable. Yeah, everything is already ready actually, ive installed it before without the bootloader, and tried the grub-install but then that didnt work, so I searched and found out that it doesnt work.

Anyway...thanks again, that makes things easier for me :)

---

### Post by Pumalite on 2007-11-17
You are welcome. Good luck.

---

