---
title: "Apt-get is broken"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Paralab on 2009-11-15
Hello,

I followed this guide: [http://ubuntuforums.org/archive/index.php/t-20342.html](http://ubuntuforums.org/archive/index.php/t-20342.html)

Which the commands were:

dpkg-divert --local --rename /usr/lib/apt/methods/http
echo '#!/bin/sh' > /usr/lib/apt/methods/http
echo '/usr/bin/trickle -s -d 25 /usr/lib/apt/methods/http.distrib' >>  usr/lib/apt/methods/http
chmod 755 /usr/lib/apt/methods/http

However it was not what I was after so I followed the commands to remove it which were:

rm /usr/lib/apt/methods/http
dpkg-divert --local --remove /usr/lib/apt/methods/http

This does not remove it and my apt-get is broken:

root@ubuntu:~# apt-get install irssi
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  irssi-scripts
The following NEW packages will be installed:
  irssi
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
E: The method driver /usr/lib/apt/methods/http could not be found.

I am running Ubuntu 9.10.

Many thanks. ;)

---

### Post by Paralab on 2009-11-15
Should I reinstall Ubuntu perhaps?

---

### Post by wilee-nilee on 2009-11-15
> **Paralab said:**
> Should I reinstall Ubuntu perhaps?
This can probably be fixed, but if you have everything backed, and want to just get back to a working system you could reinstall. Unfortunately I can't help you with this. I am not sure what this script did or does.

---

