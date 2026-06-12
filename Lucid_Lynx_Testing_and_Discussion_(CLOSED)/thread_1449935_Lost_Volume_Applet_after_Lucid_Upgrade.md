---
title: "Lost Volume Applet after Lucid Upgrade"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Thinkin on 2010-04-08
Seems to be missing from my panel and I cannot figure out how to replace.

---

### Post by komputes on 2010-04-14
This seems to affect upgrades only. I have found another forum thread and a mailing list thread as well as an actual bug that was reported.

Bug:
[https://bugs.launchpad.net/bugs/552221](https://bugs.launchpad.net/bugs/552221)

Forums thread:
[http://ubuntuforums.org/showthread.php?p=9118842](http://ubuntuforums.org/showthread.php?p=9118842)

Mailing list thread:
[http://forum.nginx.org/read.php?26,69797](http://forum.nginx.org/read.php?26,69797)

The workaround for this is to open **System > Preferences > Startup Applications** (if you do not have this, it is most likely another bug - if so, the application will be called **Sessions**)

Add an entry:
Name: Volume control (or whatever you want)
Command: gnome-volume-control-applet
Note: Whatever you want

Then log out and back in and you should now have your volume control back.

---

