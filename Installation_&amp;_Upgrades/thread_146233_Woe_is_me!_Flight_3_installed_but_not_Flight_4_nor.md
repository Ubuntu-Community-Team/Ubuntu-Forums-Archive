---
title: "Woe is me! Flight 3 installed but not Flight 4 nor Flight 5."
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by balaram on 2006-03-17
I successfully installed Dapper Drake Flight 3 a few weeks ago; except that I had to switch to console on the first boot up and edit the xorg.conf file to use the 'vesa' driver, but with that Ubuntu booted and all was graphically well.
    I'm using a Biostar Tforce 6100 mobo with Nvidia Geforce 6100 Integrated Graphics; AMD Sempron 3000 64-bit CPU.
     When Flight 4 was released I tried installing it but the installation hung while attempting to install the Xorg files. I checked reported bugs at the time and saw that this problem had been confirmed so I just kept updating Flight 3 and anxiously awaited the next release. 
      I tried installing Flight 5 a couple of days ago and experienced quiet vexation when confronted with the identical result. Woe is me! Anybody know of a work around I might try. Balaram.

---

### Post by m.musashi on 2006-03-18
With install problems, one of the first things to rule out is the possibility of a bad CD. It is recommended that you burn it SLOW (I had one I burned 4x that wouldn't install) and check the md5sum (before you burn). 

If you've ruled that out then the one thing that caught my attention is the chipset. I looked up the board and it has the NVIDIA GeForce 6100 + NF410 chipset. I had BIG problems with a similar chipset (6150/430) on an Asus board. I returned it and bought an MSI board with the 6100/410 chipset. It has been better but not perfect. It might be worth doing a bit of research to see if others have had problems with your board. For example, [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=63670) seems to be related to problems with this board.

Anyway, just a thought.

---

