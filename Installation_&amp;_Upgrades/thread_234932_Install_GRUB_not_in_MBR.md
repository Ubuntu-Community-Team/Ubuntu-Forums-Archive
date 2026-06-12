---
title: "Install GRUB not in MBR ?"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by Vilius on 2006-08-12
Hi,
How to customize boot loader installation place ?
(there was an option in breezy, how about dapper)
Before OS installation of course.

thanks
Vilius

---

### Post by confused57 on 2006-08-12
The Dapper alternate CD installer gives you the option of where to install grub, however the Desktop CD automatically installs to the mbr.

---

### Post by VirtuAlex on 2006-08-12
> **confused57 said:**
> Desktop CD automatically installs to the mbr.
and often does it wrong. When you have SATA and IDE disks in the system it tends to install itself into IDE mbr. It is quite stupid they do not include an option to choose where to put mbr with live CD.

---

### Post by Vilius on 2006-08-12
Maybe it's possible to switch to old text based installer ?

---

### Post by VirtuAlex on 2006-08-12
I do not think live CD has this option. You have to download alternate CD. Or you can install from live CD and reinstall grub by hand (there are plenty howtos) if it put itself on the wrong drive. Whatever fits you.

---

