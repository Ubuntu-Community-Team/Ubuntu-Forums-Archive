---
title: "gdm dependencies and their dependencies"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by TBeholder on 2011-10-22
I recently noticed that gdm package got some interesting dependencies, indirectly:

libimobiledevice2 ("Library for communicating with the iPhone and iPod Touch")
libplist1 ("Library for handling Apple binary and XML property lists")
libusbmuxd1 ("USB multiplexor daemon for iPhone and iPod Touch devices - library")
usbmuxd ("USB multiplexor daemon for iPhone and iPod Touch devices")

Thee are not "recommended" or "suggested", but required - that is, removing any of them would uninstall gdm as well.
Does this grow like kudzu when unchecked?
Or are these really in some roundabout way necessary for **Gnome Display Manager** (now *that*'s a scary thought).

---

