---
title: "Upgrade error. 6.10 to 7.04"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by ylipam on 2007-09-06
I tried (couple of times) to upgrade Ubuntu edgy 6.10 to 7.04 from "Software updates".
Download goes well, but when program starts to prepare the upgrade following error comes:

"Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry."
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Network connection is working fine (download works).
I think I've been messing up my repositories?

Didn't find any familiar error from this forum.
Would appreciate some help, thanks.

---

### Post by zvacet on 2007-09-06
```
gksudo gedit etc/apt/sources.list
```

In front of that two lines put # sign.Save file and 

```
sudo aptitude update
```

Try to upgrade again.

---

