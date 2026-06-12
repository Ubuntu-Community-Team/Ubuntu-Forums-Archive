---
title: "Upgrade to 8.04, nvidia video problems"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by falkaholic on 2008-04-22
Did an upgrade to the 8.04 LTS.

I have a Nvidia 8600gt with a dual acer AL1916w monitors.

The big hickup would be getting my video working again. Booting gets me to the default video mode. 

Reseting the Xorg.conf and adding and and removing the restricted drivers seems to get it out. It ends up using the nv drivers instead of the nvidia it used before.

The problem is that I can't get it into anything but cloned mode, not twinview etc.

The nvidia-settings wants me to run the nvidia-xconfig, when i do that, I'm back to square one.

Any ideas?

---

### Post by frodon on 2008-04-22
The folowing might help :
[http://ubuntuforums.org/showpost.php?p=4733244&postcount=6](http://ubuntuforums.org/showpost.php?p=4733244&postcount=6)

---

### Post by falkaholic on 2008-04-23
Thanks for the pointer.

Doesnt seem to do that job for me.


Just today, a bunch of updates came down the pipe (99 in fact) and one of them was teh hardware detection software. After rebooting, it got me back into non-safe mode video. Its a step up, but my twist is I have dual monitors, and it never detects the second monitor.

---

