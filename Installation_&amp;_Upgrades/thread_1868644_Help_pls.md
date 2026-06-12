---
title: "Help pls"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by buchi_cent on 2011-10-24
pls help i try running update manager then i got this error message;

                   Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Do anybody know how to fix this error or solution to this error.

---

### Post by zvacet on 2011-10-24
Try with 

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

EDIT Please be more descriptive with next thread title.You will get help sooner.

---

