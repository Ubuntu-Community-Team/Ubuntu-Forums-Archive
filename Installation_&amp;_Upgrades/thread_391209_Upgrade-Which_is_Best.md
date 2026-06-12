---
title: "Upgrade-Which is Best"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2007-03-22
Is there a difference in a cd or dvd upgrade and using the terminal?
If so, which is better?

---

### Post by Kateikyoushi on 2007-03-22
[QUOTE=AZ]Update from alternate cd

WHen you upgrade from the cd, you will only be upgrading the packages that are part of the base install. So pretty much anything that is not from the main repository will not be upgraded (because it is not there).

That means that those packages will either
1. Continue to work fine. This is the case if they do not depend on any specific version of the core packages.
2. Be removed by the package manager. This is the case if they depend on a specific version of a package that is going to be removed or upgraded.
3. Stay installed but not work anymore. This can be the case if your software was installed "by hand" without using the package manager, or if it was installed by the package manager, but the package is not properly built ( this can be the case with many third-part applications)
[/QUOTE]

So you might be better off with the dvd than the cd because it has more packages but in the end the net wins.

---

