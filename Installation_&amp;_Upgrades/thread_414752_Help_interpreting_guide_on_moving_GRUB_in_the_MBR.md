---
title: "Help interpreting guide on moving GRUB in the MBR"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2007-04-20
Hey

I've just installed Ubuntu 6.10 on my machine and I can't get it to boot without using GRUB on a floppy.

The reason for this is the controller on my motherboard to which my two hard drives are connected, according to another guy who've also experienced this problem, "*overwrites four bytes of /dev/hde with zeros at booting time.*"

The controller is a HPT370 Raid Controller but I'm not using the RAID functionality -  it is turned off. They basically work as IDE connectors for my hard drives because the two IDE connectors without RAID on my board are utilized by my two DVD drives.

He has written a guide on how to circumvent this problem but since I'm not experienced with Linux in general I'm having trouble following his solution. That's the reason I'm writing here, in hope that someone with a bit more knowledge can guide me in following his workaround. Here's the link to his solution:

[http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html](http://lists.gnu.org/archive/html/bug-grub/2004-07/msg00113.html)

Thanks in advance,

-Rune

---

### Post by runesvend on 2007-04-21
*bump*

Anyone? Anyone at all?

---

