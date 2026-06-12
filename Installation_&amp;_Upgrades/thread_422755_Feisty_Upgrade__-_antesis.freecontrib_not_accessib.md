---
title: "Feisty Upgrade  - antesis.freecontrib not accessible"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Andy17MB on 2007-04-25
When I try and Upgrade from Edgy To Feisty I get a message back that [http://antesis.freecontrib.org/](http://antesis.freecontrib.org/)... can not be contacted (there seem to be a number of mirrored repositories on it relating to Dapper).  Any suggestions why this ios happening and how I work around it or correct whatever is calling it?

Thanks

---

### Post by dbcummings on 2007-04-25
It appears that your /etc/apt/sources.list file must have a defunct or faulty repository listed.  Make sure you run sudo apt-get update from the terminal before running the upgrade.  What command are you using to run the upgrade?  Is it sudo apt-get dist-upgrade.  Did you update your sources.list file to Feisty before making the upgrade?  I recommend doing a clean install for Feisty.  Backup your data, wipe the drive and perform a clean installation.

---

