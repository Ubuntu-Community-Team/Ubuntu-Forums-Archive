---
title: "Installation error related to hard drive?"
date: 2007-09-16
forum: Installation &amp; Upgrades
---

### Post by Cleric. on 2007-09-16
I am trying to install Xubuntu on an older computer (PIII 800MHz, 256MB RAM), but whenever I run the installer, it gives me an error saying:

"The ext3 filesystem creation on partition 1 of SCSI1 (0,0,0) (sda) failed."

What is strange is that the hard drive is internal; there aren't even any other hard drives connected to the computer. 
I don't know why it would be recognized as "sda" at all.

What exactly is going on?

---

### Post by logos34 on 2007-09-16
Feisty uses the libata scsi subsystem drivers to ID disks, so it sees everything including IDE as 'sd_'.

You might want to use gparted to reformat sda1 as ext3 and run through the install once more.

---

