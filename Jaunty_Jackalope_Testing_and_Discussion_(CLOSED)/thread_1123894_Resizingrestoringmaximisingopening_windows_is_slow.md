---
title: "Resizing/restoring/maximising/opening windows is slow in Compiz (Metacity is fine)"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tom66 on 2009-04-12
Reported as a bug already.

However I would like to know if it is simply a configuration issue on my side. I am running 9.04 beta (and enjoying it) with proprietary fglrx drivers, and resizing/restoring/maximising/opening (anything which involves changing window geometry) takes about 1-2 seconds to take effect. This bug did not exist in Intrepid, so I'm wondering what might be wrong. See signature for details on laptop spec. Metacity is not affected, only compiz. Switching windows is not a problem unless windows are minimised in which case it takes a moment. During the "pause" the mouse works but almost everything else stops working.

---

### Post by deathsshadow77 on 2009-04-12
exactly the same issue here, hoping it gets fixed by the final release

---

### Post by tommysl on 2009-04-14
Got the exact same problem. I'm on a Lenovo T400 with ATI3450 using fglrx drivers. It worked flawlessly in 8.10.

On the plus side, everything else works fine.

---

### Post by uBeer on 2009-04-14
There are some other threads about this, it's an Ati related problem, so I hope that we get a final release of the 9.04 fglrx drivers in the final release of Jaunty. The Windows 9.04 drivers are already out, so it shouldn't be too late (except that there ain't much time for extended testing...).

We'll see, hope it get's fixed soon!

---

### Post by INTERPEGASUS on 2009-04-20
I have a sony vaio with an ATI card and the following actions are very slow ( 1-3 seconds or more):
- Maximizing Windows
- Restoring Windows
- Opening Windows


Is there a a way of fixing this issue or improving the speed?

Thanks in advance!:)

---

### Post by Nirgalksi on 2009-04-20
Same here, Sony vaio also, ATI proprietary drivers

I had the same thing a couple of months ago on intrepid when using kde experimental packages from launchpad, it went out when I stopped using it (Im using only gnome, it was for application like amarok, digikam...).
I tried to change almost every compiz option without luck, must be general with compiz (nad maybe something with kde package from my previous experience

---

### Post by scradock on 2009-04-20
I don't know if my experience with an older ATI card might help:

I have an HP Pavilion with ATI Radeon Xpress 200M video. Everything worked fine in Intrepid, but once Jaunty arrived I was getting faulty screen-redraws in Wine if Compiz or compositing metacity were used (metacity without compositing worked fine).

Turned out that for my card, the new default of UXA acceleration is not supported, so the (open source) driver defaulted to EXA. All it took was to manually set Option  "AccelMethod"  "XAA" in the Devices section of xorg.conf, and full compatibility between Compiz and other programs was restored.

---

### Post by tom66 on 2009-04-21
I tried the fix mentioned, it seemed to make no difference.

---

### Post by cemc on 2009-04-22
Just wanted to add a 'me too' on this topic. I have a HP Compaq 8510p, with Radeon Mobility HD 2600, and after upgrading to Jaunty (yesterday), I noticed some slowness when maximizing xterm.
Turns out if Compiz is enabled, window maximization/restore/resize is a bit sluggish. The moment I click the maximize button, it just freezes for like a second and the CPU goes 100%. Ran top, and Xorg grabs the CPU.

With Compiz disabled, the problem goes away.

tom66, you said you opened a bugreport on this, can you tell us the bug number, so we can add something to it, make it more 'urgent'?

Thanks.

---

