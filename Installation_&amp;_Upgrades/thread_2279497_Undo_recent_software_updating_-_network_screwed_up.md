---
title: "Undo recent software updating - network screwed up"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by keergyriah on 2015-05-23
Greetings.

Over the last few days, my internet connection to the router has become really screwed up, taking forever, not connecting, etc.  I made no recent changes and suspect the software updater (updated 2x last 5 days) is to blame.  Right now I'm using "non-free firmware for linux kernel drivers" for my wireless device which could already be kind of sketchy.  But it worked superbly before this.

I followed this post#3 [http://ubuntuforums.org/showthread.php?t=1723348](http://ubuntuforums.org/showthread.php?t=1723348) and I suspect that "2015-05-21 14:13:49 upgrade ubuntu-drivers-common:amd64 1:0.2.91.7 1:0.2.91.9" is my problem.  Can I undo this specific update, or the other ones?

I'm kinda lost how to do other fixes I've found, which may not apply to this. I also don't want to reboot since I've done a bunch of custom settings via compbiz.  Help is much appreciated.

---

### Post by dino99 on 2015-05-24
you can downgrade (package > force version) to 0.2.91.4 ( i'm usually doing it with 'synaptic')
but you can also glance at /var/log/dmesg to get more warnings/errors logged

---

### Post by grahammechanical on 2015-05-24
Additional Drivers sits on top of ubuntu-drivers. On my system ubuntu-drivers has nothing to do with the ethernet or Wifi drivers as they kernel modules. Here are a couple of useful commands relating to ubuntu-drivers.

```
ubuntu-drivers list
ubuntu-drivers devices
```

Is WiFi listed as one of the devices?

Regards.

---

