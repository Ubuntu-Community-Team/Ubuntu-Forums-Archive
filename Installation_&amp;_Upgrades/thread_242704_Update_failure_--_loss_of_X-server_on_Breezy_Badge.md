---
title: "Update failure -- loss of X-server on Breezy Badger 5.10"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by nobar on 2006-08-24
The Ubuntu.com main page currently has an "IMPORTANT NOTICE" that the update process for 6.06 was recently broken and that recently updated systems may fail to start the X server (graphical interface).

I have observed this problem on 5.10 -- and it is not yet fixed.  Also, the solution presented for 6.06 does not quite work.  Instead of installing "xserver-xorg-core" I had to install "xserver-xorg" to resolve my problem.

```
$ sudo apt-get install xserver-xorg
$ sudo /etc/init.d/gdm restart

```

BTW: My system is the VMware "Browser Appliance" provided for use with the free VMware Player.  It is possible that my problem was somehow related to that specific configuration.

---

