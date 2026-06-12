---
title: "Software Updater hangs if IPv6 enabled"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by rattskjelke on 2016-01-14
About a month or so ago I noticed *Software Updater* hanging when trying to get updates.
I tried *apt-get update* and the same thing happens but I can see it hangs up at:
```
Get:65 http://pubmirrors.dal.corespace.com wily-backports/universe Translation-en [270 B]
100% [Connecting to archive.canonical.com (2001:67c:1360:8c01::16)] 
```

I tried different mirrors and they all worked.
It appears to only be archive.canonical.com that will not take IPv6 connections
Then I noticed if I disable IPv6 it works. 
I'm running Xubuntu 10.15 with a wire ethernet connection to a cable modem.
Anybody know what logs to check to see what is going on?

---

