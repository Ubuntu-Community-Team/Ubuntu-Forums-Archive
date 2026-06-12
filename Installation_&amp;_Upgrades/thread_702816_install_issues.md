---
title: "install issues"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by jasonk on 2008-02-20
hi,
i have an issue with install of gutsy.  i'm running an asus p5l-MX board and an ati x1600 video card.  when i've tried to boot off the live cd to install it starts up, but then the display dies every time. i  can hear the startup music, but the screen says nothing is plugged in.  so i tried the alternate install cd, on that one, it won't find my network card.  i ended up using the onboard video card and the live cd, and everything installed ok, but then when i went back to my ati it starts to load then hangs on checking for local install scripts (/etc/rc.local) or something like that and won't finish booting.  can someone please help me.  i'm getting really frustrated!
thanks

---

### Post by miriad on 2008-02-20
Have you tried installing the fglrx driver from ATI?
The one in the repositories is outdated, but would probably help your situation, but not allow compiz for compositing (Visual effects).

The newer one from ATI allows the use of Compiz.

---

### Post by jasonk on 2008-02-24
i don't know how to install it when my computer wont boot up

---

### Post by miriad on 2008-02-24
Ok, a few questions:

Does the Live CD boot using VGA (Safe graphics) mode with the ATI card?

What type of network card is it?

---

### Post by jasonk on 2008-02-25
no, the live cd will not boot with graphics.  i can hear it do the bootup sounds, but there is no display.  the network card is a built in attansic L1 Gigabit card.  i had gutsy installed before with all of this hardware, but when i installed last time, i had a different video card, then changed it later.

---

