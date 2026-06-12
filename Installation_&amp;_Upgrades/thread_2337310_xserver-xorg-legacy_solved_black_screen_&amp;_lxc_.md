---
title: "xserver-xorg-legacy solved black screen &amp; lxc incompatibility on Xenial"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2016-09-16
Most people won't need this, but:

on 16.04, if you run into strange problems starting X on some hardware or inside lxc,
be aware of xserver-xorg-legacy.  Installing that package installs
a wrapper that lets X run setuid root as in days of yore
(see also /etc/X11/Xwrapper.config ).

It saved me twice this week:
1) when trying to run X with radeon graphics
inside lxc (see script [http://kegel.com/linux/lxc-opengl-demo/install-x.sh.txt](http://kegel.com/linux/lxc-opengl-demo/install-x.sh.txt) )

2) trying to run X using nvidia proprietary drivers 
with an old gtx 750 which had been working great with ubuntu 12.04,
and worked great on clean install with 16.04, but refused to start when
I installed proprietary drivers.  Looking at Xorg.0.log, it seemed it
was having trouble detecting the screen, so I guessed that running X as root would
help, and sure enough, installing xserver-xorg-legacy seemed to help.

---

### Post by mörgæs on 2016-09-17
Thanks for posting.
If you mark the thread 'solved' there is a better chance that people will find it.

---

