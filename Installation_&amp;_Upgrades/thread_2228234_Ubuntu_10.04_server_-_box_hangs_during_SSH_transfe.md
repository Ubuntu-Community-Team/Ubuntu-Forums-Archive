---
title: "Ubuntu 10.04 server - box hangs during SSH transfers (latest SSL update?)"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by granric on 2014-06-06
In addition to [http://ubuntuforums.org/showthread.php?t=2228174](http://ubuntuforums.org/showthread.php?t=2228174) and [http://ubuntuforums.org/showthread.php?t=2228206](http://ubuntuforums.org/showthread.php?t=2228206), I've found another major annoyance related to today's update: when I SSH to my box to transfer files (on the other end of the wire I've a win server running the latest WinSCP), the Ubuntu box suddenly freezes after a few MB transfer (black screen, unresponsive to keyboard & mouse).

The only differences on this side were introduced by today's update, namely: 

```
Upgraded the following packages:
libssl0.9.8 (0.9.8k-7ubuntu8.15) to 0.9.8k-7ubuntu8.18
linux-generic (2.6.32.60.67) to 2.6.32.61.68
linux-headers-generic (2.6.32.60.67) to 2.6.32.61.68
linux-headers-server (2.6.32.60.67) to 2.6.32.61.68
linux-image-generic (2.6.32.60.67) to 2.6.32.61.68
linux-image-server (2.6.32.60.67) to 2.6.32.61.68
linux-libc-dev (2.6.32-60.122) to 2.6.32-61.124
linux-server (2.6.32.60.67) to 2.6.32.61.68
openssl (0.9.8k-7ubuntu8.15) to 0.9.8k-7ubuntu8.18

```

and, as mentioned elsewhere, I've fallen back to run 2.6.32.60 - I'm evaluating to return to previous version of libssl/openssl, at least to check where stands the issue.

Any alternative hint/workaround is greatly appreciated - if there's any debug I can help with, I'm surely available.
Ric

---

### Post by anthonie on 2014-06-07
Since updating yesterday, I am having problems as well with ssh. I run a remote notification system (ssh -X with notify-send) on my phones and for some reason my dbus sessions are borked now. I have not found a way to get it working, nor have I found an explanation that could shed some light on the problem at hand.

```
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.


** (notify-send:14111): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:14111): CRITICAL **: dbus_g_proxy_connect_signal: assertion `DBUS_IS_G_PROXY (proxy)' failed

** (notify-send:14111): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.

```

Can't help but finding this very annoying...

---

