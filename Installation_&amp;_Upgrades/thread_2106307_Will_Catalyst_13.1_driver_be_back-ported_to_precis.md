---
title: "Will Catalyst 13.1 driver be back-ported to precise 12.04?"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by fig_wright on 2013-01-18
The Catalyst 13.1 drivers are out. This is a major release, with official support for Ubuntu 12.10. Does anyone know if they will be back- ported to Ubuntu 12.4?

PS I know the driver binary can be installed manually, but I want to avoid that.

---

### Post by fig_wright on 2013-01-19
Does anyone at least know when this driver will be issued as the "updates" driver for Ubuntu 12.10?

---

### Post by Mark Phelps on 2013-01-19
> **fig_wright said:**
> The Catalyst 13.1 drivers are out. This is a major release, with official support for Ubuntu 12.10. Does anyone know if they will be back- ported to Ubuntu 12.4?

PS I know the driver binary can be installed manually, but I want to avoid that.

Don't KNOW, but it's unlikely. The newer drivers required X-server v1.13 -- and Ubuntu 12.04 uses X-server v1.12 -- and AMD already announced this last summer that they were dropping retricted driver support for the HD 2x/3x/4x series for future drivers.  It's very unlikely that they will spend the time to reverse this position to make the new drivers work with the older cards (and X-server version).

---

### Post by ttoine on 2013-01-21
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

The new AMD driver is already available for 12.04 with all the x-org dependencies.

---

### Post by fig_wright on 2013-01-25
Awesome - great reply :popcorn:

---

### Post by fig_wright on 2013-01-25
Link for doing the above:
[http://www.kubuntuforums.net/showthread.php?56790-HOW-TO-Install-experimental-X-Org-and-the-latest-graphics-drivers&](http://www.kubuntuforums.net/showthread.php?56790-HOW-TO-Install-experimental-X-Org-and-the-latest-graphics-drivers&)

Looks experimental. Caution:

> “xorg crack pushers” team Packages for those who think development versions, experimental and unstable are for old ladies. We want our crack straight from upstream git! Well, straight, we want it built and packaged so we don't need to know what we're doing, except that we will break our X and put our computers on fire.

LOL.

---

