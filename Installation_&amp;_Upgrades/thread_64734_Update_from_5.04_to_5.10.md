---
title: "Update from 5.04 to 5.10"
date: 2005-09-11
forum: Installation &amp; Upgrades
---

### Post by woopud on 2005-09-11
What  is the easiest way to update from 5.04 to 5.10 ?

---

### Post by mlomker on 2005-09-12
[QUOTE=woopud]What  is the easiest way to update from 5.04 to 5.10 ?[/QUOTE]

I'd recommend starting with a backup.  Some important things didn't work for me and I've seen a lot of posts that aren't so encouraging.

Other than that you should edit your /etc/apt/sources.list to point to Breezy instead of Hoary.  Then:

Ctrl-F2 over to a text console and login as root.
killall gdm
apt-get update
apt-get dist-upgrade

I ended up trying to upgrade from Synaptic and it went very badly.   ](*,)

---

