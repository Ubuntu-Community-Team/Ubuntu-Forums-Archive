---
title: "uptimed install woes"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by geforce123 on 2008-01-28
I previously uninstalled it using apt-get...

When I try to re-install it:

```
apt-get install uptimed
Reading package lists... Done
Building dependency tree... Done
uptimed is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up uptimed (0.3.3-8) ...
/var/lib/dpkg/info/uptimed.postinst: line 39: /etc/uptimed.conf: No such file or directory
dpkg: error processing uptimed (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 uptimed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by geforce123 on 2008-01-31
I managed to fix it myself.

Somehow, apt-get got confused ...

I did a 

```
touch /etc/uptimed.conf
```

and it worked.

---

