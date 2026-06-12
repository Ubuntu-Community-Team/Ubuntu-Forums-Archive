---
title: "problem at installation"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by arbellior on 2008-01-31
Hi good people of ubuntu,
I'm new in ubuntu, I want to install it and remove any windows leftovers (had enough of it...) but I'm experiencing troubles in installation.
I've downloaded the iso file and burned the CD (version 7.10 desktop)...I tried to boot from disc, it sometimes gives me the ubuntu logo and list and sometimes don't....but when I do arrive to the list and choosing the first option (installation), it gives me the following mesage:

crc error
kernel panic - not sunching: VFS: unable to mount root fs on unknown stack

and some more stuff on the sides....
I want to mention that I haven't formatted the HD and I planned to use the ubuntu installation for it.

What should I do?
Thank you very much....

---

### Post by Bliepo32 on 2008-01-31
Download the cd again, and ensure that the cd doesn't have any scratches etc. If it is still not working, try the alternate install cd. It is text mode only, but it gets the job done.

---

### Post by dabl on 2008-01-31
Sounds like maybe a defective CD/burn.  Did you hold the speed down to 4X when you burned it?  A good CD should behave the same every time you try to boot it, not show different behaviors on different attempts.

---

### Post by w4kh on 2008-01-31
> **arbellior said:**
> I'm new in ubuntu, I want to install it and remove any windows leftovers (had enough of it...) but I'm experiencing troubles in installation.

Same boat as many of us... No need for Gates and Windows with Ubuntu ;)

[QUOTE=arbellior]I've downloaded the iso file and burned the CD (version 7.10 desktop)...I tried to boot from disc, it sometimes gives me the ubuntu logo and list and sometimes don't....but when I do arrive to the list and choosing the first option (installation), it gives me the following mesage:

crc error
kernel panic - not sunching: VFS: unable to mount root fs on unknown stack[/QUOTE]

I have also encountered this error... generally because I have diddled too much with BIOS settings and created a situation where the kernel used to load and install Ubuntu and the BIOS setting were at conflict, which in turn caused the kernel to "panic" which means the kernel executed some command that was "illogical"

[QUOTE=arbellior]I want to mention that I haven't formatted the HD and I planned to use the ubuntu installation for it.[/QUOTE]

Having a "blank" or unformatted hard drive is no problem at all... in fact, when you get there, select "use entire disk" (I have found things go better with the LVM option, but you should not need that if it is confusing...

If you post your hardware configuration, that would help get you better advice as to specific things to try

---

