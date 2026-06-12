---
title: "Update Manager want to UPGRADE Apache2, but it isn't installed?"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by Bluebellmaniac on 2007-12-03
Hi,

I do not have Apache2 installed, but Update Manager is wanting to install (upgrade actually) apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 php5 php5-common and php5-mysq. It looks like the pho5* stuff are dependencies that apache2* needs. I uninstalled apache2 (and apache) by running 'sudo apt-get remove apache2' and similarly for apache. 

I get the following message when I try to remove apache2:

me-and-my-system$ sudo apt-get remove apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package apache2 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

But when I run:

me-and-my-system$ sudo apt-get dselect-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  apache2-mpm-prefork apache2-utils apache2.2-common language-pack-gnome-en libapache2-mod-php5 php5 php5-common
  php5-mysql
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 5319kB of archives.
After unpacking 1253kB of additional disk space will be used.
Do you want to continue [Y/n]?                  

Why is it trying to "upgrade" something that isn't installed? 

I am running Feisty btw.

Thanks in advance!    :confused:

---

