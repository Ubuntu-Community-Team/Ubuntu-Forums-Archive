---
title: "Unable to install using CD, USB, or PXE... so what else could I do?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by caseyc585 on 2010-01-02
I have an older dell CSX laptop that I would like to load up with ubuntu or kubuntu... or anything other than XP.  The problem is that the laptop does not have the option to boot from USB, I don't have a CD/Floppy drive to attach to the media bay and I don't have a pcmia that will PXE boot... So, do I have any other options?  I really don't want to go purchase anything for this laptop because it's old, but if I could get it reloaded with anything it would be ok for a netbook... It will boot into XP, but its very sluggish

---

### Post by MelDJ on 2010-01-02
install this [http://www.daemon-tools.cc/eng/downloads](http://www.daemon-tools.cc/eng/downloads)
it can mount .isos
use it to mount the ubuntu .iso and run a wubi install. 
that i am afraid requires leaving windows in the computer as ubuntu is installed in windows but its the only i can think of

---

### Post by jenaniston on 2010-01-02
If it has an ethernet port with internal network card, go into bios to see if laptop supports LAN boot.

You can still boot indirectly an OS (like Ubuntu 9.04) on 1 GB USB stick  - even without bios having USB support  -
 by using a chain bootloader like plop linux.
So before I'll go into any further details, does bios support LAN boot ?

---

### Post by caseyc585 on 2010-01-02
The bios does support LAN boot, however it does not have a internal ethernet port and I don't have PCMIA card that will LAN boot (I only have an older wireless)

---

### Post by jenaniston on 2010-01-02
So laptop supports LAN boot - but how ? . . . only wireless LAN ? (ouch)
From what I know it might still be possible with PLoP Linux chainloader.

[http://www.plop.at/en/ploplinux.html#pxel](http://www.plop.at/en/ploplinux.html#pxel)

If you can boot the ploplinux over LAN - somehow - it will give the choice of where to direct the boot to look for OS system files.
BIOS does not ***have*** to support USB (the choice highlighted in the screenshot below),
 or the USB (with say Ubuntu 9.04) could be lower in boot sequence, after hard drive and boot around it -
 ploplinux has to be first though LAN in your case (or typically CD when available).

Hope this lead helps . . .  Good luck.

[IMG]http://i372.photobucket.com/albums/oo161/sunblush/ploplinuxusb.jpg[/IMG]

---

### Post by Cheesemill on 2010-01-02
If you can get your hands on another laptop you could swap your hard drive into that to run the install, then just put it back into your machine when its done.

It will have to be an older laptop as all new models use SATA drives, you need one that takes PATA drives. If your unsure just take the drives out and look at the pins, they're completely different.

---

