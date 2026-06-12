---
title: "Offline initiation 2 (keryx)"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by plant pot on 2011-09-27
I am installing Ubuntu on an offline machine (was [http://ubuntuforums.org/showthread.php?t=1847764](http://ubuntuforums.org/showthread.php?t=1847764)).

As expected, I need to get a bunch of extra packages via an online  WinXP machine then transferred to ubuntu via a USB pen. The sane way to get  packages from offline seems to be via keryx. Trouble is that 'normal' keryx is known  to not work with 11.04 (and Keryx's forum seems broken for new  accounts).

I read that the best way to use Keryx with 11.04 is to use the (harder to find) source  version of their latest 1.0 release. But for me: that just gives an  error on a new install of 11.04:

```
root@machine:/media/usb_pen/keryx_1.0-public21_portable/bin# ./keryx.py 
Loading config: /media/usb_pen/keryx_1.0-public21_portable/data/keryx.conf
g_dbus_connection_real_closed: Remote peer vanished with error:  Underlying GIOStream returned 0 bytes on an async read  (g-io-error-quark, 0). Exiting.
Terminated
root@machine:/media/usb_pen/keryx_1.0-public21_portable/bin# 
```

I expected  to have lots of teething troubles and niggles for a while..  But I did  think I would be mostly up and running by now.

I am not a Gnome/GTK/dbus puppy so I don't recognise the error... Any ideas?

---

### Post by plant pot on 2011-09-27
Wha??? Kernel sources not included in the standard install?

I thought something was up when I first noticed Ubuntu's Commodore Amiga styling. I really do think I am probably looking at the wrong Linux distribution.

I guess I can easily replace the window manager and init with something to my taste later. My first and key remaining requirement is an offline install. Your package system looks so nice, if only I could get it to work.

---

### Post by plant pot on 2011-09-28
I got it working eventually.
Since I am a generous sort of chap, I wrote you a mini-guide:

"Keryx v1.0 Ubuntu 11.04 mini-guide --it DOES work"
[http://keryxproject.org/forums/index.php?topic=130&limit=1#p556](http://keryxproject.org/forums/index.php?topic=130&limit=1#p556)

I encourage you to direct lost travellers to it until robust software is available.
--

---

