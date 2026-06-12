---
title: "Tiny A440 USB drive boot grub"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by essexboyracer on 2007-09-18
Hi all, looked at the similar threads on this forum, but no joy,

I have an old (circa 2000) Tiny Computers A440 laptop PIII which I would like to be able to boot from a USB key/flash/pendrive/whatever. There are as I see it two avenues to follow;

1. Upgrade the BIOS to enable USB booting
2. Hack GRUB to boot from a USB device

This is where I am at:

1. Tiny computers went bust about 5/6 years ago. As far as I can tell they are FIC.com.tw based but cant find/fathom the correct bios upgrade and I am not going to risk it. A no go for me. Some say that the PHOENIX bios incorrectly reports a USB device as a HD, but no.
2. Seems to be the only option, but I haven't found a decent HOWTO. Has anyone had any joy in achieving this? I really want the ability to try/test/use various distros via a USB key, so much more convienient than CD-ROM, plus there is an opp to save configs

oli

---

### Post by Pumalite on 2007-09-18
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by yabbadabbadont on 2007-09-18
> **Pumalite said:**
> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

If his machine could boot from USB, then I doubt that he would have started this thread....  ;)

---

### Post by kerry_s on 2007-09-18
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

[http://www.osloader.com/](http://www.osloader.com/)

google is your ticket.

---

### Post by Pumalite on 2007-09-18
I stand corrected.

---

### Post by essexboyracer on 2007-09-19
Thanks for your replies, pendrivelinux was the last thing I tried, under the false hope that the bios reports a usb flash device as a HD, but no (great tutorial for slax though). Off to google...

---

### Post by essexboyracer on 2007-09-19
I have an idea, see if GRUB can 'see' the USB device by using find from the GRUB command line, get the path for the device if it does, then add the entry into menu.1st

Also this tutorial [http://www.damnsmalllinux.org/f/topic-3-17-18236-0.html](http://www.damnsmalllinux.org/f/topic-3-17-18236-0.html)

I have also seen references to fromhd or fromusb, but this may be particular to knoppix based DSL

This is good, but seems to only work with DSL
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=17;t=18236;st=0](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=17;t=18236;st=0)

---

### Post by essexboyracer on 2007-09-19
ok, ok. I tried this:

1. DSL on USB
2. copied linux24 & minirt24.gz to FAT32 partition E:
3. Rebooted, press 'c' for command line in grub
4. Type root (hd0,5) - I think it was??!!
5. Type kernel /grub/linux24
6. Type initrd /grub/minirt24.gz

DSL started but then stopped saying no USB devices or knoppix files found. SO i am guessing i got the root bit correct, and the other two as they were loading the kernel off of the FAT32 partition. The only thing is missing is the USB device as it couldnt find any knoppix files.

---

### Post by essexboyracer on 2007-09-20
Has no-one else had this problem? Anyway in my strive to get an old laptop with no USB boot option in the BIOS available, I have come across a couple of interesting threads on puppylinux and backtrack 2.

[http://www.murga-linux.com/puppy/viewtopic.php?t=7979](http://www.murga-linux.com/puppy/viewtopic.php?t=7979)

The above link is to puppy linux and for booting from USB

[http://forums.remote-exploit.org/showthread.php?t=7512](http://forums.remote-exploit.org/showthread.php?t=7512)

This link is for installing Backtrack from a device booted from usb

Can any clever chap (or chapess) shed some light for me on whats going on with what they describe?

---

### Post by essexboyracer on 2007-09-20
Heres another take:

Use GRUB to boot a busybox installation that is on a hard drive partition somewhere, then use busybox to boot another kernel (the one on my USB stick, preferaly a ubuntu one (or slackware based: read slax)). From reading ubuntu community docs somewhere it sounds like kboot has this

---

