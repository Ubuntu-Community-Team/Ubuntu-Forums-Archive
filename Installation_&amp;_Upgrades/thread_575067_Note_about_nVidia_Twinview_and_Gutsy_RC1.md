---
title: "Note about nVidia Twinview and Gutsy RC1"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by vek on 2007-10-13
Yesterday I tried installing the new RC1 (from scratch, blank partitions, cuz I figured thats the best way to have it 100% work the first time, right?)  
I managed to get the system into an unusable state within 5 minutes of starting.  Here are my steps

1.  Install
2.  Reboot
3.  Update everything
4.  Enable restricted drivers (nvidia)
4.  reboot
5. Use the display config manager to enable the second screen

At this point, the entire thing was completely unusable and would go into an infinite loop of restarting, and then the greeter app crashing.  (I think that might be fixed by now, but regardless...)  The infinite unusable loop persisted across reboots.

Of course, I'm not a naive desktop user, so I simply dropped to text mode and restored an earlier copy of my xorg.conf.  However, we can't really expect all users to be able to do this.  If X doesn't start, the system is essentially 'unusable'.

**So here's a note to all you folks trying to get your dual screens or laptop screens working with nvidia cards.**

1.  Enable the restricted drivers
2.  Reboot
3.  gksudo nvidia-settings
4.  Set things up as you want using that control panel instead

**Do not use** the display config manager!  It will NOT work correctly for you, and you may very well end up with a broken X.

---

### Post by Pumalite on 2007-10-13
You probably have one of the newer Nvidia Cards. ??

---

### Post by vek on 2007-10-13
No, its about 2 years old.  Geforce 7800

---

### Post by Pumalite on 2007-10-13
Well, I installed Gutsy RC in a system with an Nvidia 7800 GT yesterday and everything came out working out of the box, including restricted drivers.

---

