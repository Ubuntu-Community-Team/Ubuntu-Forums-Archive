---
title: "Installation hangs on trm290 IDE chipset support (Feisty and Gutsy)"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by barbex on 2007-11-22
Hi all!

I'm trying to install Ubuntu on my old Laptop. 

Configuration:
SIS650 Chipset with a SIS 961/962 Southbridge
Intel Pentium 4, 2 GHz
256 MB RAM
IDE Harddrive (Hitachi)

I know it is a bit weak with the RAM but I'm going for a minimal install. I have tried just running the Gutsy Live CD but it never got passed the hardware detection. After reading about various problems of Gutsy and IDE drives I dusted off my Alternate install CD of Feisty to install a commandline system.

Not only is the install maddening slow, it also hangs every time on 10% during hardware detection with "Loading module 'trm290' for 'IDE chipset support'...".

I have tried the usual boot options (apm=off acpi=off and noapic nolapic) with the same result every time.

I'm not a linux expert by any stretch of imagination and I am lost here.

What else can I try?

---

### Post by barbex on 2007-11-23
Sigh, nobody?

Let me rephrase my question:

Is there a way to tell the installer to use some sort of generic IDE module? 


I have in the meantime installed a debian server and SUSE 10.1 and both worked so there must be a way to get Ubuntu to install too. I just need some help as to How.

Please.

---

