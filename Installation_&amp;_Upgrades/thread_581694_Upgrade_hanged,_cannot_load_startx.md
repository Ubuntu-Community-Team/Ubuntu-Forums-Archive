---
title: "Upgrade hanged, cannot load startx"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by eitan_a on 2007-10-19
Hi, tried upgrading to 7.10 today.  The upgrade downloaded all the files okay and was unpacking and installing them.  There were a few packages that couldn't be installed due to some error, but I brushed those away and continued to upgrade.  At this point my system was pretty unusable anyways.  Well the update manager quit at some point.  I had to restart the computer and I tried the new kernel but it gave me a kernel panic.  Okay, so I tried another kernel, an older one, and it failed to load startx but got me to a terminal.  I did a dpkg --configure -a from this terminal and it was working for a little bit but then got an "abort dump" error.  and will not continue.  It is complaining about a lot of dependancy problems.  Well anyways, I am stuck here and cannot boot gutsy in any usable manner.  I am running XP again and require this to be solved.

Thanks.

---

### Post by tjk on 2007-10-19
At the terminal prompt, try running:

sudo apt-get update
sudo apt-get upgrade

Some of the dependencies my be broken because of an incomplete installation and this may solve your problem... it definitely won't hurt your system anymore.

---

### Post by eitan_a on 2007-10-19
I tried these, but it keeps saying i need to do dpkg --configure -a, it won't do anything else..

---

