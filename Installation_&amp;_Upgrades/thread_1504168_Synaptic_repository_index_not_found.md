---
title: "Synaptic repository index not found"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by amalgamas on 2010-06-07
Ubuntu 10.04: I get the following error in Synaptic: "Could not download all repository indexes"  "Could not get [http://ppa.launchpad.net/berndth/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/berndth/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found" (translated from Norwegian).

"http://ppa.launchpad.net/berndth/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz" does not exist, but it does for Karmic (change lucid for karmic in the url).  How do I correct this in Synaptic?

---

### Post by SlidingHorn on 2010-06-07
Take a look [here]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Add_Repositories_using_Synaptic_Package_Manager").  Find the repository that it's trying to pull from, copy that line, and below it, paste with karmic in place of lucid.

---

### Post by amalgamas on 2010-06-07
Many thanks!  It did the trick.  :)

---

