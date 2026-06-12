---
title: "an extra 2 gigs"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by tikal26 on 2006-06-03
:rolleyes:  When I upgrade to Dapper I ended up using 2Gigs extras. I use to mage 6.4 gigs and now I have 8.64 gigs. How do I free some of that space up.

---

### Post by tikal26 on 2006-06-03
anyone? :confused:

---

### Post by Hezekiah on 2006-06-03
It may be apt caching the debs needed for the upgrade.  You can check in /var/cache/apt/ which is where the cached files are stored.  Synaptic has an option somewhere toclear the cache.

---

### Post by meng on 2006-06-03
sudo apt-get clean

from man apt-get:
clean clears out the local repository of retrieved package files

---

### Post by rcarring on 2006-06-04
You can also dump cache debs from the Preferences menu in synaptic.

---

