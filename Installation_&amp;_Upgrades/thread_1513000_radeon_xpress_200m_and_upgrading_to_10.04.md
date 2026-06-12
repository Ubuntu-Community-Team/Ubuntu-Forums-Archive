---
title: "radeon xpress 200m and upgrading to 10.04"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by fontenot_1031 on 2010-06-18
Hi. I'm currently running Intrepid so I could run the proprietary drivers (fglrx drivers) for my video card (radeon xpress 200m) because with the newer release, Jaunty, the xpress 200m card was dropped from support.

However, I've discovered that when watching videos the open source drivers for my card (xserver-xorg-video-ati) work significantly better than the fglrx drivers.

I want to upgrade now 10.04 but I've seen a lot of threads about people having problems with the fglrx drivers. **My main question is has anybody with a radeon xpress 200m card had any problems with 10.04 using the open source drivers?**

---

### Post by ebasa on 2010-06-18
Works just fine here.

---

### Post by JHCKX on 2010-06-20
> **fontenot_1031 said:**
> Hi. I'm currently running Intrepid so I could run the proprietary drivers (fglrx drivers) for my video card (radeon xpress 200m) because with the newer release, Jaunty, the xpress 200m card was dropped from support.

However, I've discovered that when watching videos the open source drivers for my card (xserver-xorg-video-ati) work significantly better than the fglrx drivers.

I want to upgrade now 10.04 but I've seen a lot of threads about people having problems with the fglrx drivers. **My main question is has anybody with a radeon xpress 200m card had any problems with 10.04 using the open source drivers?**

10.04 works but video performance is slower on my machine than using 9.04. See

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/576125)

Suspend and hibernate don't work either, see

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/577340](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/577340)

I have a Packard Bell MZ35 laptop with a radeon xpress 200m video

---

### Post by fuyao on 2010-07-11
i have a thinkpad R51e with this model of video card, did you find anymore info on how to make this card work on 10.04? im having a hellish experience with the drivers right now

and also i discovered that what you installed for video drivers back with this model of video card in 8.04 will work until 9.10, (game performance, movies etc) then everything will go haywire when you upgrade to 10.04

---

