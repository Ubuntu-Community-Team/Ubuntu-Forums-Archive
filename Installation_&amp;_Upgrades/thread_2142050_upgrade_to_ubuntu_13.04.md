---
title: "upgrade to ubuntu 13.04"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by rxlord on 2013-05-04
hey everybody today i started my comouter after a long time and a window popped up saying a upgrade is available to 13.04 i thought i will upgrade later and clicked the cross on top.\
now i want to upgrade to 13.04 and i cant find the upgrade option.
i searced on google and it said open update manager and click the upgrade button.theres no upgrade button in software updater it only has option to update software.
can anybody telll mehow to bring that upgrade window again?

---

### Post by jagojago on 2013-05-04
Hi rxlord

Just try  "update-manager -d" at your terminal (root or sudo)

;-)

---

### Post by Cheesemill on 2013-05-04
> **jagojago said:**
> Hi rxlord

Just try  "update-manager -d" at your terminal (root or sudo)

;-)

You shouldn't use the -d if you want to upgrade to 13.04.

The -d is used for upgrading to the latest development release which is currently 13.10, this should only be attempted if you have the time and knowledge to report bugs and fix your machine when 13.10 breaks (which it will).

---

### Post by rxlord on 2013-05-04
so how to bring that upgrade window back?

---

### Post by Cheesemill on 2013-05-04
Just do...
```
update-manager
```

---

### Post by rxlord on 2013-05-04
but there is no option to upgrade in update manager.Theres only regular updates for packages.
upgrade button is missing

---

### Post by Cheesemill on 2013-05-04
If that's not working you can do the upgrade from the terminal instead with the command...
```
sudo do-release-upgrade
```

---

