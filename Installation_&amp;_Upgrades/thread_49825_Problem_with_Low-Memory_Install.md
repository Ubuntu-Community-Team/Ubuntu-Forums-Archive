---
title: "Problem with Low-Memory Install"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by m0a0nelson on 2005-07-17
I have a low-memory (32 megabyte) Pentium system that I would like to install Ubuntu Linux version 4.10 on.

When I boot from CD-ROM, I get a panel saying this is a low-memory system and that the low-memory installation process will be used.  I hit return to continue (<Continue>), but before resuming, at the bottom left of the screen is the message:

FATAL: Module hid not found.

Doesn't make much sense, perhaps the formatting of the message is not complete.  Is there a module called "hid"?

I get the panel and FATAL message initially (booting) and then also later while the installation system is being loaded into memory.  I can mess around and get up to 87% of the installation system in memory before it kicks out to the low-memory panel and subsequent FATAL message.

Does the FATAL message indicate that the low-memory installation process isn't being started successfully?  Or do I need to give up on this system (getting more memory for this old a system doesn't make much sense)?  The documentation with the CD-ROM says that 32M is enough, but I know I'm right at the boundary,
and strange things happen at boundaries.

Thanks for any help I receive.

---

### Post by DJ_Max on 2005-07-17
Dunno about the error, but your speculation is probably correct. Have you looked at [http://www.ubuntulite.org/](http://www.ubuntulite.org/) .

---

### Post by RJARRRPCGP on 2005-07-18
[QUOTE=m0a0nelson

FATAL: Module hid not found.
[/QUOTE]

That looks like an error message you can get if the RAM is bad. You should run Memtest86 to check for RAM errors.

---

### Post by m0a0nelson on 2005-08-16
I acquired memtest86 and ran it on my low-memory Pentium system.
I let memtest86 run for three passes - no memory errors detected.

---

### Post by nad on 2005-08-21
The hid module is related to usb devices (human interface device).This, in itself, will not cause a failed installation. There could be bios problems related to an early implementation of usb.

I am not familiar with the "low-memory installation", however, this is nowhere near enough to run a desktop system. Even a low-resource window manager like xfce will have problems. Maybe  without without some extensions or better yet icewm or twm (huh?).

If you can't get it to at least 64MB, use it for a firewall, router, dhcp server, doorstop. Or if you really want to play with it the way it is, see [www.linux.org](www.linux.org) , for dozens of distributions designed just for such a system.

---

