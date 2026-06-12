---
title: "Random Freezes"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by dumbomustflyy on 2005-07-20
hello, im a noob to linux so bare with me.

ive been trying to use suse but had random freezes with it, so i switched to Ubuntu and now im having the same problem.  With Ubuntu, the first time i installed it and used it, it never froze until i decided to update. i restarted the computer, loaded up Ubuntu and Gaim then it froze. the freezing started alot each time i loaded Gaim, now it just freezes whenever it feels like it, so i dont know whats wrong. i tried searching for Gaim freezes and nothing i read seemed to help. any advice is appreciated..

here are my system specs. 
Ubuntu AMD64 version
AMD64 2800+ (754 socket)
Chaintech nForce3 VNF3-250
Mushkin PC3200 512MB
WesternDigital 80GB WD800JB
Asus Nvidia TI4200 64MB
C-Media CMI8738/C3DX soundcard

my friend mentioned that maybe its the 64bit kernel having issues with the newest version of gaim?

---

### Post by mingus on 2005-07-20
If you have had random freezes, including in SuSE, then it would seem to be very unlikely that GAIM is the problem.  There is a forum for AMD64, take a look there for freeze problems.  Look also for any kernel arguments that may be needed for your machine.

You might also try installing the stock 32bit kernel; you don't have to remove the 64 kernel.  You could then add the stock kernel to your grub menu (/boot/grub/menu.lst) and boot from it to test if the kernel is the problem.

---

