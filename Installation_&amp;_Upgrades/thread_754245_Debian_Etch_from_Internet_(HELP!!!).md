---
title: "Debian Etch from Internet (HELP!!!)"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Arkaniad on 2008-04-13
OK so here's the deal, i have a Dell Inspiron 7000 that is Maxed out on memory and has a 366 mhz pII.

It cannot boot from my CD/RW's, and i cannot buy a cd/dvd pack at this time

It has a floppy drive

Here is the hitch-

I have a belkin USB wlan adapter, and every time i install ubuntu (regular, any version) it never connects to our router. but, on edubuntu, it somehow works, because i have to enter it at startup. well, now my edubuntu cd wont read the kernel therefore rendering it useless, i have decided to try Debian 4.0.

The netinstall floppies are being loaded as we speak.

but i just need some clarification or other methods.

i have a 1gb flash drive, but the inspiron does not have a usb boot in its bios. I am really itching to get linux on that. and i dont want edubuntu.



Help?

---

### Post by koenn on 2008-04-13
If your pc knows how to boot from a USB stick, you can use that.
[http://www.debian.org/releases/stable/i386/ch04s04.html.en](http://www.debian.org/releases/stable/i386/ch04s04.html.en)
since this uses  floppy disk emulation, maybe it works. 


Also, on the debian install CD, you'll find an 'install' directory with sbm.bin and a readme file. You can use that to create boot floppies that can access your CD-drive. so even if you can't boot from a CD, you can still use the CD as a repo during the install process (so you don't need network access immediately)

I'm not sure all of these boot methods have been taken to Ubunru as well.

---

