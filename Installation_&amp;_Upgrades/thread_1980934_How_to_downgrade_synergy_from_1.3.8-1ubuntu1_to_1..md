---
title: "How to downgrade synergy from 1.3.8-1ubuntu1 to 1.3.6-1ubuntu1"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by raffen on 2012-05-16
*How do I downgrade synergy from 1.3.8-1ubuntu1 to 1.3.6-1ubuntu1 on ubuntu 12.04?*

Background:  The upgrade from 11.10 to 12.04 introduced a broken version of synergy.  This is well documented in [bug 926198]("https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/926198").  I cannot upgrade to the upstream 1.4 version because that would break compatibility existing 1.3 servers.

```

$ grep synergy /var/log/dpkg.log
2012-05-14 09:52:27 upgrade synergy 1.3.6-1ubuntu1 1.3.8-1ubuntu1
$ apt-cache showpkg synergy | grep -A1 ^Provides
Provides: 
1.3.8-1ubuntu1 - 

```

---

