---
title: "Install AD Plugin Centrify fails all of a sudden."
date: 2013-06-27
forum: Installation &amp; Upgrades
---

### Post by mrstaun on 2013-06-27
Used to install the AD plugin from Centrify like this.

apt-get install centrifydc

But today when trying it fails with the error :

```
[EMAIL="root@srv-fog-ds1"]root@srv-fog-ds1[/EMAIL]:~# apt-get install centrifydc
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package centrifydc
[EMAIL="root@srv-fog-ds1"]root@srv-fog-ds1[/EMAIL]:~#
```

Anyone have the same issue or seen this?

---

### Post by dino99 on 2013-06-27
The latest was available for Lucid, then removed from the ubuntu archive
[https://launchpad.net/ubuntu/+source/centrifydc](https://launchpad.net/ubuntu/+source/centrifydc)

---

### Post by t-readyroc on 2013-06-27
Thanks for the info.  Just ran into this myself.

---

### Post by unixisfun on 2013-06-27
> **t-readyroc said:**
> Thanks for the info.  Just ran into this myself.

As they were issues in packaging, the latest version of Centrify DirectControl 5.1 has been removed from the repository. Centrify is actively working with vendor to fix this issue. Your patience and understanding is appreciated. More details can be found at [http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Broken-new-centrifydc-package-for-ubuntu-12-04-LTS/m-p/12202#M2652](http://community.centrify.com/t5/DirectControl-Express-for-UNIX/Broken-new-centrifydc-package-for-ubuntu-12-04-LTS/m-p/12202#M2652)

---

### Post by mrstaun on 2013-06-28
Thanks, adding the 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
to /etc/apt/sources.list.d/centrify.list 

made my day. We really depend on the package.

---

