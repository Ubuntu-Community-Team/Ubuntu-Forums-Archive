---
title: "Warning message"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by gman2004 on 2005-10-01
I tryed to add applications and I got the following message:
The following problems were found in your system:
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages)
 Any idea what is it?

---

### Post by aysiu on 2005-10-01
[QUOTE=gman2004]
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages[/QUOTE] Sounds as if you have duplicate entries. Check your /etc/apt/sources.list to see where the duplicate is and remove it.

---

