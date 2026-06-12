---
title: "[SOLVED] Upgraded to 8.10 today and lost GUI"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by potatoehead64 on 2008-10-31
Having upgraded, on reboot I seem to have lost the GUI completely. I'm just getting a log in and password screen in text mode. It logs on ok, but I remain in text mode i.e. just like being presented with root.
I confess to being a bit rash with the various options presented during the upgrade (basically, my wife phoned me whilst I was at work and asked what to accept.... I just chanced it!.) Is the a way to downgrade or install via ISO disk without loosing my files on the partition?

Any have any ideas how to fix?

Marty

---

### Post by Peter09 on 2008-10-31
Once logged in try typing

```
startx
```

see if this brings up a GUI.

From there you should be able to sort out your video driver. See if this works and come back

---

### Post by michiedo on 2008-10-31
the same happened to me.
I solved rebooting in "recovery mode" (or something similar) then when the choice was between "log as root" "continue normal boot" .. ... "try to fix X"  I choose the last, and it automatically fixed my /etc/X11/xorg.conf.

hth

good luck

---

### Post by potatoehead64 on 2008-10-31
> **michiedo said:**
> the same happened to me.
I solved rebooting in "recovery mode" (or something similar) then when the choice was between "log as root" "continue normal boot" .. ... "try to fix X"  I choose the last, and it automatically fixed my /etc/X11/xorg.conf.

hth

good luck

Thanks, this worked!

---

