---
title: "Upgrading a package without upgrading the whole system"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by giuffsalvo on 2007-11-05
Hi, I noticed that in the repositories for 7.10 there's a newer version of MLDonkey (2.9, if I remember correctly). Now, I have 7.04, and I'm happy with it and don't want to change, at least for a while (I've seen that it has problems in installing VMware Workstation), but in the repos for 7.04 there's still (and I guess it will remain forever) an old version of MLDonkey (2.8). Is there any way to update the package of MLDonkey? What happens if I change the repos in /etc/apt/sources.list, without upgrading the whole system?
Thanks

---

### Post by rsambuca on 2007-11-05
I don't think that changing your sources to the new version is the best idea.  If there is something that you really need in the new version of MLDonkey, I would either find a deb or compile it from source.

---

