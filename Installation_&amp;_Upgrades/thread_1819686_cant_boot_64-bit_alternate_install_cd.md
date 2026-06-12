---
title: "cant boot 64-bit alternate install cd"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by headless_ on 2011-08-06
hello,

when i try to boot the 11.04 64-bit alternate.iso i get the following message, after it says that isolinux blabla is loaded:

[INDENT]EDD: Error 8000 reading sector 2855[/INDENT]

and when i remove the cd it says:

[INDENT]gfx.c32: not a COM32R image[/INDENT]

and then there is a grub-shell.

please help. thx
headles

---

### Post by oldos2er on 2011-08-06
Did you check its md5sum? [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by headless_ on 2011-08-08
The md5sum is correct. I solved the problem for me using the MiniCD image. I dont have a problem booting that, neither the standard iso. I remember trying to install 10.10 with the alternate iso didnt work for me too. So maby its a bug?

---

### Post by DMJ on 2011-11-09
I had the same error trying to install from a USB disk drive connected to my laptop. The same disk worked just fine to install my desktop system. I tried creating a new disk and checked the md5sum on the disk image, but no luck. The standard Ubuntu install CD worked fine with the same setup. I ended up installing from an SD card. I need the alternate CD for LUKS volumes. It would be nice if the standard disk could have this capability. Especially now that 12.04 will require a DVD, there's no reason to have so many different install disks.

Disk: Ubuntu 11.10 alternative CD 64 bit
System: Acer 1410 laptop with Asus SDRW-08d1S-U USB drive

---

### Post by tdk77 on 2012-01-19
I had this same error on every ubuntu disk i've burned after 10.04. (always error 8000 but the sector number changes.)
I am just installing 10.04 and upgrading over the internet.

---

