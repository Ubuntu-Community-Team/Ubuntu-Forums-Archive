---
title: "gnome screensaver's gone missing"
date: 2006-10-24
forum: Installation &amp; Upgrades
---

### Post by linuxgrrl on 2006-10-24
I just upgraded to Dapper from Breezy and followed the instructions in the Sticky thread about disabling the screensaver before doing the upgrade.

The problem is, now that I've booted into Dapper the screensaver  item is completely missing from the gnome config menu.  Maybe this is my fault ... when disabling it, I saw an option for "stop daemon" and I clicked it.  I thought it would start up again after a reboot?

Any rate, how do I get the screensaver config menu back?  I don't want the menus burned into my television :)
thanks,
Mary

---

### Post by funkyade on 2006-10-24
```
~> sudo aptitude reinstall xscreensaver xscreensaver-data gnome-screensaver
```

then go to preferences and have a fiddle with it!

hth

---

### Post by linuxgrrl on 2006-10-25
thank you! :)

---

