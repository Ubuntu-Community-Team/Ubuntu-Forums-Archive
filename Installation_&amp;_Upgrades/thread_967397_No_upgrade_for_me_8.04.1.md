---
title: "No upgrade for me? 8.04.1"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by awacs on 2008-11-02
I have several Ubuntu servers running 8.04.1. 

Some will present an upgrade to 8.10 by apt-get install update-manager-core and do-release-upgrade. 

Some report, 'no new release found.' all have internet connectivity.

Any idea why?

---

### Post by awacs on 2008-11-02
i got it. some machines have prompt=normal, some have prompt=lts in /etc/update-manager/release-upgrades.

---

