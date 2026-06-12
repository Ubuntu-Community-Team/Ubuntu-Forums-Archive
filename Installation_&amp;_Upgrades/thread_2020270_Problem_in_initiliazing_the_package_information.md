---
title: "Problem in initiliazing the package information"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by supravat on 2012-07-08
Hello every one....I am facing a serious problem in Ubuntu 12.04 Lts. Whenever I am trying to install new package or update the packages I am getting error with the following error message and as a result I am unable to install or update my system.

The error message:
-----------------------------------------------------------------------

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'
-----------------------------------------------------------------------


Please help me whow to resolve the provlem.
Thank you

---

### Post by dino99 on 2012-07-08
"update-manager" what a nightmare, better to use synaptic

sudo rm  /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

):P

---

### Post by supravat on 2012-07-09
Thank you....dino99 ....it worked :)

---

