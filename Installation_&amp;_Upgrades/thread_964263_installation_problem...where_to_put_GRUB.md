---
title: "installation problem...where to put GRUB"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by davide1982 on 2008-10-30
Hello to all

That's my question ... first i state that I have already several times tried to install earlier versions of UBUNTU now i give a try to 8.10, and i'm not completely newbie...

well, so I'm just installing the 8.10 and I performed the manual partition ... now my setup disc is made as follows:

hd 1st and 2nd both 320 gb in RAID 1 configuration on Mobo SATA2 controller integrated intel ICH10 with win xp (and they do not have to be touched and must remain as they are ...)

hd 3rd 200 gb always on port SATA2 controller intel ICH10 i use that for data storage with a 150GB partition ntfs

the remaining 50GB on hd 3rd are divided in: 1gb for the swap, 49gb in ext3 to install ubuntu 8.10 ...

Now ... the nice GRUB boot loader default me to stick on (hd0), I want it to be the least intrusive as possible and obviously let me start correctly windows in the raid 1 ...

you say do I leave on (hd0) or put it somewhere else or I do?

Clearly, I want to have a chance if removed to eliminate linux grub easily and naturally and keep me able to load windows on the raid 1 ...

Thanks in advance for your support

P.S. 

Someone told me to installa GRUB on the 3rd HD i think (hd3) and put it first in boot setup...don't know if this might be work...

...and sorry for bad english

---

### Post by lemming465 on 2008-10-31
> Someone told me to installa GRUB on the 3rd HD i think (hd3) and put it first in boot setup

Given your hardware setup and constraints, that sounds like your best choice.  When the 8.10 install gets to the bootloader step be sure to use the *advanced* button, otherwise it will do something unfortunate to the intel fakeraid setup for XP.

If you can't get your BIOS to boot the second hard drive, it is possible to add an entry for Linux to the XP boot.ini menu.

---

