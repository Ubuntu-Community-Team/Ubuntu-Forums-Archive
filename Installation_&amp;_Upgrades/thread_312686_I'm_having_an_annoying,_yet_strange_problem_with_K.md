---
title: "I'm having an annoying, yet strange problem with Kubuntu and my pc..."
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by softdel on 2006-12-04
Hello :)

I have been using Kubuntu for a while now, and I decided earlier today to install it on my main pc. 

I had just installed Kubuntu on another PC and it went perfectly...
...But, about half an hour ago I tried to install it on my main PC and it wasn't so smooth.

The CDR booted fine and I selected Start/ Install from the menu...when I did this it showed the loading kernel...and then it just went blank before the X server (and KDE) had started...so I couldn't get to the installer link on the desktop. I could here the disk spinning for some time, and the monitor still had signal...but it just isn't working for me...](*,) 

So I was wondering if anyone had any ideas?

Here are my PC specs:
CPU: AMD Athlon 64 X2 4600+
RAM: 2GB DDR2 533MHz
GFX: 256Mb Nvidia Ge-force 7600GT- PCI-E
VDU: Digimate 19" LCD @ 1280x1024 60Hz

Trying to install Kubuntu 6.10



Any help is urgently needed and i will be very grateful.

---

### Post by Delta_Farce on 2006-12-04
I had a similar issue on my Athlon system with Edgy. I'm not sure what the cause is, but I got around it by using the alternate install cd.

I also had an issue (once installed) where I had a black screen for 2-3 minutes before the x session started. I fixed this by adding the line vga=789 to my kernel string in grub's menu.lst.

My system runs an ATI X800, so this may have been the cause of the problems. I've also got a widescreen LCD which may have contributed. Have a try with the alternate install cd though as that runs the older install program (ie no x session).

Cheers,

Mark

---

### Post by softdel on 2006-12-05
Ok, thanks. I will have a go :)

---

