---
title: "failure to find packages.gz* during edgy upgrade"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by ezebe on 2006-12-17
Hi 
I'm a linux newbie having problems upgrading from dapper to edgy.  I type 
gksu "update-manager -c"
into terminal and I immediately get this message,

/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

but update manager starts ok and all seems well. I select the upgrade and click ok, but after 3 or 4 cyles of downloading 41 files it dumps me out, showing this error message.

Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz) 404 Not Found

Is there something wrong in my setup, or are they in the process of being updated or something, and should i just be patient?

---

### Post by taurus on 2006-12-17
I would comment out by playing a # in front of that repo in /etc/apt/sources.list, [http://packages.freecontrib.org/](http://packages.freecontrib.org/)...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by dave.goodfellow on 2007-01-14
Thanks, that worked for me.
Dave

---

