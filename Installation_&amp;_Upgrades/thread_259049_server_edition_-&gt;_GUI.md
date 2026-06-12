---
title: "server edition -&gt; GUI"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by xolot1 on 2006-09-16
the question: how to add a GUI to the server edition of ubuntu.

background:
i picked up an old optiplex out of someones trash to use as a fileserver.  it had only 64mb ram, so i used the server edition of ubuntu to install, and added nfs-common and open-ssh to round out the box. i found some more ram, and am trying to give it a GUI - im thinking fvwm, cause its really lightweight, and i now still have only like 192mb ram. what steps must i now take to get a GUI working?  i tried earlier today apt-getting gdm and fvwm, but that was not working at all, and i was unsure of what other dependencies i might need.

listing major packages will probably be sufficient (ie, gdm, fvwm, xserver-****, etc).

thanks!

---

### Post by bernied on 2006-09-16
I'm not familiar with fvwm but it looks like a window manager (like gdm or kdm), not a desktop environment. Why not just install xubuntu-desktop, that should sort out all your dependencies, XFCE is the desktop and gets good reviews for being lightweight and running on low-spec systems.
So the only package would be:
xubuntu-desktop

---

