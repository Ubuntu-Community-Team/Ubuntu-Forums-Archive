---
title: "RC Live CD does not boot. What to try next?"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheFinePrint on 2008-10-25
I have a desktop machine that I used to have Debian Etch 64bit on, however I would like to change it to Ubuntu so that the differences between the machines I manage is less.

The Alpha-6 32bit Live CD works OK, however I can't get any of the 64-bit images to work on it.  At latest I tried the 64bit RC Live CD, which when done with the boot splash image only blinks underscore.  Ctrl+Alt+F2 does nothing.  Ctrl+Alt+Backspace does nothing.

Hardware:
MB: ASRock AliveXFire
CPU: AMD Athlon 64 X2 4000+
RAM: 2GB DDR2
Graphics: Galaxy GeForce PCI-E 7200GS 128MB

In the end I would like to install from the alternate disc, as it is the only that allows for WDE.

The alternate disc RC-64 (as well as earlier versions) has the following errors:
Softreset failed (device not read) and
end request: I/O error dev sr0 sector 1428224
Buffer I/O error on device sr0

Error messages are repeated over and over.

When done setting the system up and installing the base system I get the following warning:  Debootstrap warning.
File (....)/zlib1g_1.2.3.3.dfsg-12ubuntu1_amd64.deb was corrupt.

I always get this message with 8.10 alternate, although which exact package varies with which version I try to install from.

I then get stuck in an eternal loop where the install failes, and I go back.

Some advice on how to proceed would be very welcome.

---

