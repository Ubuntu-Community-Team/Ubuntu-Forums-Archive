---
title: "USB and video problems with 3.13 kernel."
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by marek_online on 2014-04-22
I upgraded my desktop machine from 13.10 to 14.04 over the weekend. It's a [HP P7-1040UK]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02918113&tmp_track_link=ot_faqs/top_issues/en_ie/c02918113/loc:1&cc=ie&dlc=en&lc=en&product=5142074"). 

I'm stuck using an old 3.8 kernel because the 3.13 stock kernel with Trusty Tahr leaves me with failsafe-only graphics and one set of working USB ports. 

Of two sets of USB ports on the device (front and back) only one set works (those on the front of the machine). The graphics issue is clearly present from the boot splash image, so it doesn't seem to be an issue with X specifically.

I've only access to a wireless net connection, which doesn't work with the 3.13 kernel either.

So aside from it being very clear that there are significant driver issues, I'm not sure where to even start trying to get the more up-to-date kernel working.  I'd appreciate any pointers on how to begin!

---

### Post by marek_online on 2014-04-23
The latest kernel updates, which came through yesterday, have resolved the issue. Though it also seemed to help to install linux-image-extra for the kernel version.

---

