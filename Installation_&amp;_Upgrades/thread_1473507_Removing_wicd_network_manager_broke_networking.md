---
title: "Removing wicd network manager broke networking"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by mdittmer on 2010-05-05
I've been using the wicd network manager for some time now, but I recently decided to switch back to the default network manager for Ubuntu's Gnome configuration. To start I used:

$ sudo apt-get remove wicd

Ever since, I can't seem to get my eth0 or wlan0 interface to work. I can't see them in ifconfig, I can't bring them up, nothing. The machine is a Samsung N120 netbook. I'm assuming that somehow network drivers got uninstalled or removed from a list of kernel modules to load, but I don't know how to fix it.

Any thoughts?

EDIT: I'm using Ubuntu 9.10 Karmic

EDIT: SOLVED. Network went into a bad state, but a restart and manual network configuration with /etc/network/interfaces resolved the issue.

---

