---
title: "No boot filename received"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by serialbox on 2008-08-05
Hi everyone.  I was hoping to get some quick help or pointed in the right direction.

I have a fairly new laptop intel core2 duo and decided rather than setting up dual boot for ubuntu and windows Xp since I ran into problems with the partitioning that I would just install ubuntu as my main os and scrap windows.

The installation process went very smoothly and I had no problems however Im noticing that when I reboot the machine, 

at the DHCP... loading part it sits for about 1 min and then I get an error:
[PHP]
PXE-M0F Exiting ROM
No boot filename received
[/PHP]

Then it goes ahead as normal and boots up and loads ubuntu.

Why am I getting that error despite successfully booting into linux?  Is my computer still looking for a windows boot file first?

thanks!

---

### Post by cariboo on 2008-08-06
It may have something to do with the boot order in your bios. I normally have the boot order set to boot from the cdrom then the first hard drive and disable the rest.

Jim

---

### Post by serialbox on 2008-08-06
great thanks.. I'll take a look at that.  damn glad I made the switch!

---

