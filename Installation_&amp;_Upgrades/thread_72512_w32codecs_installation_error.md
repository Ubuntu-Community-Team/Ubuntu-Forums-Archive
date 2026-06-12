---
title: "w32codecs installation error"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by batrachian on 2005-10-06
Following the instruction to install w32codecs and got the following errors:

sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate


I guess MPlayer can not work because of this. Please help.

---

### Post by swerner on 2005-10-06
If you search the Ubuntu forum you will find that this has been a big problem. Try:
```
wget ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb
dpkg -i w32codecs_20050412-0.0_i386.deb
```

---

