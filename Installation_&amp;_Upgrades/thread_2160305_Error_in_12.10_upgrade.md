---
title: "Error in 12.10 upgrade"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by ravimandal on 2013-07-06
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_quantal_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.

---

### Post by fantab on 2013-07-06
From Terminal run the following:
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

