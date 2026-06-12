---
title: "High gpu temperature after upgrading to 13.04"
date: 2013-05-02
forum: Installation &amp; Upgrades
---

### Post by MyUtopia on 2013-05-02
Hi everybody! I've noticed that gpu temperature is quite high (about 74°C) after upgrading ubuntu from 12.10 to 13.04 (64bit) and the fan spins very fast. This has never happened in 12.10. Maybe a unity issue? I have a Dell Studio, Intel I5 and Ati Mobility Radeon Hd 4570. I'd really like to solve this problem. Any idea? Thanks to all of you!:KS

EDIT: I've just tried to reinstall 12.10 and 12.04 (I had no problem at all with them), but NOW the same problem appears: high fan speed and gpu temp over 70°C!!!! I can't find an explanation. In addition if I switch to Windows 7 (I have a dual boot), the problem disappears and everything goes back to normal. Please help me, I'm running out of ideas!](*,)](*,)

---

### Post by andreagangemi on 2013-06-05
I'm experiencing a somewhat related problem.
In my case the fan sped does not increase, resulting in an overheat... causing the PC shutting down abruptely.

Looks like it happened after installing lm-sensor and Psensor

I'm running Ubuntu Studio 13.04 
I have a 2009 Toshiba satellite (Athlon X264 and ATI)

---

### Post by andreagangemi on 2013-06-05
Seems that things has been solved by adding 
acpi_osi=Linux
options in the kernel boot parameters

Actually I had to do the same things in my previus version (11.10) but I always forget to do it

---

### Post by andreagangemi on 2013-06-12
Correction

To solve the issue on my toshiba satellite L300D I did the following 2 things:
1. I restored the BIOS to the default values
2. I put "acpi_osi=" (left blank, no Linux or wathever) in the kernel boot parameters

---

