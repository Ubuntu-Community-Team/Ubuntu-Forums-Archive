---
title: "Buffer I/O error ...edgy livecd boot problems"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by denad on 2006-10-26
When I try to boot edgy, the splash screen keeps loading for a while and then I get a lot of lines like this:

[17179698.500000] hdc:ide_intr:huh? expected NULL handler on exit.
[lots of numbers here too] Buffer I/O error on device hdc, logical block 357566

Athlon XP 2800+
2*512mb RAM
120GB Seagate IDE
Writemaster DVD/CD burner

I searched this forums and then tried using irqpoll as a boot-option in the installer menu, then removing one of my memory sticks, neither worked. Is there anybody that has a solution to this?

---

### Post by unisol on 2006-10-26
do you have raid on your system? are you installing from the livecd? if the livecd is the problem,try downloading from here,[http://ftp.osuosl.org/pub/ubuntu-releases/edgy/](http://ftp.osuosl.org/pub/ubuntu-releases/edgy/) it has the alternate installcd

---

### Post by iHaveHerpes on 2006-10-26
I need a solution to this, too. (I'll try what you said above)

---

### Post by denad on 2006-10-27
No I don't have raid. I guess I will try using the alternate installer then.

---

### Post by dampier on 2006-11-25
I had this error on a 48x drive and on a 32x drive. Worked well then on a even older 8x drive.

---

