---
title: "bug: updating from 10.10 to 11.04, fglrx"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2011-05-02
my upgrade FAILED because of this package. so remove it beforehand.

`dpkg --force-all -P fglrx`

if you already did the upgrade, like me, do this:

`dpkg-divert --rename --remove /usr/lib/libGL.so.1.2`
`dpkg --force-all -P fglrx`
`apt-get update && apt-get dist-upgrade`


oh, and you will NOT have 3d after the update. so, just do not do it yet.

---

