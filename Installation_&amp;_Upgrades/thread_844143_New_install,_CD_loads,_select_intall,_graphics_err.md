---
title: "New install, CD loads, select intall, graphics errors after splash screen"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by coletrx on 2008-06-29
Hi there, many thanks for any sugestions, have tried serching the forums, will get straight into it..

The problem:
After selecting install from the boot CD (ubuntu install menu ie run live or install) , ubuntu logo appears with the bar sliding from side to side, then bar changes to slide once from left to right, then screen black, then green and black vertical lines appear on the screen about 1cm appart - they wont go away.

More info:
I have a dual screen setup, with DVI and VGA. Before the error, both screens display the same thing (POST, then ubuntu loader). At the error, DVI screen is black, VGA is displaying the green + black lined screen.

Failed fixes: 
Ive burnt the CD twice, once at slow speed, once at slowest. Ive checked the CD for errors, its sys ok. In BIOS, primary graphics out is set to be my video card.

Ive spoken to a Linux friend, he said I might be able to force the installer to run at a lower graphics setting, but I couldnt find how to do this on the Internet.

Hardware:
Gigabyte GA-G33M-S2 and 7600 silent video card. 3GB Kingston value RAM. Core 2 Duo E6300.

Any sugestions?

---

### Post by PmDematagoda on 2008-06-29
Did you try removing your dual-screen setup and then trying to install Ubuntu?

---

### Post by coletrx on 2008-06-29
Will try that now :)

---

### Post by coletrx on 2008-06-29
It works now!

Im writing this from inside the Live CD load. I disconnected the VGA cable, and it booted fine. Thankyou very much for the help :)

---

### Post by PmDematagoda on 2008-06-29
> **coletrx said:**
> It works now!

Im writing this from inside the Live CD load. I disconnected the VGA cable, and it booted fine. Thankyou very much for the help :)

No problem, but if you want to use the Dual-Screen setup, then you will have to install the Nvidia driver before doing so(it is a must!).

---

