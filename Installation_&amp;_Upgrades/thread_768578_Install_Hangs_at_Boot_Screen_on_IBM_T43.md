---
title: "Install Hangs at Boot Screen on IBM T43"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by NickFormerlyKnownAsPrince on 2008-04-26
Hey, I used to use Ubuntu back around version 6 somewhere and am looking to get back into day-to-day use, but I'm having a serious issue when trying to install with the new Hardy Heron, though I haven't tried any other versions.

Right now, whenever I boot from the CD, I get to Try/Install/Check CD/etc. pre-boot environment, and I can edit the boot parameters, but any time I select any of the options, the unit just hangs. I tried changing over to an external CD drive, same thing.

So what's going on? I did install a new HDD before any of this, and I'm setting up Windows on it now, so I know it's not the drive. What should I do to get the install running smoothly?

---

### Post by schloss on 2008-04-26
I have a similar problem (except my machine is a T41). I wiped the hard drive so I could do a fresh install, no problem. Unfortunately, whenever I attempt to install, I either get the repeated "/dev/fd0 not found" error (the machine has no floppy drive) -- which using the floppy=no switch *does not solve* -- or the system hangs while on the splash screen, sometimes blinking the caps lock indicator. Any advice?

---

### Post by schloss on 2008-04-26
Solved my problem. The key (pun intended?) is to use a thumbdrive to install instead of the CD. Instructions are here (works from Windows, they don't have instructions up yet on how to make a Hardy installer from Ubuntu):

[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

---

