---
title: "problem installing vmware workstation on server 8.04"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by trawler on 2009-11-16
I've installed ubuntu server 8.04 and i'm trying to install vmware workstation 5.5. 
I know it's an old version, but it needs to be that specific version.

The installation went ok (just installing a deb file) but I'm stuck at vmware-config.pl:
```
What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.24-25-server/include/

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.24-25-server).  Even if the module were to 
compile successfully, it would not load into the running kernel. 
```

I have 2 directories under /usr/src -
linux-headers-2.6.24-25
linux-headers-2.6.24-25-server

Output of uname -r:
```
2.6.24-25-server
```

Vmware insists the the directory i gave is not of my running kernel, but it has to be...
Any ideas?

---

