---
title: "Finch confusion..."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by TheBane on 2009-11-24
I thought finch came bundled with Pidgin, so I tried to run finch in the shell and was told I didn't have it, thus I:

```
sudo apt-get install finch 
```

and here is my output...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  finch: Depends: pidgin-data (< 1:2.6.2-z) but 1:2.6.3-1ubuntu1~pidgin1.9.04.1 is to be installed
E: Broken packages
```

Also tried to install it via the SPM and got the same error message: 

```
finch: Depends: pidgin-data (< 1:2.6.2-z) but 1:2.6.3-1ubuntu1~pidgin1.9.04.1 is to be installed
E: Broken packages
```

Any help would be sweet. Thanx in advance. =)

---

### Post by mad_ady on 2009-11-30
Yes, I have the same problem in Karmic Koala:
```

root@frost:~# apt-get install finch
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  finch: Depends: pidgin-data (< 1:2.6.2-z) but 1:2.6.3-1ubuntu1~pidgin1.9.04.1 is to be installed
E: Broken packages
root@frost:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

```

I have manually downloaded the deb, installed it with dpkg force, and it worked for a while, until the package management system said it had to be removed because of the conflicts.

Looks to me like an error in the package management system.

Any known workarounds?

---

### Post by TheBane on 2009-12-01
Actually worked itself out. Must have been an un-updated package at the time I was trying to install it. Oh wells. :D

---

