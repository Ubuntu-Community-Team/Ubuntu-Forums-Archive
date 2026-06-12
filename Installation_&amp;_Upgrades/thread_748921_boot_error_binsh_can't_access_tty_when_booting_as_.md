---
title: "boot error /bin/sh can't access tty when booting as HDD-1 - fine as HDD-0"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by jh1000 on 2008-04-07
Ubuntu boots fine when it is on hard drive in cable select master position but when I moved disk to cable select slave position and set BIOS to boot off it (HDD-1), ubuntu loads and eventually gives  error

/bin/sh can't access tty; job control turned off
and goes into
(initramfs)

it seems that it is referring to the master drive despite bios telling it to boot off  the slave. I don't want to dual boot with grub,etc. on both drives. the master (windows) boots fine. 

red hat booted fine in similar configuration. from slave position HDD-1.

---

### Post by jh1000 on 2008-04-13
I did a workaround. I put ubuntu drive as cable select master HDD-0 and moved windows drive to cable select slave HDD-1. They both boot fine.
I still think there is bug in boot sequence of Ubuntu. I don't think it is grub. I think ubuntu's boot sequence reverts to the master no matter what the BIOS tells it. 
The version I'm using is ubuntu (edgy eft) 6.1 oct 2006.
Does anyone know if later version of Ubuntu has fixed this?

---

### Post by confused57 on 2008-04-13
> **jh1000 said:**
> I did a workaround. I put ubuntu drive as cable select master HDD-0 and moved windows drive to cable select slave HDD-1. They both boot fine.
I still think there is bug in boot sequence of Ubuntu. I don't think it is grub. I think ubuntu's boot sequence reverts to the master no matter what the BIOS tells it. 
The version I'm using is ubuntu (edgy eft) 6.1 oct 2006.
Does anyone know if later version of Ubuntu has fixed this?
I believe you'll be fine with later versions of Ubuntu...if I remember correctly Edgy 6.10 uses root=/dev/xxx, instead of root=UUID=xxxxx in the grub boot kernel line.  This is one advantage to using UUID's, instead of /dev/xxx, if you decide to switch the location of a hard drive.

---

### Post by jh1000 on 2008-04-17
> **confused57 said:**
> I believe you'll be fine with later versions of Ubuntu...if I remember correctly Edgy 6.10 uses root=/dev/xxx, instead of root=UUID=xxxxx in the grub boot kernel line.  This is one advantage to using UUID's, instead of /dev/xxx, if you decide to switch the location of a hard drive.

Sorry it took so long to get back to thank you but upgrading is a nightmare. 
booting on Live CD generated from 
ubuntu-7.10-desktop-i386.iso
detected my screen resolution as 3680x3050 with 
	HorizSync	30-70
	VertRefresh	50-160
which I don't think is possible with my monitor but it caused a dual image of the desktop one very small on top of a stretched and backwards image of the desktop which I have never seen before. Also the 
safe graphics mode hanged while

running local boot scripts
and <Ctrl><Alt>F2 did not work

After tinkering all I had to do was under 
   preferences | screen resolution 
change it to 1024x768 and it seems to work, but I don't know 
what other surprises are waiting. 
I might stick with 6.10 since 8 is already in beta and then switch to 8.
But I won't be able to test confused57 hypothesis and see if 8 will boot as HDD-1.

Edgy 6.10 does use root=/dev/xxx

---

