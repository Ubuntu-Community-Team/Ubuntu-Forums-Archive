---
title: "Package manger problem"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by Maxiejoe on 2013-03-03
When I try to run package manager the message appears.    An resolvable problem occurred while initializing the package information.  'e:Encountered a section with no Package:header, E problem with Mergelist/var/lib/apt/lists/security.ubuntu.com_ubuntu_dist_precise-security_multiverse_multiverse_binary-1386_packages, E: The package lists or status file could not be parsed or opened.'

I am using 10.04 ubuntu

Also the ununtu software center will not open.   Thanks  for any help.

---

### Post by plucky on 2013-03-04
> **Maxiejoe said:**
> When I try to run package manager the message appears.    An resolvable problem occurred while initializing the package information.  'e:Encountered a section with no Package:header, E problem with Mergelist/var/lib/apt/lists/security.ubuntu.com_ubuntu_dist_precise-security_multiverse_multiverse_binary-1386_packages, E: The package lists or status file could not be parsed or opened.'

I am using 10.04 ubuntu

Also the ununtu software center will not open.   Thanks  for any help.

Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` to delete all the list files and then run ```
sudo apt-get update
``` to reload the list files.

Good Luck

---

### Post by Maxiejoe on 2013-03-04
> **plucky said:**
> Open a terminal and run ```
sudo rm /var/lib/apt/lists/* -vf
``` to delete all the list files and then run ```
sudo apt-get update
``` to reload the list files.

Good Luck

Thanks alot,  it did work and is now running fine......Problem solved

---

