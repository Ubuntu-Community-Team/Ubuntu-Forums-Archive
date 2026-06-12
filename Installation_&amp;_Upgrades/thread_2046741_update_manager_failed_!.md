---
title: "update manager failed !"
date: 2012-08-23
forum: Installation &amp; Upgrades
---

### Post by KRITI DUDHIYA on 2012-08-23
:( update manager: failed to initialize package information and says-


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by plucky on 2012-08-24
> **KRITI DUDHIYA said:**
> :( update manager: failed to initialize package information and says-


An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Welcome to the forum.

Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -rf
sudo apt-get update
``` should fix your problem.

The first command deletes all the .list files in /var/lib/apt/lists/ directory and the second command reloads them from the repositories.

Good Luck

---

### Post by KRITI DUDHIYA on 2012-08-25
Thanx a lot.. it was very helpful. :)

---

### Post by grahammechanical on 2012-08-25
That is just the command I am looking for. Thank you.

Regards.

---

