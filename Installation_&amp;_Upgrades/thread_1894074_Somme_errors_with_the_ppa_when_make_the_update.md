---
title: "Somme errors with the ppa when make the update"
date: 2011-12-11
forum: Installation &amp; Upgrades
---

### Post by Bruno81 on 2011-12-11
Hi.

When I make the sudo apt-getupdateI receive some errors:

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources    
  404  Not Found

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources    
  404  Not Found


W: Impossibile recuperare [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

Andafter said that is impossibletodownload some index files: they'll be ignored or will be usedoldfilesinstead

What canI do?

Tnx so much for the answers!!!!!!!!!!

Best Regards.

---

### Post by oldos2er on 2011-12-11
> **Bruno81 said:**
> 
W: Impossibile recuperare [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found


Neither of those PPAs have a repository for Oneiric, so I'd remove them from your sources.

---

