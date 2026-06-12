---
title: "Beryl removed but blocking upgrade to Feisty"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by derbyjon on 2007-06-29
I'm using the GUI update manager to upgrade from Edgy to Feisty. Edgy is currently up to date.

I'm getting the following error:
Failed to fetch [http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/edgy/main-edgy/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]

As I don't use beryl I searched within Synaptic and performed a complete removal of the beryl packages. This didn't change the error. I've also rebooted and am still getting the same error.

Any suggestions welcome.

---

### Post by BlahMan_of.Doom on 2007-06-29
Well all THAT error is saying is that that file is not available on that site. You could install beryl but have it not running, so that it would unblock the upgrade, I assume.

---

### Post by derbyjon on 2007-06-30
I eventually got around the problem by removing Beryl from the repository list.

---

