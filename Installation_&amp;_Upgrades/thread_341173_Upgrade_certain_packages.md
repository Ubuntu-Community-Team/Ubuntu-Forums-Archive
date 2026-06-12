---
title: "Upgrade certain packages"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by endfx on 2007-01-18
I've run "apt-get -s -u" to get a list of packages that needs to be upgraded.

Now I only want to upgrade one of those packages, how do I do this?
I've tried "apt-get upgrade packageName" but it still tries to upgrade all of the packages.

Is it possible to only upgrade 1 package at a time?

Thanks

---

### Post by darkmaster on 2008-01-22
> **endfx said:**
> I've run "apt-get -s -u" to get a list of packages that needs to be upgraded.

Now I only want to upgrade one of those packages, how do I do this?
I've tried "apt-get upgrade packageName" but it still tries to upgrade all of the packages.

Is it possible to only upgrade 1 package at a time?

Thanks

Sure, just

sudo apt-get install package-name

and Package-name will be the only one to be upgraded ;)

---

