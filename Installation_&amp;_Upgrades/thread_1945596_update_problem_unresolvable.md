---
title: "update problem? unresolvable"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by hrock on 2012-03-23
on starting up date manager i get this mesage 

"An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing mozilla-openthesaurus-de (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.' "

its the same with synaplic 

a nice simple easy solution would be good. 

thank you 

hrock

---

### Post by hrock on 2012-03-23
well when copped and pasted here the simile's come out of the wood work.

---

### Post by Bucky Ball on 2012-03-23
Have you got them both open at the same time??? If so, close one and try again.

Which Ubuntu release are you using?

---

### Post by plucky on 2012-03-23
> **hrock said:**
> on starting up date manager i get this mesage 

"An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing mozilla-openthesaurus-de (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.' "

its the same with synaplic 

a nice simple easy solution would be good. 

thank you 

hrock


Open a terminal and run ```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
``` and see if that fixes it.

Good Luck

---

### Post by hrock on 2012-03-24
well it would seem that update manager had crashed so was sort of still running and it did the same thing after the first restart but after the 2nd one it did not start and when i started it every thing seems fine. 

thanks for the help its the first time in 3 years ubuntu has come close to not sorting its self out on its own

---

