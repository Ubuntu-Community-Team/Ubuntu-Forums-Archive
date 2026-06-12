---
title: "Installing Ubuntu on a Thinkpad X61 (with USB optical drive)"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by chaddasaurus on 2008-03-26
I have a Thinkpad X61 which does not have an internal CD drive, so I have an external CD drive attached via USB port (and I have used the left USB port as some people on the forum expressed problems with the right two USB ports).  When I boot off the cd, I get to the very first Ubuntu installation screen, but when I highlight "Start or install Ubuntu" and press enter, everything kind of freezes and soon the cd in the optical drive stops spinning.  Do I need to change one of the boot parameters to use this external CD drive? I have already changed the SATA recognition setting in my BIOS to "Compatability" mode. I am new to Linux.

---

### Post by chaddasaurus on 2008-03-26
I should probably add that it is Ubuntu version 7.1

---

### Post by jfif on 2008-03-27
Somebody mentioned the SATA hard drive problem. 
Have you tried to change the SATA mode to 'compatibility' from 'AHCI' in the BIOS?

---

### Post by chaddasaurus on 2008-03-28
Yes, I made that change, but it did not have any effect on the installation problem.

---

### Post by Whiffle on 2008-03-28
Which install CD are you using?  If you're using the LiveCD installer, I'd probably try the alternate CD.

---

### Post by chaddasaurus on 2008-03-28
I am using the regular CD. What is the purpose, or possible advantage in this case, of the alternate CD? And if it is "text based" won't that be even harder to use for a newbie to linux?

---

### Post by chaddasaurus on 2008-03-31
Can anyone tell me what the boot parameters:
hd=cylinders,heads,sectors
and
floppy.floppy=thinkpad
mean?

---

