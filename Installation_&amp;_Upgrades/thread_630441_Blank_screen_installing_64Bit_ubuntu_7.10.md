---
title: "Blank screen installing 64Bit ubuntu 7.10"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by steverido on 2007-12-03
Hi,

I am trying to Dual boot with Vista. I have downloaded and burnt the 7.10 64 bit to disc and done all the usual to boot from CD.

I get the ubuntu splash screen with options. I have tried installing with the first two options and my screen is always blank. I read the second option worked if ubuntu did not register the graphics card. The disc is being read so it is doing something.

I have not installed this before and wanted to explore to see if I liked it enough to make this my main operating system.

Your help would be much appreciated:lolflag:

---

### Post by elliotjreed on 2007-12-03
I had the same!

Are you using an ATI Radeon X1300? I am!

In the end, I had to use the digital cable to my monitor for the live CD, and then the analoge when installed!

Mine worked fine once I had installed the fglrx driver!

No idea why it did it in the first place though, sorry!

---

### Post by spoddles on 2007-12-03
I've had a similar problem with 64bit and an 8800GTX... at the first menu I edited the boot command and changed "splash" to "nosplash"...after installation I edited the /boot/grub/menu.lst and changed it there too, then did a grub-install. Might help...

---

