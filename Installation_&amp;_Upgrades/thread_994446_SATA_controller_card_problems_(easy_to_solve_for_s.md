---
title: "SATA controller card problems (easy to solve for someone who knows more than I)"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by nexus_2006 on 2008-11-26
Just replaced a bad motherboard in a PC with UBUNTU 6.06, an athlon XP 2500+, 1GB DDR400, ATI 9600 GPU.  Old mobo had a SATA controller (that ABIT NF7-S was a great mobo) but this one does not.  I bought a SATA PCI card with the Silicon Image SIL3512 chipset.  No problems, card is detected, (now using 8.10) Ubuntu loads the correct modules, card shows up in "lspci" but the drive doesn't show up in the places menu.

How do I get it to go ahead and mount the filesystem on that drive?  It is a REISERFS FS, but I don't know how to figure out what device the drives are if they don't show up automagically.  I rocked this stuff when you just had 4 IDE devices in master/slave setuy, but I don't know what to do with this wonky stuff.

---

### Post by logos34 on 2008-11-26
what does 

sudo fdisk -l

show?

Or

sudo apt-get install gparted

gksudo gparted

Do you see it?

---

### Post by thegeologician on 2009-11-01
Hi, I have the exact same problem, lspci shows the card, fdisk -l does not list the hard drive. Any suggestions/solutions yet?
Thanks!

---

