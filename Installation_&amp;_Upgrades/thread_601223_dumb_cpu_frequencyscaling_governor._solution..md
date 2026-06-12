---
title: "dumb cpu frequency/scaling governor. solution."
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2007-11-03
Installed 7.04 feisty on an old laptop. It has a 1.5Ghz CPU.

the cpu applet kept showing 600Mhz and the sysinfo applet showing little cpu usage. I belived everything was fine. But as soon as i started upgrading to gutsy hell broke loose. The machine simply stops responding. The system applet shows almost no cpu usage, no disk usage, but load rising fast. and cpu always at 600Mhz. the same install procedure on a 700Mhz desktop was alright.

Then i noticed that user load indeed was low, but the system load was almost at 100%... i couldnt see the shade of blue the applet was using...

After a while the load just get to 11+ and i have to do a forced shutdown.

Changing the governor to performance or min_scaling to 15000 solved it.

If you get stuck with wrong scaling, read [http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

saved the day. ...I'm still clueless as to why running at 600mhz locked the system... but it's a korean notebook, branded "COM PAL" which ironically is read in Portuguese as something like "fuxored", so i'm not gona loose my sleep over it.

---

### Post by gcbzzzz on 2007-11-03
ok, now it's locking also @ 1500mhz... only a little later in the upgrade process.

seems like i will loose some sleep.

---

### Post by gcbzzzz on 2007-11-03
seems like it was some bug with the HD controller. 

I did two things to solve this.

1. disabled swap on HD (swapoff -a)
and then created (fdisk ..., mkswap ...) a swap partition on a USB2 drive and enabled it (swapon ...)

2. installed the 386 kernel instead of the generic.

don't know which one solved. I will upgrade to gutsy and see what happens with the gutsy -generic kernel.

---

