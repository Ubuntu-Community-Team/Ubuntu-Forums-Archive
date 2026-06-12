---
title: "Could not initialize the package information"
date: 2011-07-27
forum: Installation &amp; Upgrades
---

### Post by dmaris on 2011-07-27
Ubuntu 11.04
Dell Inspiron 1210 (Mini)

Cannot applay any new updates for 2-3 months.  I get the following error:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by Rubi1200 on 2011-07-28
Hi and welcome to the forums :)

Open a terminal with Ctrl+Alt+T and copy and paste the following commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes any corrupted package lists, the second one updates them.

---

