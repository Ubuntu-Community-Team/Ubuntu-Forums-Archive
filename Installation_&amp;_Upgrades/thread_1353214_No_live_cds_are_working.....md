---
title: "No live cds are working...."
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by GamesForLinux on 2009-12-12
I'm trying to install Ubuntu on a friends laptop. The cd will boot and allow me to choose 'Try without changing' then shows the scrolling screens of terminal information, shows the pulsing Ubuntu logo, more scrolling screens of terminal, and the screen goes black. This appears to be where x would normally load the login screen. We've tried the wubi installer, and it downloads and installs, but doesn't get past the pulsing Ubuntu logo.
In fact, we've tried Fedora 12, Puppy, Mandriva, and Gentoo, and none of them will load a gui, even though Gentoo has a graphical boot screen, and Ubuntu has a logo.

All of the cd's we've booted from work perfectly in multiple other computers, and they do boot, so it's not an issue of setting the BIOS to boot from a cd.

The only thing I can think of would be a hardware issue. The computer specs are as follows:

Toshiba Satellite A3565-S6935 laptop
Intel Core 2 Duo T6400 2.0Ghz cpu
ATI Mobility Radeon HD 3650 Video card
4 GB ram
WAN miniport l2tp
Realtech HD Audio

I've had the same problem on a different computer, which was a HP desktop that I don't remember the specs on.
Any help would be greatly appreciated. Thanks!

---

### Post by khelben1979 on 2009-12-12
Are you trying the latest versions?

---

### Post by darkod on 2009-12-12
> **GamesForLinux said:**
> I'm trying to install Ubuntu on a friends laptop. The cd will boot and allow me to choose 'Try without changing' then shows the scrolling screens of terminal information, shows the pulsing Ubuntu logo, more scrolling screens of terminal, and the screen goes black. This appears to be where x would normally load the login screen. We've tried the wubi installer, and it downloads and installs, but doesn't get past the pulsing Ubuntu logo.
In fact, we've tried Fedora 12, Puppy, Mandriva, and Gentoo, and none of them will load a gui, even though Gentoo has a graphical boot screen, and Ubuntu has a logo.

All of the cd's we've booted from work perfectly in multiple other computers, and they do boot, so it's not an issue of setting the BIOS to boot from a cd.

The only thing I can think of would be a hardware issue. The computer specs are as follows:

Toshiba Satellite A3565-S6935 laptop
Intel Core 2 Duo T6400 2.0Ghz cpu
ATI Mobility Radeon HD 3650 Video card
4 GB ram
WAN miniport l2tp
Realtech HD Audio

I've had the same problem on a different computer, which was a HP desktop that I don't remember the specs on.
Any help would be greatly appreciated. Thanks!

It might be a video driver problem but I don't know how to solve it for the Try Ubuntu option. It was doing something similar to my desktop with integrated HD3200, restarting it just before the login screen.
But if I selected Install Ubuntu option, the process will finish successfully (in my case) and then on first boot I just installed video driver using the recovery mode boot option.
It might work for you too, but if you first want to use the Try option, don't know how to do that.

---

### Post by GamesForLinux on 2009-12-12
> **darkod said:**
> It might be a video driver problem but I don't know how to solve it for the Try Ubuntu option. It was doing something similar to my desktop with integrated HD3200, restarting it just before the login screen.
But if I selected Install Ubuntu option, the process will finish successfully (in my case) and then on first boot I just installed video driver using the recovery mode boot option.
It might work for you too, but if you first want to use the Try option, don't know how to do that.

Alright, I can try this but... the wubi installer did the exact same thing. Would doing a recovery boot option and installing drivers on it work as well? I'd rather play with the virtual partition before messing with the real one.

---

### Post by darkod on 2009-12-12
> **GamesForLinux said:**
> Alright, I can try this but... the wubi installer did the exact same thing. Would doing a recovery boot option and installing drivers on it work as well? I'd rather play with the virtual partition before messing with the real one.

Not sure. Personally I find it easier to toubleshoot "real" ubuntu than wubi. Wubi is working inside windows in sort of virtual way and you never know what to expect. I'm staying away from it so can't really give advice on it.

---

### Post by lisati on 2009-12-12
Could be something about the Toshiba hardware. I currently use 9.04 on a Toshiba M200 laptop, no major hassles, but when I tried a Live USB with it, it didn't play nice. It was as if the default display settings didn't suit or something of that nature. The same USB worked on my desktop (managed to get to the Live session GUI, but other things didn't play so nice.)

---

