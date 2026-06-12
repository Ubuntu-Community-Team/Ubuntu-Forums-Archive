---
title: "installing via bootalbe USB"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by livin4th on 2012-09-21
Hi,
       I am trying to install ubuntu linux from a bootable pendrive on my sony  waio PCG 7D2L. But I couldn't get it to boot from the pen drive. I set  my boot order to 

Optical drive
Network
Floppy Disk Drive
HDD

there is no USB option present. Also the CDROM is dead so USB boot is  the only option. Can anyone please suggest how to boot it from the USB.  The above order just boots the existing windows XP.

The bootable USB works fine with my other Dell laptop. I thought I would look into the Network boot if everything else fails. Is there any way of using my existing harddrive to use to install a new ubuntu partition? I already have a running XP on the laptop.

Thanks

---

### Post by oldfred on 2012-09-21
Sounds like system may be too old to boot USB. Did you look under HDD. My flash drives boot as hard drives, but my system shows many USB choices.

Some have said this works.
Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Others just remove hard drive and connect to anther computer to install. As long as you do not install any proprietary drivers (unless Sony needs something) you then can put drive back in and have it work.

---

### Post by livin4th on 2012-09-21
Ya I checked all the available boot devices. The only one listed is a toshiba hard disc under HDD boot option. My kingston pendrive was not recognised any where.

---

### Post by krs000 on 2012-09-22
[PLOP]("http://www.plop.at/en/bootmanager/index.html") boot manager is your friend. It will boot plop and then PLOP (not BIOS) will let you boot any bootable USB.

---

