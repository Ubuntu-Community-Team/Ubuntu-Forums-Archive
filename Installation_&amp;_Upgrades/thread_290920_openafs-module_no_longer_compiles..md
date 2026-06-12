---
title: "openafs-module no longer compiles."
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by joemo75 on 2006-11-01
The openafs kernel module for Ubuntu 6.10 wont compile anymore.  It dies with the following error.

```

 /usr/src/modules/openafs/src/afs/LINUX/osi_machdep.h:55:2: error: #error   &#9618; 
 &#9474; Not sure what to do about rlim (should be in the Linux task struct         &#9618; 
 &#9474; somewhere....)

```

---

### Post by JDahl on 2006-11-02
You need version 1.4.2 of openafs. This link

[http://ubuntuforums.org/showthread.php?t=264992&page=2](http://ubuntuforums.org/showthread.php?t=264992&page=2)

takes you through how to compile a working package from Debian unstable.

---

### Post by dlg on 2007-01-20
> **joemo75 said:**
> The openafs kernel module for Ubuntu 6.10 wont compile anymore.  It dies with the following error.

```

 /usr/src/modules/openafs/src/afs/LINUX/osi_machdep.h:55:2: error: #error   &#9618; 
 &#9474; Not sure what to do about rlim (should be in the Linux task struct         &#9618; 
 &#9474; somewhere....)

```


you need to use openafs 1.4.2 with edgy.  with the help of #openafs i've built the necessary packages.  they're available here: **[http://www.dsrw.org/~dlg/moebius/linux/ubuntu-openafs/](http://www.dsrw.org/~dlg/moebius/linux/ubuntu-openafs/)**

---

