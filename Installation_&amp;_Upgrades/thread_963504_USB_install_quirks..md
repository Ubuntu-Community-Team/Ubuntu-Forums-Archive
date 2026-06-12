---
title: "USB install quirks."
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mjoolnir on 2008-10-30
I've been trying to install 8.10 on my Acer Aspire One (HDD version) via a USB drive (installed with Unetbootin). My trouble is that the USB drive is dectected as /dev/sda and the HDD is /dev/sdb, and even if I choose to install to the HDD (sdb) the kernel and GRUB are installed to sda. Anyone know how to fix this? I also need the whole drive to be encrypted, I'd like one small partition for /boot to be encrypted if possible, and logical one containing / and swap partitions.

---

### Post by C.S.Cameron on 2008-10-30
If, when you get to partitioning, you use manual, you should be able to choose the location to install the boot loader.

---

### Post by mjoolnir on 2008-10-30
Yeah I've been trying to use manual, but even after reading quite a few how-to's on dm-crypt I still don't understand whats doing on and how to partition the disk, is there a visual representation of how Ubuntu sets up a dm-crypt/luks disk by default?

---

### Post by mjoolnir on 2008-10-31
Bump, the USB install is now freezing at 6% after I choose to install the Xubuntu desktop.

---

