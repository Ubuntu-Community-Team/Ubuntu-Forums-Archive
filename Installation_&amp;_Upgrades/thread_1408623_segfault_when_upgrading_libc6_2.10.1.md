---
title: "segfault when upgrading libc6 2.10.1"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by hbbk on 2010-02-16
hi 

I just upgraded my kubuntu karmic with karmic-update sources and got the following error, (I really don't like when I have installation of libc with errors :) this will bring huge problems later for sure)

Any clue to repair that ?

```

root@hbbk:/# aptitude safe-upgrade
...
Get:1 http://fr.archive.ubuntu.com karmic-updates/main libc6 2.10.1-0ubuntu16 [3759kB]
...
Preparing to replace libc6 2.10.1-0ubuntu15 (using .../libc6_2.10.1-0ubuntu16_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libc6_2.10.1-0ubuntu16_i386.deb (--unpack):
 subprocess new pre-installation script killed by signal (Segmentation fault)
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.10.1-0ubuntu16_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.10.1-0ubuntu16); however:
  Version of libc6 on system is 2.10.1-0ubuntu15.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
...
root@hbbk:/# aptitude show libc6-i686
Package: libc6-i686
State: installed
Automatically installed: no
Version: 2.10.1-0ubuntu15
...

```

---

### Post by hbbk on 2010-02-16
I downgraded some packages so that I could continue use aptitude

```

Downgrade the following packages:
libc-bin [2.10.1-0ubuntu16 (karmic-updates, now) -> 2.10.1-0ubuntu15 (karmic)]
libc-dev-bin [2.10.1-0ubuntu16 (karmic-updates, now) -> 2.10.1-0ubuntu15 (karmic)]
libc6-dev [2.10.1-0ubuntu16 (karmic-updates, now) -> 2.10.1-0ubuntu15 (karmic)]

``` 

But now each time I try to install something I have a seg fault with aptitude (or apt-get), I cleaned the cache /var/cache/apt but nothing changed

```

root@hbbk:/# apt-get install mencoder mplayer mplayer-nogui
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  mplayer-doc
The following packages will be upgraded:
  mencoder mplayer mplayer-nogui
3 upgraded, 0 newly installed, 0 to remove and 112 not upgraded.
Need to get 6015kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://fr.archive.ubuntu.com karmic-updates/multiverse mplayer-nogui 2:1.0~rc3+svn20090426-1ubuntu10.1 [2090kB]
Get:2 http://fr.archive.ubuntu.com karmic-updates/multiverse mencoder 2:1.0~rc3+svn20090426-1ubuntu10.1 [1657kB]
Get:3 http://fr.archive.ubuntu.com karmic-updates/multiverse mplayer 2:1.0~rc3+svn20090426-1ubuntu10.1 [2268kB]
Fetched 6015kB in 16s (362kB/s)
Segmentation fault
...

```

Any idea ?

---

