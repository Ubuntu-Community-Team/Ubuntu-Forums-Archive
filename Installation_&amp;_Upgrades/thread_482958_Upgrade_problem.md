---
title: "Upgrade problem"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by maxweld on 2007-06-24
I am trying to upgrade from Ubuntu 6.06 to 6.10 on my way to 7.04.

I have issued ```
gksu "update-manager -c -d"

```

I then get told that a few packages will be deferred, which I sort of expected.

I then get offered the upgrade, but while it is a few seconds into the first step, Preparing the Upgrade, it complains with 

```
Failed to fetch http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/freenx/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-i386/Packages.gz 302 Found
Failed to fetch http://free.linux.hp.com/~brett/seveas/freenx/dists/breezy-seveas/freenx/source/Sources.gz 404 Not Found

```

What is it trying to tell me, and how can I get around this obstacle?

Thanks in advance
maxweld

---

### Post by maxweld on 2007-06-24
Hey - Its OK

I just needed to remove a few lines in /etc/apt/sources.lst

Thanks anyway

---

