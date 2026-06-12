---
title: "Kernel upgrade, restricted modules and ATI drivers!!"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by adam.tropics on 2005-11-26
Well they say it comes in threes!

Anyway, was doing a fresh install from cd, which installed i386 kernel, so once configured atheros wireless (iwconfig......) upgraded to i686 kernel. At this point I was told of kernel update, which I accepted also. 1hour. 3 kernels, oh well! Anyway, I need to install fglrx drivers, and am fine with that bit, but wish to compile madwifi from source so i can ditch the restricted modules.

All goes well  (sharutils first, then madwifi) untill 'make' on the madwifi at which point it seems to complete but along the way i get errors such as:

 > Warning: could not find /usr/src/madwifi/ath_hal/.hal.o.cmd for /usr/src/madwifi /ath_hal/hal.o
*** Warning: "ieee80211_iterate_nodes" [/usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko] undefined!
*** Warning: "ether_sprintf" [/usr/src/madwifi/ath_rate/sample/ath_rate_sample.ko] undefined!

Anyone have any ideas, even if I then do the make install, it seems to do it, but then nothing, presumably due to these missing files etc???

---

