---
title: "Dual Boot: IDE SATA"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by samjaynes on 2007-02-11
Thanks for reading this thread.   I am planning on purchasing a WD 250GB IDE HD soon to install Ubuntu on.  Currently my PC has XP on another WD 160GB IDE.  My question is how does installing a SATA HD later on to install possible XP on to dedicate the existing 160GB to MythTV affect GRUB?  From what I understand, GRUB recognizes that XP is currently installed on another HD, but will it pick up SATA devices as well, now and later.

Additionally, I would like to know if I purchased a SATA 250GB drive instead of an IDE, would this work out under a dual boot situation as I don't know how Master/Slave configs would work then???

PC Configs:
ASUS 9V
AMD 64 3000+
nVidia 5200
512MB Dual Channel Memory

---

### Post by confused57 on 2007-02-11
You might want to consider this option:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

As long as you set your Ubuntu drive in bios as the first hard drive booted, there "shouldn't" be any problems to add a SATA drive along with your 2 IDE drives...you'd just need to change your entry in grub to boot the new Windows install...if Ubuntu recognizes your SATA controller, you should be OK.

---

### Post by reiki on 2007-02-11
your mileage may vary, but I have an ASUS motherboard as well (P5LD2) and it has both IDE and SATA drives in it. Ubuntu had no problem with the sata controller at all and I can boot from ide or sata. If you change your boot order in BIOS you may have to copy a /boot/grub/menu.lst from one place to another, but other than that it works fine.

---

