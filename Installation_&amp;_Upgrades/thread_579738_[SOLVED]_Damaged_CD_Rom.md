---
title: "[SOLVED] Damaged CD Rom"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2007-10-18
Ok, this is the problem. It is a very old PC, when I first installed it Xubuntu 7.04, had to do some tricks to achieve it, since everytime I use the CD rom, the computer slows down as if were XP on 64MB of RAM. In short, makes me crawl in despair. Now I've just downloaded the 7.10 Xubuntu and can't run CD.
The last time, what I did was uninstall the HD and put it into a newst PC, Pentium IV, ATI Radeon 7000, 2.02 Processor, 768MB RAM. And installed the OS, when I changed back, had a few problems, the OS learned to "eat caviar" and now was "eating 3rd time fried meat". Had to work a lot to find out how to change from the ATI configuration to "vesa".

The question is: Will it be necessary to do all that again? It is the CD ROM the problem? The Oldie's specs are:
Celeron 700MHz
256MB RAM
8 MB video (shared 32 from RAM, so now it's 40) How ever, it does support and runs Beryl. Check the screen shot:lolflag:

It's an AOPEN Custom PC. 
Please help!!! The sooner I clear this, the sooner I'll be on Gutsy!

---

### Post by logos34 on 2007-10-18
try [this method]("https://help.ubuntu.com/community/Installation/FromLinux") (essentially you copy the CD contents to a holding partition and do the installation from the hard drive without having to boot from CD)

*ignore the first paragraph about unetbootin since you already have the disc

---

### Post by Steveway on 2007-10-18
How about the alternate-cd?
It has a text-based installer, not as userfriendly but needs way less ressources.

---

### Post by arashiko28 on 2007-10-18
> **Steveway said:**
> How about the alternate-cd?
It has a text-based installer, not as userfriendly but needs way less ressources.

It's not about resources, Xubuntu runs like a charm on that Flintstone's PC. The problems is that the CD ROM makes the system to fail everytime I use it, it does not matter if it's a software or a music CD, it just slows down the PC performance to nearly frozen.

---

### Post by arashiko28 on 2007-10-31
Please help here fellas! I can't repartition the disk without deleting the already installed OS, so can't do what you recommend. The gpartitioner warn me when I try to do it.

---

### Post by logos34 on 2007-10-31
Can't you just upgrade over the net?

---

### Post by arashiko28 on 2007-10-31
I could have done it, but I'm on a rant with my internet company, the service has come to merely c*** and it will take a lifetime to do it. I know it's an old PC, but don't have cash to upgrade it, not even to buy a CD rom.

---

### Post by logos34 on 2007-10-31
> **arashiko28 said:**
> I could have done it, but I'm on a rant with my internet company, the service has come to merely c*** and it will take a lifetime to do it.

So you have a slow connection and it would take too long, is that what you mean?

Because that's the only other solution I can think of.  I mean, if this thing slows to a crawl whenever you use the cdrom, it would probably take forever to transfer a cd iso to the machine.  [EDIT:  gparted won't let you shrink a mounted partition--you need to work from the livecd.  So that's out, unless you can use gparted from a usb stick]

Have you checked the settings in the Bios i.e.IDE and DMA?  And is the cdrom on the same cable as the hard drive?  (but even that wouldn't explain such a drastic slowdown)

What about[ installing from usb flash drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")?  Is that an option?

---

### Post by arashiko28 on 2007-11-01
Yeah, that is in short, though I shouldn't. I'll try the USB drive. And no, the cd rom and the hard drive have two separated cables. Thanks, i'll let you know if it goes well.

---

### Post by arashiko28 on 2007-11-05
Problem solved. Got new CD rom. Also, had this awful delay of 5 minutes while booting, it solved as soon as changed the CD rom.

---

