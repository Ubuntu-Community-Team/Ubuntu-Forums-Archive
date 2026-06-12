---
title: "Ubuntu 14.04.1 won't install on hp 3125 laptop"
date: 2014-10-10
forum: Installation &amp; Upgrades
---

### Post by Paden_Owen on 2014-10-10
I set up a live boot USB. (I don't have a disc drive)
Whenever I try to boot up my PC the screen is black and flickers but the computer is completely unresponsive.

I tried using the live boot on my other PC and it worked fine.

Specs:
Processor: AMD E1-1500 APU with Radeon(tm) HD Graphics 1.48 GHz
RAM: 2.00 GB 
System Type: Windows 7 Ultimate 32-Bit

I've tried everything I can think of and would love some help.

---

### Post by ecophobia on 2014-10-11
Enter boot menue and try acpi=off" option

---

### Post by kc1di on 2014-10-11
Hi Paden_Owen  and welcome to Ubuntu,

I'm a little confused about what's happening, Does the machine boot normally in windows?  If so the machine is working fine.
if not sounds like a hardware failure of some sort. and it would not boot ubuntu either. 

If it boots windows but not Ubuntu  Does the live usb get as far as the boot menu?

if it does try hitting the tab key and you'll get a page with several F key entries at the bottom of the screen select F6 then select nomodeset option hit esc then enter.  it should boot, but will have the wrong video size.  but it should get you to a desktop where you can install ubuntu you have to install the correct video driver after the first boot after the install. 
good luck

---

### Post by Vladlenin5000 on 2014-10-11
> **kc1di said:**
> if it does try hitting the tab key and you'll get a page with several F key entries at the bottom of the screen select F6 then select nomodeset option hit esc then enter.  it should boot, but will have the wrong video size.  but it should get you to a desktop where you can install ubuntu you have to install the correct video driver after the first boot after the install. 

There's no harm in trying this, worst case scenario it won't have any effect. *Nomodeset* usually is for certain nvidia cards only but, again, you can try it.
My bet goes to "acpi=off" suggested above.

---

### Post by kc1di on 2014-10-11
Either way he can find them at F6 ;)

---

