---
title: "Could not calculate the upgrade"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by doublewitt on 2011-11-27
When running the Update Manager, this is the error message that shows up:


[I][COLOR="Blue"]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'[/COLOR][/I]

Does anyone know what I can do to solve this?
I'm using 10.04 LTS

---

### Post by MAFoElffen on 2011-11-27
> **doublewitt said:**
> When running the Update Manager, this is the error message that shows up:


[I][COLOR=Blue]Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'[/COLOR][/I]

Does anyone know what I can do to solve this?
I'm using 10.04 LTS
May be a broken or orphaned package... Try
```

sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade

```

---

