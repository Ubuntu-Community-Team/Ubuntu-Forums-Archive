---
title: "Severe symbol sigaction error on Koala (Synaptic crashes)"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by sayyeah on 2009-11-20
Hi all, after upgrading from 9.04 to 9.10, I cannot run the svn client and Synaptic manager. (possibly some other apps as well.)

First, I tried to update from svn repo using conventional commands:
```
$ svn co https://robotcub.svn.sourceforge.net/svnroot/robotcub/trunk/iCub

svn: relocation error: /usr/lib/libapr-1.so.0: symbol sigaction, version GLIBC_2.0 not defined in file libpthread.so.0 with link time reference

```

So after searching for libapr-1 on Synaptic, I found that there are libapr-1-dev and -dbg packages.
When I tried to install them, an error message appeared:

```
dpkg: relocation error: dpkg: symbol sigaction, version GLIBC_2.0 not defined in file libpthread.so.0 with link time reference
```

After this incidence, I cannot even run Synaptic manager at all now!
It only shows the following error message:

```

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

When I run as it says:
```

$ sudo dpkg --configure -a

Setting up man-db (2.5.6-2) ...
dpkg: relocation error: dpkg: symbol sigaction, version GLIBC_2.0 not defined in file libpthread.so.0 with link time reference
sayyeah@kyu-mobile:~/work/icub/icub_software$ /usr/bin/perl: relocation error: /usr/bin/perl: symbol sigaction, version GLIBC_2.0 not defined in file libpthread.so.0 with link time reference

```

Any hint please?

---

### Post by sayyeah on 2009-11-20
Well, 'sudo dpkg --configure -a' worked after two times of rebooting. Now svn and Synaptic are running ok but I really don't understand about this weird behavior.

---

