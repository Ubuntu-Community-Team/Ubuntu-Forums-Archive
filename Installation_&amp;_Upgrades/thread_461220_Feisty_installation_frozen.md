---
title: "Feisty installation frozen"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by ultra2k on 2007-06-01
Hi, i am trying to install ubuntu feisty on my new machine

Amd64 5200x2
Abit KN9s
hdd maxtor 320 sata2
vga asus gf6200

i tryed the 64bit version and the 32, both hangs during the partitioning of the hdd (randomly sometimes at the beginning, some times during "formatting")
the system frozes and i need to reboot.
the 32 bit version starts correctly with noapic (MP-BIOS bug: 8254 timer not connected to IO-APIC)
the 64 bit version boots correctly, but as i described during install all frozes.

what could i do?
i am downloading the "alternate cd" right now..

thanks for helping, dont know what to do

---

### Post by mike23 on 2007-06-01
hey i got exactly the same pc and the same problems!!! 64bit freezes and with 32 bit i get that APIC thing. maybe theres something wrong with our amd's after all?

Al that "designed for windows" and "vista capable" crap on those stickers on the case.....

---

### Post by oobergeek on 2007-06-01
Hey!

I don't have the same system setup as the 2 of you do but I've tried to install 7.04 on a bare HD and during the install it just stops..(quits)..??

I've had 7.04 running on a dual boot system with WinXP, so I can't for the life of me figure out what the problem could be..?? 

Any help would be much appreciated!

---

### Post by ultra2k on 2007-06-04
adding noapic to the boot line solved
i figured out that the bios versione is bugged, i upgraded to the last relase from abit (2.0) (as suggested this sould fix the problem)
but i still cannot use the sistem without apic (X frozes after few  seconds)

---

