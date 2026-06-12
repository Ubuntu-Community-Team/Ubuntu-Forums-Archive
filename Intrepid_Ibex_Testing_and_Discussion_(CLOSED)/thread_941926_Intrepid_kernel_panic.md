---
title: "Intrepid kernel panic"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Keithamus on 2008-10-08
I'm running 64bit Intrepid beta 1 - been running since the beta was announced. Everything has been running fine; it ran so well, I even upgraded my girlfriends machine (identical machine to mine - we're both running Lenovo N200 3000 models).

So we did our updates today, and all of a sudden we've been getting kernel panics (I assume they're kernel panics, the whole machine freezes and the caps light flashes). We're both running 2.6.27-6-generic, I tried rolling back to 27-5 but still got panics; I haven't got any earlier kernels on my system (except for 24 from hardy).

Is this a known bug, is there any known hardware to cause problems? Like I said it's been running fine since beta was released, right up until today.

---

### Post by Rocket2DMn on 2008-10-08
Moved to Intrepid Ibex Testing and Discussion.

---

### Post by AlexBellisBrown on 2008-10-08
I had a kernel panic after i upgraded, bearing in mind its a beta... and still under developement, it was a bad move on my part, luckily i had a backup of everything and reinstall of Hardy was easy enough, i tried to find a way to boot back into Ubuntu normally, but couldnt, not even when using previous kernels. Kernel panics (as far as i know) are related to a hardware problem, so i pretty much urge anybody, before they try to upgrade to Interpid, try their system with the Live CD first, to make sure it runs right, failing that, wait until the full release. Hope you find a way to fix it! I couldnt, and just went for the easier reinstall. Good luck though.

---

### Post by jblance on 2008-10-09
I have a similar sounding problem

running Intrepid 64bit on Toshiba Tecra Laptop with Centrino vPro and nVidia video (also Intel gig eth - opps)

was runnning fine, updated yesterday now get kernel panic on boot
latest kernel installed is 2.6.27-6
have tried recovery boot option (and booting older installed kernels)
Depending on which kernel I try to boot (using recovery) get errors:
2.6.27-6: Kernel panic - not syncing: Attempted to kill init!
2.6.27-4: Kernel panic - not syncing: Attempted to kill init!
2.6.24-19:
either: Bad page state in process 'udevd'
or: run_program: '/sbin/modprobe' abnormal exit

Havent got the LiveCD with me at the moment, so booting into that for fsck etc will have to wait until tomorrow.

Any other suggestions??

---

### Post by AlexBellisBrown on 2008-10-09
After having 2 hours trawling the web, i couldnt really find any way of fixing this without a re-install. Plus the error seemed to have corrupted some data on my primary hard drive. Let me know how it goes. :)

---

### Post by Keithamus on 2008-10-09
We both can use our machine, browse the web, do whatever - but we both just get random lockups, sysreq keys don't work and the caps light flashes.

I don't want to submit a bug report because I have no idea what is causing it, is there any way to debug this?

---

### Post by jblance on 2008-10-09
Well upon further investigation I have found that one of my memory modules has gone bad (may explain some earlier issues too -including a few lockups)

Have removed module and am now booting fine.

Suggest you run memtest on your machine to ensure that your memory isn't on its way out

---

### Post by Keithamus on 2008-10-10
I realised today that I bought a new wireless-n router the same day I upgraded both machines. Turns out (as we both have 4965agn wireless cards) that it is an issue with that! Not with Intrepid itself.

For anyone reading this, it is looking to get fixed by the final intrepid. You can read more about it on this bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

---

