---
title: "E:Encountered a section with no Package: header, E:Problem with MergeList"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by kosalads on 2012-10-08
Guys,
 Let me know why do I get this error and how can I resolve this ?

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by jerrrys on 2012-10-08
In terminal

sudo rm /var/lib/apt/lists/* -vf

sudo apt-get update

---

