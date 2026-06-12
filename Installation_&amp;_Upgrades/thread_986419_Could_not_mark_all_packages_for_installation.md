---
title: "Could not mark all packages for installation"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by bborg on 2008-11-18
I recieve the following message when trying to install Xastir 1.9.2-2.1 
on my Ubuntu 8.10 machine:

Could not mark all packages for installation or upgrade

The following packages have unresolved dependencies. 
Make sure that all required repositories are added and 
enabled in the preferences.

xastir:
 Depends: libgdal1-1.5.0 but it is not going to be installed
 Depends: gpsman but it is not going to be installed
 Depends: gpsmanshp but it is not going to be installed

How do I add the required repositories?:confused:

---

### Post by Partyboi2 on 2008-11-18
Go to Software Sources (System>Admin>Software Sources) and on the first tab tick all the boxes at the top  except source code.

---

### Post by mrtomservo on 2008-11-18
Try updating the package list before installing.  If that doesn't work, can you post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by bborg on 2008-11-19
Go to Software Sources (System>Admin>Software Sources) and on the first tab tick all the boxes at the top except source code.

thanks to Partyboi2

---

