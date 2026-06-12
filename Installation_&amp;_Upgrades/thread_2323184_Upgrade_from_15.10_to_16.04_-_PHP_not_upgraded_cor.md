---
title: "Upgrade from 15.10 to 16.04 - PHP not upgraded correctly"
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by Tom_C on 2016-05-03
It seems in the upgrade from 15.10 to 16.04, PHP5 was not fully removed before PHP7 was installed.
I tried sudo apt-get -f install and get
The following additional packages will be installed:
  pkg-php-tools
Suggested packages:
  dh-make
The following packages will be REMOVED:
  libapache2-mod-php5
The following packages will be upgraded:
  pkg-php-tools
1 upgraded, 0 newly installed, 1 to remove and 58 not upgraded.
15 not fully installed or removed.
Need to get 0 B/38.2 kB of archives.
After this operation, 10.2 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 560010 files and directories currently installed.)
Removing libapache2-mod-php5 (5.6.11+dfsg-1ubuntu3.2) ...
ERROR: Module php5 does not exist!
dpkg: error processing package libapache2-mod-php5 (--remove):
 subprocess installed pre-removal script returned error exit status 1
Errors were encountered while processing:
 libapache2-mod-php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt autoremove gives me
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libapache2-mod-php5 : Depends: php5-cli but it is not installable
 pkg-php-tools : Depends: php5-cli (>= 5.3) but it is not installable
E: Unmet dependencies. Try using -f.



What can I do to get my php working again?

---

