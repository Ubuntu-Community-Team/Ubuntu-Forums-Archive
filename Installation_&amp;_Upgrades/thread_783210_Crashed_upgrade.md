---
title: "Crashed upgrade"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by fm1234 on 2008-05-05
Hi,
I upgraded from 7.10 to 8.04 but the process got an error while doing something with pida (upgrading?). Some problem with a file descriptor. I don't have the details because the upgrade window said he was trying to recover and then it totally died before I could copy the errors.

Anyway, I ended-up removing the pida package and do a dpkg --configure -a which got me a few new updates and that was it.

The system is working AFAICS except for the login window which displays only the the top-left quadrant, just enough to see the login box.

So, 1) how can I fix the login screen? and 2) is there a way to check what is missing to finish from the installation process and restart it?

TIA

---

### Post by fm1234 on 2008-05-06
I solved it and in case this can be useful for someone else:

> So, 1) how can I fix the login screen?

the solution is here: [http://ubuntuforums.org/showthread.php?p=4892692#post4892692](http://ubuntuforums.org/showthread.php?p=4892692#post4892692)
Either remove Virtual option from xorg.conf or run

sudo dpkg-reconfigure xserver-xorg

> 2) is there a way to check what is missing to finish from the installation process and restart it?

sudo apt-get dist-upgrade

seems to do the job. In addition, in synaptic, you can remove packages which are "Not installed (residual config)" as explained here: [http://www.berthon.eu/wiki/foss:ubuntu:aptclean](http://www.berthon.eu/wiki/foss:ubuntu:aptclean)

---

