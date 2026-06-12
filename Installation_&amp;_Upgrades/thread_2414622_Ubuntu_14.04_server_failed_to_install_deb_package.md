---
title: "Ubuntu 14.04 server failed to install deb package"
date: 2019-03-12
forum: Installation &amp; Upgrades
---

### Post by aalg on 2019-03-12
Dear all:
I have a machine, which can not access the internet, running ubuntu 14.04 server.
When i try to install packages&#65306; ‘dtrx, mono-complete, tree.....’ through apt-get install directly.
I just get the unalbe to loacte error:
[HTML]E: Unable to locate package dtrx[/HTML]
So i try to download the .deb binaried in some other machine, and then install them using dpkg.
But i get the following errors this time:
[HTML]root@ubuntu:/home/gan.liu/downloads# dpkg -i dtrx_6.6-1.2_all.deb Selecting previously unselected package dtrx.(Reading database ... 69548 files and directories currently installed.)Preparing to unpack dtrx_6.6-1.2_all.deb ...Unpacking dtrx (6.6-1.2) ...dpkg: dependency problems prevent configuration of dtrx: dtrx depends on p7zip-full; however:  Package p7zip-full is not installed. dtrx depends on cabextract; however:  Package cabextract is not installed. dtrx depends on unshield; however:  Package unshield is not installed.
dpkg: error processing package dtrx (--install): dependency problems - leaving unconfiguredProcessing triggers for man-db (2.6.7.1-1ubuntu1) ...Errors were encountered while processing: dtrx[/HTML]

What can i do to get these kind of packages installed ?

Regards!

---

### Post by aalg on 2019-03-12
update error info for easy reading:
```
root@ubuntu:/home/gan.liu/downloads# dpkg -i dtrx_6.6-1.2_all.deb Selecting previously unselected package dtrx.
(Reading database ... 69548 files and directories currently installed.)
Preparing to unpack dtrx_6.6-1.2_all.deb ...
Unpacking dtrx (6.6-1.2) ...
dpkg: dependency problems prevent configuration of dtrx:
 dtrx depends on p7zip-full; however:
  Package p7zip-full is not installed.
 dtrx depends on cabextract; however:
  Package cabextract is not installed.
 dtrx depends on unshield; however:
  Package unshield is not installed.


dpkg: error processing package dtrx (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 dtrx

```

---

### Post by mastablasta on 2019-03-13
uf.... you need to resolve your dependencies: 

```
dpkg: dependency problems prevent configuration of dtrx:
 dtrx depends on p7zip-full; however:
  Package **p7zip-full** is not installed.
 dtrx depends on cabextract; however:
  Package **cabextract **is not installed.
 dtrx depends on unshield; however:
  Package **unshield **is not installed.
```

if the server can't be connected to internet you might want to think about having your own repositories.

---

### Post by mtodorov69 on 2019-03-13
It seems obvious from the output that dtrx requires p7zip-full, cabextract and unshield at least to be installed.

But it would be better to install automatically rather than manual. dtrx seems to be on the **universe** repository for trusty (Ubuntu 14.04 server) ... What are the contents of your **/etc/apt/sources****.list** ?
 
Full list of dtrx's dependencies can be found here: [B][https://packages.ubuntu.com/trusty/utils/dtrx](https://packages.ubuntu.com/trusty/utils/dtrx)

[/B]

---

