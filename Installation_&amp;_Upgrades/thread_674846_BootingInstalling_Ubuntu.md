---
title: "Booting/Installing Ubuntu"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by Salaminic on 2008-01-22
Okay, so here's the problem. I got Ubuntu 7.10, and burned it to a DVD. Now I simply pop it in and restart. BUT, it doesn't show me to press some random button to boot from cd. I installed Ubuntu before, and it worked fine. Now it doesn't. On my machine, I got... Windows AND Fedora installed. Each on it's own partition. Maybe it's because of the Fedora boot thing. You know... The Fedora boot loader that installs and replaces the old Windows one. I don't know how is it called. Anyway, help is appreciated.

---

### Post by kellemes on 2008-01-22
> **Salaminic said:**
> Okay, so here's the problem. I got Ubuntu 7.10, and burned it to a DVD. Now I simply pop it in and restart. BUT, it doesn't show me to press some random button to boot from cd. I installed Ubuntu before, and it worked fine. Now it doesn't. On my machine, I got... Windows AND Fedora installed. Each on it's own partition. Maybe it's because of the Fedora boot thing. You know... The Fedora boot loader that installs and replaces the old Windows one. I don't know how is it called. Anyway, help is appreciated.



In order to boot from disk you need to enter BIOS and set the diskdrive first in the list of boot-devices.

---

### Post by erginemr on 2008-01-22
Hi,

I believe you should start by checking your BIOS settings; the boot order.

---

### Post by acidsolution on 2008-01-22
Select cd/dvd rom as your first boot device in BIOS settings .
Not only fedora all linux bootloader does the same replaces windows bootloader

---

