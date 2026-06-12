---
title: "upgrade to 8.10 results in beige screen after login"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by zeppelin222 on 2008-11-01
Hello everyone,

I've been trying to upgrade to Intrepud Ibex from Hardy Heron, and after a long series of different attempts, I am stuck. I first started by using the upgrade manager like it says on the main website, i left, and when i came back my screensaver was on but frozen. i had no choice but to kill the power, so i did, and when i rebooted i would just get errors. so i downloaded a live cd and tried to install it from there... no luck. then i tried reinstalling hardy from a live cd, and i got that going, except w/o an internet connection, and then for no apparent reason when i restarted after setting up my wireless drivers with ndiswrapper, it would not boot again. so i tried the same intrepid live cd that i had before, but this time it worked, and i got the the install to go fine. except when i rebooted after the install, after i log in, i just get that beige screen with a mouse pointer. the pointer responds to mouse movements, but it wont leave that beige screen. i tried the intrepid cd one more again, just for kicks, and now i cant get the installer to load. oy vey...

oh by the way im dualbooting with win xp, and so far it still works.

---

### Post by zeppelin222 on 2008-11-02
well my friend who had the same problem helped me out, idk how he figured it out, but if anyone else is having this problm, try this:

> sudo apt-get remove compiz

sudo apt-get remove compiz-core

you just lose your fancy desktop effects. oh well.

---

