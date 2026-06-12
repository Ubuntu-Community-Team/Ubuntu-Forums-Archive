---
title: "Problem instaling Dapper on an old box"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by pillu on 2006-07-21
hi,

I have an old P 2 laptop (Dell Inspiron 7000) with 192 MB ram. I was thinking of installing xubuntu on it. According to the how-tos that I found, I should do a server install and then apt-get xubuntu-desktop. I got an official ubuntu CD for this purpose. Unfortunately that CD is some sort of a live CD and does not directly start the installation on booting from it. Now here is the problem.

When I boot from that CD and select the start or install option, my old guy cannot run the ubuntu live CD. It just stops at the "mounting root file system" option and then gives a DMA timeout error after waiting for a long time. I guess the problem is insufficient memory because the cd needs 256 megs to run. The same thing happens with the safe graphics mode.

Now my question is can I somehow start the install without actually running ubuntu from a live CD and then clicking the install option. I don't really see any way of doing this but if anyone has any ideas plz reply. (The best solution is to probably download and burn the ISO.)

cheers
anand

---

### Post by nalmeth on 2006-07-21
Yep, you got it m8
256megs of RAM recommended for live install. It's suprising that it couldn't even load though, as I've actually installed on a 192meg box before with the liveCD

Download the xubuntu alternate install CD and you should be good.

EDIT: Just re-read, look into boot-options on the liveCD, and enter a boot-option to disable DMA, this is why you can't boot. You must have a pretty old HD or CD-ROM. 

The install will probably still be slow, and may fail anyway

---

