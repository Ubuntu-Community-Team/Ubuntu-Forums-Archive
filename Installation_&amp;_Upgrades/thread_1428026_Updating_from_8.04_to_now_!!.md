---
title: "Updating from 8.04 to now !!"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by bouzzi on 2010-03-12
Hello,

I was wondering ... Is there was a way to update from 8.04 directly to the current version without going through all the others (8.10, 9.04, etc..)?

or ...

Will it be easier with the next LTS (10.04)?

about this ....!

Will it be possible to migrate directly from 8.04 to 10.04, one LTS to another?

Bouzzi

---

### Post by slakkie on 2010-03-12
Wait for the end of April (29th iirc), LTS to LTS is supported, which will make sure you can upgrade from 8.04 to 10.04 directly, not having to install all intermediate releases.

---

### Post by tommcd on 2010-03-12
> **bouzzi said:**
> 
 Is there was a way to update from 8.04 directly to the current version without going through all the others (8.10, 9.04, etc..)?

No. It is recommended to upgrade in sequence, i.e., from 8.04 > 8.10 > 9.04 > 9.10. This is the only method that is supported. Skipping versions with dist-upgrades is not recommended:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)
> **bouzzi said:**
> 
Will it be easier with the next LTS (10.04)?

Probably, if you want to go the dist-upgrade route. I always do clean installs myself.
> **bouzzi said:**
> 
Will it be possible to migrate directly from 8.04 to 10.04, one LTS to another?

Probably. It was possible to dist-upgrade from 6.06 LTS to 8.04 LTS. Upgrading from 8.04 LTS to 10.04 LTS should also be supported.

---

