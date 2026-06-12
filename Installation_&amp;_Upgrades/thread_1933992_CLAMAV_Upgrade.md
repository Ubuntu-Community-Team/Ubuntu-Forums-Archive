---
title: "CLAMAV Upgrade"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by jogor10 on 2012-03-01
Although I am regularing running the Update Manager, when I go to use CLAMAV, it seems to tell me that the anti-virus software is outdated and the GUI has an update but there doesnt seem to be a link to update it..  I ran apt-cache search clamav and then tried to run apt-get clamav.  On the "get" piece,I got invalid operation clamav.  Can anyone help with some direction?  much appreciated
Jo

---

### Post by Lasall on 2012-03-01
Hi jogor10,

check clamav-FAQ at [http://wiki.clamav.net/bin/view/Main/FAQ](http://wiki.clamav.net/bin/view/Main/FAQ).


Kind regards

Lasall

---

### Post by ottosykora on 2012-03-01
clamav, the engine, is in repositories, it will almost all time report then as being out dated, but do not worry about that, this is quite normal with clamav.

Clamtk id the gui, this one can also be updated from repository , but will then often be reported as outdated. Also here no big problem, it is rather normal.
But clamtk can be updated by downloading the .deb file from the site:

[http://sourceforge.net/projects/clamtk/files/ClamTk/4.37/clamtk_4.37-1_all.deb/download](http://sourceforge.net/projects/clamtk/files/ClamTk/4.37/clamtk_4.37-1_all.deb/download)

---

### Post by jogor10 on 2012-03-01
thanks--- good link

---

### Post by jogor10 on 2012-03-01
thanks-- very helpful FAQ for clamav

---

