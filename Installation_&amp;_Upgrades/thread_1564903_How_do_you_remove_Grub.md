---
title: "How do you remove Grub"
date: 2010-08-31
forum: Installation &amp; Upgrades
---

### Post by Mit240 on 2010-08-31
I have Windows 7 and Ubuntu 10.04 dual-booted on my machine. grub was aautomaticlu installed as the primary loader. Soon i want to nuke my ubuntu partition but i know that will delete grub. Can i remove grub or at least make Windows boot loader default.

---

### Post by zvacet on 2010-08-31
First do [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe")After that you can remove your ubuntu partition.

---

### Post by oldfred on 2010-08-31
per meierfra. mbr.bin may cause problems in some cases better to use lilo
Restore basic windows boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

The windows way is fixMBR or Vista/7 BootRec.exe /fixmbr from windows repair screens.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

