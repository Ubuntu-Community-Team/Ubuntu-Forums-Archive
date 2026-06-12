---
title: "Installation problems on IBM T 21"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by miked130 on 2008-03-28
Trying to load/install Linux on an IBM Thinkpad T21 and the hardware apprers to hang while loading.

Here is the last line I see before the hardware hangs.

119.376849 ACPI:  PCI Interrupt 0000:00:03.1[A] -> Line [LNKC] -> GSI 11 (level, low) -> IRQ11

I get the same error with the both the latest stable versions of Ubuntu 7.10 and Debian 4.0.  I plan on using the laptop as a file and print server.  Based on the printer I have, I'm kind of tied to the Distros/Versions listed here. 
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)

Let me know if anyone has seen a work around, or has a recommendation to help me get past this point.

---

### Post by kerry_s on 2008-03-28
with debian type> install noacpi acpi=off apm=on

if i remember correctly. :confused:
i did it for a friend sometime ago, i used xfce4->
[http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-xfce-CD-1.iso)

we also found alot of answers at thinkwiki->
[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)

---

