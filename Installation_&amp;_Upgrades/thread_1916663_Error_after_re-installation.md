---
title: "Error after re-installation"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2012-01-28
I did a clean re-install. When I do an update I get the following:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E38FDEE72D75E850

The solution was:

sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com  E38FDEE72D75E850

---

