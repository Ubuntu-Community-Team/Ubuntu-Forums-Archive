---
title: "Error During Update: Edgy to Feisty"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by ppatalano on 2007-04-20
When trying to update edgy to feisty, I get this error:

> Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://ubuntu.geole.info/dists/dapper/universe/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/dapper/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu.geole.info/dists/dapper/multiverse/binary-i386/Packages.gz](http://ubuntu.geole.info/dists/dapper/multiverse/binary-i386/Packages.gz) 404 Not Found




---

### Post by gardara on 2007-04-20
got the same error....

Open up terminal and enter

sudo gedit /etc/apt/sources.list

Then find 

deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse
deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) edgy universe multiverse

And change it to

deb [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse
deb-src [http://ubuntu.geole.info/](http://ubuntu.geole.info/) feisty universe multiverse

:)

---

