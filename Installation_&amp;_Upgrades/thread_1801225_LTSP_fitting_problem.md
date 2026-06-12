---
title: "LTSP fitting problem"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by nevertheless-it-spins on 2011-07-10
Hi everyone
Ubuntu 10.10

We have an Ubuntu cluster made on the basis of fat clients of ltsp. The cluster has been working for several months on a series of 4-core nodes.
Now we installed a new system on the basis of 4-socket/12-core Supermicro platform ([http://www.supermicro.nl/Aplus/system/2U/2042/AS-2042G-TRF.cfm](http://www.supermicro.nl/Aplus/system/2U/2042/AS-2042G-TRF.cfm)) and a problem appeared. See attached screenshot.
But I do not think that this is a hardware problem. All hardtests are OK.
It seems to me the problem related to the storage structure I chose. It is the following.

Rootfs is aufs, where the ro-filesystem is nfs and rw-filesystem is either tmpfs or nfs4 on a local disk. Moreover, nfs is mounted using cachefiles. I know it is a bit complcated, but it worked on all other systems.
I guess the problem appears due to massive simultaneous read-write whick appears with about 12 tasks.

Could you offer some solutions?

---

