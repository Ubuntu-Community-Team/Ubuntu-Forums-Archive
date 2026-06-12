---
title: "Holy crap - Laptop overheated during 8.10 upgrade"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by Jamsi on 2008-11-27
As the title suggests, my laptop seems to have overheated and crashed midway through a 8.10 upgrade. The upgrade had about 30 minutes to go and was in the middle of installing the packages.

Now when the laptop boots I get the famous "kernel panic" error.

When I boot using an earlier kernel, I can get into terminal only (gnome fails) but the system is read only, and therefore cannot get network access (ifup eth0) in order to type "apt-get dist-upgrade" to complete the process.

Any friggen idea's before I throw this thing off a bridge?

Cheers.

---

### Post by cdtech on 2008-11-27
use the "sudo ifup eth0". Did you try the sudo command, should work for ya.

---

### Post by Jamsi on 2008-11-27
Umm ... yes .. I tried that ..

ifup: failed to open statefile /var/run/network/ifstate: no such file or directory

---

### Post by Jamsi on 2008-11-27
whooo .. ended up getting network to work after

/etc/init.d/loopback start

---

