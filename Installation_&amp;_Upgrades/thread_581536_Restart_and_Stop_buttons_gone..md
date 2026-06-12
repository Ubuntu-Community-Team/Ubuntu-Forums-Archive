---
title: "Restart and Stop buttons gone."
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2007-10-19
I installed Ubuntu 7.10 on a new created partition, then I installed a bunch of Gnome themes, icon themes, KDE libraries and programs, a bunch of applets, and customized my environment as I always do: a kicker (KDE panel) set to 'tiny' running on top of a gnome-panel, gives me a dual-row panel that can use applets and system menus from both desktops.

I also installed the nVidia proprietary driver in order to get my multimonitor setup to work properly (no Compiz effects is the price to pay for multimonitor, apparently)
2 video cards (nVidia 9750GT), one with two monitors attached, and the other one with one monitor, all independently configured and with xinerama enabled.
This had worked perfectly on my previous 64bit OS (Ubuntu 7.04)

The problem is that in the shutdown interface the Stop and Reboot buttons are missing, and I don't even remember if they diappeared after installing something 8and what) or if it's been this way right from the start.

I "solved" this with a simple workaround: I made two custom panel launchers that run the commands ```
gksu halt
```and```
gksu reboot
``` for shutdown and reboot respectively, but I would still like to get the original shut down and reboot buttons back in place. I guess it must be some daemon that doesn't start, now the problem is: what daemon is not starting? Doest it crash, or not start at all? Why?  (and once found out, of course, I'll ask about how to fix it)

---

### Post by Luke771 on 2007-10-20
The answer was in this thread.

[http://ubuntuforums.org/showthread.php?t=199647](http://ubuntuforums.org/showthread.php?t=199647)

The funny thing is that I started that thread too!
The very same thing had happened before and I didn't remember the solution [it was a DUH-problem in the first place]

---

