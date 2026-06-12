---
title: "Best version to install for current hardware including HD7770 graphics"
date: 2013-03-15
forum: Installation &amp; Upgrades
---

### Post by andy78 on 2013-03-15
Hi I am going to install ubuntu on my pc along side windows 7 this will be a fesh install of both. I recently baught a new graphics card msi HD7770 and hardrive for my aging pc. The spec is AMD athlon 64 x 2 6000+ 2gigs of dual channel ram. Which version of ubuntu should I install for maximum compatablity. I herd there was some problems with ATI graphics cards and should I install the 64bit version of ubuntu?

---

### Post by Mark Phelps on 2013-03-15
32-bit or 64-bit -- the choice is yours.  Despite what some folks may say, in my own experience testing this directly, 64-bit is no faster than 32-bit.  What is DOES do is allow you to use a lot more system memory -- but with only 2GB of RAM, you won't gain anything using 64-bit over 32-bit.  Oh, and BTW, if you choose 32-bit now, you will NOT be able to upgrade later -- it will require a re-install to do the switch.

While the HD7x series is supported in Ubuntu 12.10, it seems that lots of folks are having problems with the AMD restricted drivers and 12.10.  The open-source Radeon drivers get better all the time, so unless you really NEED restricted driver support, I would install 12.10 and use the default Radeon drivers.

---

### Post by andy78 on 2013-03-15
What is the difference between the restricted drivers and default? Why would you need them?

---

### Post by andy78 on 2013-03-18
ended up being really slow with the default drivers, so installed the restricted drivers, this caused even more problems and I lost unity menu bar etc.. ended up having to uninstall all the drivers and install the amd beta 13.2 drivers now its working well, fast and smooth with nice effects. Lot of hassle though, almost gave up and went back to windows.

---

### Post by darkod on 2013-03-18
It's too late now, but you could have used 12.04.2 LTS instead of 12.10. It's LTS with much longer support and I assume the packages/software is better supported too.

Most often activating the fglrx from Additional Drivers is enough for ATI cards but you always have the option to install the latest driver from AMD/ATI directly, at least they are making good linux drivers. You do the same on windows if you want latest functionality.

Not sure if you want some special effects or how you use the PC, fglrx is enough for my general usage desktop. I would seriously consider using only LTS versions though especially if you don't want doing clean installs often.

---

### Post by Ximaceo on 2013-03-18
Hello andy78,

There are two versions of Ubuntu,
- LTS (Long Term Support) If you are looking for a stable and solid operative system.
- Non-LTS will provide newer packages which have improved features, perhaps at the cost of stability.

I'm gamer ("understand" you too) and Ubuntu's user from 1 month ago, I have used 12.04.2 LTS and 12.10 both 32-bit/64-bit and I recommend you to use 12.10 32-bit, newer is better.
64-bit instruccions are longer than 32-bit, so 64-bits system are slower. You need 64-bit for +4GB RAM systems.

Propietary display driver are faster but they aren't open-souce. I recommend you to use the latest stable video driver to have the best performance, now AMD Catalyst 13.1

---

