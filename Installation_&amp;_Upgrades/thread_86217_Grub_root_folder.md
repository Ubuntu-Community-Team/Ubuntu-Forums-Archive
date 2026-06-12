---
title: "Grub /root folder"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by imaca on 2005-11-04
When I try install Ubuntu on my second (sata) harddrive, grub fails to boot and returns Error 21, which as far as I can tell means the HDD doesn't exist.
I changed the installation so that /boot was on my first hard drive and it all worked.
My question is:
 Does the /**b**oot folder always have to be on the first HDD or is this a problem with Grub not handling the SATA  HDD?
Ideally I would like to have my entire Ubuntu installation on my SATA disk.

---

### Post by Kyral on 2005-11-04
There is an issue with SATA at the moment sorry to say. I mean it shouldn't matter where /boot is as long as GRUB points to it (I boot off a small 8 GB HD, but GRUB is installed on the MBR on my 300 GB HD, which is first in the boot sequence in the BIOS)

---

