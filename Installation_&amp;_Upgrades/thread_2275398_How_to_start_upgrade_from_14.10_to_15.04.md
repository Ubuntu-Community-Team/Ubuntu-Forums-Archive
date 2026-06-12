---
title: "How to start upgrade from 14.10 to 15.04"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by STPitcher on 2015-04-25
Yesterday, the Software Updater offered to upgrade 14.10 to 15.04.  I wasn't ready to do it just then.  Now I'm ready.  But Software Updater is no longer offering the upgrade.

How to I ask it to start the upgrade???

- stp

---

### Post by grahammechanical on 2015-04-25
Have you tried running software updater and telling it to check for updates?

---

### Post by STPitcher on 2015-04-25
It appears to check for updates automatically, every time I start the software updater.  It does report several updates for 14.10.

- stp

---

### Post by sammiev on 2015-04-25
1. Update your software 1st on 14.10

2. Backup all your data.

then update to 15o4

---

### Post by PhilGil on 2015-04-25
> **sammiev said:**
> 1. Update your software 1st on 14.10

2. Backup all your data.

3. Roll back or uninstall any software installed via PPA's then disable or remove the PPA's (either manually or using the ppa-purge tool). Make note of changes so you can reinstall after the upgrade.

> **sammiev said:**
> then update to 15o4

---

### Post by oldos2er on 2015-04-26
> **STPitcher said:**
> How to I ask it to start the upgrade???

- stp

```
do-release-upgrade
```

---

### Post by craig10x on 2015-04-26
By the way, you don't need to uninstall ppas before doing the upgrade, just go to software sources and uncheck them...after upgrading and re-booting to the new version, then you just re-check them again...

---

### Post by STPitcher on 2015-04-26
Thanks.  Mission accomplished.. Once I finished the updates for 14.10, it offered me the 15.04 upgrade.  I was figuring that since the day before it was happy with the condition of my 14.10, that it was still quite sufficient.  But I gather it doesn't bother to look for major upgrades until all the lessor updates are done.

Upgrade went moderately smoothly.  Couple of glitches... I think I still have to work on my flash player.

- stp

---

