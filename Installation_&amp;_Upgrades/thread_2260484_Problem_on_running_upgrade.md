---
title: "Problem on running upgrade"
date: 2015-01-12
forum: Installation &amp; Upgrades
---

### Post by satimis on 2015-01-12
Hi all,

Ubutun 14.04

On running sudo apt-get update ; sudo apt-get upgrade```

....
Ign http://hk.archive.ubuntu.com trusty/multiverse Translation-en_HK           
Ign http://hk.archive.ubuntu.com trusty/restricted Translation-en_HK           
Ign http://hk.archive.ubuntu.com trusty/universe Translation-en_HK             
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Please help.  Thanks

Regards
satimis

---

### Post by ian-weisser on 2015-01-12
404 means exactly what it always means.

There is no Trusty version of that PPA. See [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists)

---

### Post by satimis on 2015-01-12
> **ian-weisser said:**
> 404 means exactly what it always means.

There is no Trusty version of that PPA. See [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists)

OK, thanks

satimis

---

