---
title: "Same package in multiple repositories"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by hokiejp on 2011-03-03
I have several repositories set up in APT, including the Wine PPA (provides new stable builds of wine as well as some related packages).  Recently, the Wine repository started serving their own version of the ia32-libs package.  They update it very frequently, and I'm tired of pulling an extra 50MB every time I get upgrades.

I know I could pin the package version to the current one, but I'd like to still receive any updates that might come through the official Ubuntu channel.  Is there a way to tell apt to only fetch a package from one repository and ignore any others that might offer the same one?

---

