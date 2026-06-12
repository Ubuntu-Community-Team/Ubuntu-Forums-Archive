---
title: "WINGRUB, unrecognized partitions, and Error  22"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by halfthelaw on 2006-06-14
I needed to temporarily reformat my ubuntu partition, which also has my /boot directory (and hence all GRUB files). Realizing there would be problems if I did this without first getting another boot loader, I installed and ran WINGRUB ([http://grub4dos.sourceforge.net/wingrub.html)](http://grub4dos.sourceforge.net/wingrub.html)). However, even after supposedly installing to the MBR, I still get my old GRUB menu. The problem is that when I go to boot either my Ubuntu or Windows installs, I get the dreaded Error 22. I then booted off the Ubuntu live cd, and although it throws up a disk error and doesn't automount any of my partitions (not sure if it was supposed to or not), I can still mount all of my partitions just fine.
But how do I either get my old GRUB/partition table/MBR working again or get WINGRUB working?

---

### Post by Sutekh on 2006-06-14
What is the disc error and automount errors that you get from using the LiveCD?

Have you tried the methods in this link?

[Ubuntu Wiki - Recovering GRUB](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

