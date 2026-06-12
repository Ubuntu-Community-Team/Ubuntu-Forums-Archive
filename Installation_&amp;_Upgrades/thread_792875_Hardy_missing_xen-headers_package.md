---
title: "Hardy missing xen-headers package"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by michaeldasilvapereira on 2008-05-13
Hi All,

I'm not sure if anybody else has had such an issue yet, When trying to install IPTables:IPV4 which relies on a few headers files from the kernel.

After posting on the mailling list for IPTables::IPV4 I soon found out that the missing header files are located in a package called xen-headers which only exists for gutsy and not hardy ?

Some people seem to believer its a bug in Hardy missing this package?

Has anybody had this?

> "apt-file search ip_nat.h" finds this file in xen-headers-2.6.* packages. Sounds a bit weird that the xen-headers would contain this while linux-headers doesn't. Maybe it's related to the fact that xen-headers are for 2.6.16 and 2.6.19 while linux-headers is for 2.6.22 (bug in linux-headers?)

> Hi, 

  

I see there is a xen-headers package for gutsy, but nothing out there for hardy?


Oops you are right. I searched this on my desktop which is still Gutsy (laptop is at hardy).

Have you tried to run "apt-file search"?

If worse comes to worst, you can either:
1. Download the linux-source package and enable this module.
2. Download a vanilla linux kernel and create source packages with kernel-kpkg.

In any case, this sounds like a Hardy issue, consider filing a bug against hardy's kernel source package and/or asking on ubuntuforums.org.


Thanks,
Mike

---

