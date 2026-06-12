---
title: "netboot installs failing with updates today?"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by stump138 on 2008-07-16
I'm getting failures over network unattended installs today with the error:


linux-headers-generic: Depends: linux-headers-2.6.24-19-generic but it is not going to be installed 


I've tried using both my apt-cacher and the regular repos and I get this error either way.  It began with the kernel-header updates that rolled out this morning.
I also tried using the netboot images in the main and proposed branches, so I'm guessing a package got busted yesterday.

Anyone else getting this one?

---

