---
title: "FreeRadius Installation Problem"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by sham480 on 2006-11-07
Hi,

sorry if this is obvious, im new to ubuntu or any linux OS. Im trying to install freeradius, and i keep getting this error everytime i use *make install*

**libtool: install: `rlm_acct_unique.la' is not a valid libtool archive**

I looked around trying to find out the answer to this problem but with no luck. If someone could help i would be much appreciate it. Thanks

EDIT: Found problem, i was missing perl which had a few errors in the actual make command which werent noticed when i first ran it, therefore cauing this problem. Sorry

---

### Post by raze_the_wolf on 2007-07-22
Old post but may help somebody else ...

I had same problem under centos5.

I resolved by installing libtool and libtool-libs packages.

I also saw in freeradius-1.1.6/redhat/freeradius.spec this line :
[INDENT][/INDENT]"BuildPreReq: libtool libtool-ltdl-devel"

After that, the make install appears to be fine.

Good luck.

---

