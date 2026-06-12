---
title: "Installed But Doesn't Boot"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by tree6014 on 2007-12-18
I was switching my desktop from Fedora 8 to Ubuntu 7.1 and I deleted the partition from the drive and booted from the i386 install disk. Everything seemed to work fine and it ran from the live disk, but, after it installed and rebooted, it left me in a GRUB prompt that looked like this:

               GNU GRUB  version 0.97  (636k lower / 2096964k upper memory)

           [ Minimal BASH-like line editing is supported.  For the first word, TAB
             lists possible command completions.  Anywhere else TAB lists the possible
             completions of a device/filename.]

          grub> _


My system specs are:

AMD Athlon 64 X2 4200+
2GB Mushkin DDR2 800
Nvidia GeForce 7900 GT OC 256MB GDDR3
250GB SATA drive for Windows
320GB SATA drive for Linux

Any advice would be much appreciated.

---

### Post by tree6014 on 2007-12-18
OK, just fixed my problem by mistake. I changed my first boot drive to be my windows drive and then it loaded grub correctly and booted into Ubuntu correctly. Strange that it has to boot from a drive it isn't supposed to be installed on.

---

