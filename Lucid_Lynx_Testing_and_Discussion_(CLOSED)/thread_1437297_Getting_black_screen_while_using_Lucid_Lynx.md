---
title: "Getting black screen while using Lucid Lynx"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jpmutanguha on 2010-03-23
I just installed the beta version, i previously had Ubuntu 9.10 but i didn't like it because it didn't work well with my graphics card. Lucid seems to have still the same problem at that. but i have another new problem, whenever i opened like 3 or 4 things taking up the memory or slowing down the computer the computer hangs and then brings a blank black screen. I'm then left with no choice but to force shutdown.

The bug report says something about apport-gpu-error-intel.py crashing, could anyone help me? can't find any thread related to this.

---

### Post by bodhi.zazen on 2010-03-23
Moved to the Lucid Testing Forums.

As you know, lucid is still in Beta.

---

### Post by jpmutanguha on 2010-03-23
ok, but still no reply? am i the only one experiencing this problem???

---

### Post by Didius Falco on 2010-03-23
I found two bug reports on Launchpad:

This one is a few days older, but worth the read, as it explains what is really causing the problem:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/530650](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/530650)

This one is a newer one that you may want to subscribe to:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/539533](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/539533)

You may want to make sure you have all the current updates - I've had quite a few today. That may cure the problem. If not, see the abovebug reports:

It's not a fix, but it's the best I could find...I hope it helps.

Regards,

Didius

---

### Post by bodhi.zazen on 2010-03-23
Well, as it is a beta I would file a bug report. Be sure to include details on your hardware and (xorg) logs.

---

