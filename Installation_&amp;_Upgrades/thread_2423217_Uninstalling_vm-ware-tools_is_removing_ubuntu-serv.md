---
title: "Uninstalling vm-ware-tools is removing ubuntu-server package as well"
date: 2019-07-19
forum: Installation &amp; Upgrades
---

### Post by mbuzaljko on 2019-07-19
I wanted to remove open-vmware-tools from my Ubuntu 16.04 server and I saw that package ubuntu-server will be removed as well in the process. 

$ sudo apt remove open-vm-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  open-vm-tools [B]ubuntu-server

[/B]Do you have any suggestion how to handle this?

thx

---

### Post by CatKiller on 2019-07-19
There are various metapackages - ubuntu-desktop, ubuntu-server, ubuntu-minimal, and so on - that list the default packages for those setups.

If you remove any of the default packages, then those metapackages necessarily have to be removed as well. They set up the default installation, and you'll no longer have a default installation.

It's not a problem to not have the metapackages installed - they are for convenience - but you might find it useful to reinstall them before you upgrade to the next Ubuntu version: the default installed packages for 18.04 may not be the same as the default installed packages for 16.04, and you don't want to have any missing.

---

