---
title: "UPDATE MANAGER is not working"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by anupdada on 2013-07-06
[B]UPDATE MANAGER is not working
...
shows this message...
[/B]
Could not initialize the package information


An unresolvable problem occurred while initializing the package information.


Please report this bug against the 'update-manager' package and include the following error message:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by fantab on 2013-07-06
Try the following:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

