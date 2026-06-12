---
title: "msn-pecan installing issue"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by MisterGatorade on 2011-05-20
I was installing msn-pecan 1.2.
Compiling, because in the repository there's the old version.
When doing "sudo make install"
I get:

install -D libmsn-pecan.so //usr/lib/purple-2/libmsn-pecan.so
# chcon -t textrel_shlib_t //usr/lib/purple-2/libmsn-pecan.so # for selinux

And the installation stops.
What should I do? Thanks

---

