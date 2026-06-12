---
title: "i reinstalled ubuntu and i have a problem"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by nonarky on 2005-10-24
now when i try to install a program i always get this 

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

and when i run that apt-get updatecommand i still get this 

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

do you know whats wrong?

---

### Post by mlomker on 2005-10-24
Mirrormax was shut down...remove them from Synaptic or your /etc/apt/sources.list.

---

