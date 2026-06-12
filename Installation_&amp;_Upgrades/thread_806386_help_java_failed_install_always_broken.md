---
title: "help java failed install always broken"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by bannik on 2008-05-24
E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/server/libjvm.so')

this is the error i get when trying to install using "add/remove"

---

### Post by bannik on 2008-05-25
bump

---

### Post by prshah on 2008-05-26
> **bannik said:**
> E: /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/server/libjvm.so')

this is the error i get when trying to install using "add/remove"

Looks like an error either in that particular deb file or in the disk at that area. Try deleting the file '/var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb' and then installing java. To delete that file, open a terminal (Application-Accessories-Terminal) and the give the below command```
sudo rm /var/cache/apt/archives/sun-java6-bin_6-06-0ubuntu1_i386.deb
```

---

