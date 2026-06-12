---
title: "Quick fix for anyone using Linksys WUSB600n or &lt;RT2800 USB Adaptor"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by JBAlaska on 2009-12-17
It seems that Lucid develops a driver conflict with any Ralink chipset below the RT2800. The symptom is, it will detect a wireless network but will fail to connect, or connect intermittently and sux..

This was a bug with Karmic [Link](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/460323) that seems to have carried over to Lucid.

The fix is to blacklist the rt2800usb driver, like so:
```
gksu gedit /etc/modprobe.d/blacklist.conf
``` and add:
```
blacklist rt2800usb
```

Lucid will then use the RT2870STA driver and work perfectly.

Hope this helps my fellow 10.04 testers.

---

### Post by magevideogames on 2010-01-28
Wow this is a great fix.  I was looking around for months now trying to get this to work in karmic and lucid and something so simple fixes it.  Thanks a bunch!  Also, don't forget to restart after applying the change.

---

### Post by ChaosTheRedNose on 2010-02-08
This fix worked great the first time I used it. I recently reinstalled Ubuntu 9.10 and now I can only connect at 54mb. I was previousy connected at 270mb. I am using a WUSB600N v1 connecting to a WRT610N. Have you seen this issue?

---

### Post by nyarnon on 2010-04-23
Doesn't work for the 302 WUSB300N

---

