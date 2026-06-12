---
title: "I had Ubuntu 8.04 installed some months ago: Ubunto upgrade crashed! Help!!"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by DThurman on 2009-12-17
I know this is a latecomer, but did anyone post a remedy to this?

Apparently the upgrade complained of an incompatable kernel
and requested for v2.6.24.25.26, and went ahead, and complained
anyway.  On a reboot there was a message saying something of
the effect that there was a problem with two db2v2 and db2v3
conflicts: db2v2 seemed ok but db2v3 failed.  Also, there is
from /var/log/messages:

Dec 17 16:04:01 bronze kernel: [  111.244705] glxinfo[8479]: segfault at 00000200 eip b7f75bdd esp bf9e3fe0 error 4

Seems that the debian apt database failed and something with
the glxinfo?

What to do to get this fixed?

Thanks!
Dan

---

