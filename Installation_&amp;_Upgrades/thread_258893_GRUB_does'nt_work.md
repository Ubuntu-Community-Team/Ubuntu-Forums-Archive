---
title: "GRUB does'nt work"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by michelev on 2006-09-16
Hi,
I'm just install last release of ubuntu (alternate and live cd) on my external firewire HD, but when I restart my system GRUB doesnt appeare and my win xp start without problems.
I dont know why, but I can't choice the OS.
On my system I have an AMD Athlon 64 and the BIOS support the boot from external devices (1° choice).
Thanks to all
bye
michelev #-o

---

### Post by orb9220 on 2006-09-16
Grub is usally installed to the first hd mbr and needs to be there for a  dual boot. But if you are changing the bios to boot the firewire drive then the grub loader needs to be there instead.

During the alternate cd install did you tell the grub loader to install itself on the firewire hd ?

---

### Post by michelev on 2006-09-17
Thanks Orb..
I found the problem. In my bios there was 2 option to establish the boot devices order, now the system find GRUB and start it.
So, I have 2 new problems:

-> selecting ubunto the system write: Error 15, but I think that I have found the solution.

-> selection Windows the system write: Error 13, and I haven't a solution. What do u think about?

Thanx a lot,
bye michelev

---

### Post by cotcot on 2006-09-17
Installing linux on an external HDD is not that simple. Using the system to boot Ubuntu from a pendrive should work for an external HDD too. See link in my signature for these instructions.

---

### Post by orb9220 on 2006-09-17
[http://ubuntuforums.org/showpost.php?p=1221276&postcount=153](http://ubuntuforums.org/showpost.php?p=1221276&postcount=153)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28LiveUsb%29)
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by michelev on 2006-09-23
TNX to all. :-({|=

---

