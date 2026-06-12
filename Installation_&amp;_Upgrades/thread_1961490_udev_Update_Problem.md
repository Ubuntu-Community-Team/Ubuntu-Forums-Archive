---
title: "udev Update Problem"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by cagdix on 2012-04-19
Hello;

I want to update my machine but update process failing. 

Log files attached. Can anybody give an advise ?

---

### Post by zvacet on 2012-04-19
```
sudo dpkg --configure -a
```

---

### Post by cagdix on 2012-04-20
:(
Not works..

---

### Post by zvacet on 2012-04-20
It look like some packages depends of udev package.So try 

```
sudo dpkg --configure udev
```

This will not (probably) solved all,but after this list should be shorter.Read again witch package is dependency to other package and try to configure dependencies first.

---

### Post by cagdix on 2012-04-20
dpkg --configure udev
Setting up udev (173-0ubuntu4.2) ...
udev start/running, process 20329
/var/lib/dpkg/info/udev.postinst: 97: udevadm: not found
dpkg: error processing udev (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 udev

---

