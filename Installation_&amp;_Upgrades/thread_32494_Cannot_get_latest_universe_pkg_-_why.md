---
title: "Cannot get latest universe pkg - why?"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by sage on 2005-05-08
The universe web site at //archive.ubuntu.com/ubuntu/pool/universe shows the latest abiword pkg as 2.2.7 yet when I use synaptic or apt-get, it tells me I have the latest as 2.2.2 - why ??  How can I apt-get the 2.2.7 pkg with it's new dependencies??   thks.

---

### Post by Fab on 2005-05-08
[QUOTE=sage]The universe web site at //archive.ubuntu.com/ubuntu/pool/universe shows the latest abiword pkg as 2.2.7 yet when I use synaptic or apt-get, it tells me I have the latest as 2.2.2 - why ??  How can I apt-get the 2.2.7 pkg with it's new dependencies??   thks.[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org) -> extra repositories

---

### Post by tonym on 2005-05-08
2.2.2 is the version for hoary.  2.2.7 is in breezy.  Which release are you using?

packages.ubuntu.com is a useful resource for identifying versions of packages.

If you want the latest versions of everything you can change /etc/apt/sources.list to point to breezy but as this is currently the testing version you may find some things broken.

---

### Post by sage on 2005-05-08
I already have universe included and have rechecked it.  There are both 2.2.2 and 2.2.7 pkgs in universe - somehow my apt-getting is only getting the 2.2.2.  

Getting a bug fix should not be this hard - I am not liking this system.

---

