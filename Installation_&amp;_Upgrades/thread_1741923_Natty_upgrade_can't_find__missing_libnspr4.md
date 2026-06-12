---
title: "Natty upgrade can't find  missing libnspr4"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Trunkles on 2011-04-28
Oops!

I did a ```
do-release-upgrade
``` on a maverick server and got this.

Any ideas on a fix please?

Simon.

```
Err http://nz.archive.ubuntu.com/ubuntu/ natty/universe libnspr4-0d i386 4.8.7-0ubuntu1
  404  Not Found
Fetched 0B in 0s (0B/s)
Err http://nz.archive.ubuntu.com/ubuntu/ natty/universe libnspr4-0d i386 4.8.7-0ubuntu1
  404  Not Found
Fetched 0B in 0s (0B/s)
Err http://nz.archive.ubuntu.com/ubuntu/ natty/universe libnspr4-0d i386 4.8.7-0ubuntu1
  404  Not Found
Fetched 0B in 0s (0B/s)

Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or
installation media and try again. All files downloaded so far are
kept.

Failed to fetch
http://nz.archive.ubuntu.com/ubuntu/pool/universe/n/nspr/libnspr4-0d_4.8.7-0ubuntu1_i386.deb
404 Not Found



Restoring original system state

Aborting
Reading package lists... Done
Building dependency tree
Reading state information... Done
Building data structures... Done
root@laphroaig:~#
```

---

### Post by dominicsayers on 2011-09-01
Your post is marked as [SOLVED] - did you find a fix? This is happening to me with the GB mirrors at the moment.

---

