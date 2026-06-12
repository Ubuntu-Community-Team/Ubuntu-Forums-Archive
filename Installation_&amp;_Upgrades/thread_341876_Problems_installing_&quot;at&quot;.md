---
title: "Problems installing &quot;at&quot;"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by realriot on 2007-01-19
Hi,

i've installed my ubuntu-server (DAPPER) with debootstrap... Now I try to install the "at" package. This fails with:

apt-get install at
Reading package lists... Done
Building dependency tree... Done
at is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up at (3.1.9ubuntu3) ...
 * Starting deferred execution scheduler...
invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 at
E: Sub-process /usr/bin/dpkg returned an error code (1)

Somethings goes wrong with "invoke-rc.d" and "atd" ...

I'm using Dapper AMD64

Would be great if someone could give me a hint what's going wrong and how to fix this problem.

Best wishes
Sascha

---

### Post by JamieC on 2007-01-19
Open a new terminal and type the following:
```

apt-get -f install
apt-get update

```

---

### Post by realriot on 2007-01-22
apt-get -f install
apt-get update

does not work... The installation of at fails with the same reason:

> 
apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up at (3.1.9ubuntu3) ...
 * Starting deferred execution scheduler...
invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 at
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any other hints which could work?

Best regards,
Sascha

---

