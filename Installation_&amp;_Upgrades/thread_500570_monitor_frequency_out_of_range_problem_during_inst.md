---
title: "monitor frequency out of range problem during install with livecd resolved"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by earl.yuen on 2007-07-14
here is my solution:
1, when monitor prmpts "freq. out of range" message, press ctrl-alt-f2, this will bring you to console
2, sudo init 1. this command switch runlevel to single user mode, then the dead xserver session will be killed.
3, edit /etc/X11/xorg.conf, delete display sections with unusual color depth such as 16, 24 and 32 bits, as well as the modes other than "1024x768", "800x600". save the config file
4, startx, after a while the gnome desktop appears.
5, launch install by system->xxxx(i forgot ;-))->install

wish this will help those ever encounterred a similar problem. imho, ubutu installation should give more options.

---

