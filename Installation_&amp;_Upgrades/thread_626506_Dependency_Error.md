---
title: "Dependency Error"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by santhosh23 on 2007-11-29
I am using ubuntu 7.10 and installed realplayer,during the installing it asked me to remove kdelibs-data which was a part of k3b installation...so i removed it and then installed realplayer went ok. However after the installation when i tried to install any package it throwed me error..so i went to synaptic and it said that i had broken jobs therefore i completely uninstalled the broken packages which were kdelibs-data and then tried to reinstall k3b i got an error "Unpacking kdelibs-data (from .../kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/mimelnk/application/vnd.rn-realmedia.desktop', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.8-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



so i tried "apt-get install -f" still no go and i also tried "apt-get get remove to check it there were any broken jobs and there isn't any.


Please advice me on how can i fix this issue.

---

