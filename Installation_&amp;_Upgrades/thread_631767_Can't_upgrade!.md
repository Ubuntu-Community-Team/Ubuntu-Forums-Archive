---
title: "Can't upgrade!"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by ondoin on 2007-12-04
I am trying to upgrade to version 7.04 but after I click upgrade and follow instructions nothing happens!

Also,when I check for updates I get this:

[http://theli.free.fr/packages/dists/edgy/listen/binary-powerpc/Packages.gz:](http://theli.free.fr/packages/dists/edgy/listen/binary-powerpc/Packages.gz:) 301 Moved Permanently
[http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-powerpc/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-powerpc/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-powerpc/Packages.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-powerpc/Packages.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/free/source/Sources.gz:) 404 Not Found
[http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz:](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/source/Sources.gz:) 404 Not Found


Does this have to do with the upgrade problem?
In any case,what should I do?

---

### Post by Pumalite on 2007-12-04
Medibuntu change his repo a long time ago. Comment out (put a # in front) of those lines in your sources list. Also get rid of all third parties and automatix if you have it before an upgrade.

---

### Post by ondoin on 2007-12-08
Hey man, thanks for your advice but I'm a new at Linux, so can you explain what do you mean?

---

### Post by Pumalite on 2007-12-08
sudo cp /etc/apt/sources.list /etc/apt/sources.list.back
gksudo gedit /etc/apt/sources.list
Remove
Add # to the offending lines
Save, exit, reboot
sudo apt-get update
sudo apt-get upgrade

---

### Post by Pumalite on 2007-12-08
Check my editing.

---

