---
title: "Grub loading stage 1.5, error 18"
date: 2006-04-04
forum: Installation &amp; Upgrades
---

### Post by BernieM on 2006-04-04
Down-loaded Breezy Badger, burned CD. Installation failed on packages(apparently bad CD). Burned new CD. Blanked hard drive. Installation went OK until re-start. At end of boot sequence get "grub loading stage 1.5" and "error 18". How do I get around this? This is my first experience with linux.

BernieM

---

### Post by lha on 2006-04-05
"18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general)."

So your computer is a bit old. A bios update that adds support for larger drives would help, if you can find one. (Try to search from the site of the manufacturer of your motherboard.) Updating bios can be a bit tricky. Another option is to create a smaller root partition (4-8 GB) in the beginning of your hard drive, then make a swap partition (~0.5GB) and finally use the rest of your hd for a /home partition. (Third option is to create a small /boot partition (50-100 MB) in the beginning of your hd and use the rest for root.)

---

### Post by lha on 2006-04-05
If you are not familiar with partitioning, [check Herman's site]("http://users.bigpond.net.au/hermanzone/p14.htm"). It has a couple of installation guides for beginners. They have a lot of screenshots, so they may be helpful. Those guides' primarey target are those who want to dual-boot, so you have to pick the relevant parts yourself.

---

