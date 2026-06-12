---
title: "upgrade problem"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by alexscr on 2011-02-12
Hi - I keep getting the following msg as I try to upgrade from 10.04 -> 10.10 ...
"Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report." 

I don't think any of the issues above apply - can anyone offer advice on how to get around or "force " the upgrade please .. alexscr

---

### Post by zvacet on 2011-02-13
In terminal type

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

