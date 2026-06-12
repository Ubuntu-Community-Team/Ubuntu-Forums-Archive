---
title: "plymouth-theme-ubuntu-logo error"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by sm30 on 2016-10-02
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

Every time I upgrade or install, I get the following error.

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libpango1.0-0 libpangox-1.0-0 linux-headers-4.4.0-21
  linux-headers-4.4.0-21-generic linux-image-4.4.0-21-generic
  linux-image-extra-4.4.0-21-generic linux-signed-image-4.4.0-21-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/22.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
dpkg: error processing package plymouth-theme-ubuntu-logo (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
Errors were encountered while processing:
 plymouth-theme-ubuntu-logo
E: Sub-process /usr/bin/dpkg returned an error code (1)

What is a safe way of solving this?  Thanks

---

