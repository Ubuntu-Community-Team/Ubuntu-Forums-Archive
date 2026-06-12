---
title: "Fiesty upgrade times out"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by grado on 2007-04-30
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/Release.gpg) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/i18n/Translation-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/binary-i386/Packages.gz](http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/binary-i386/Packages.gz) 403 Forbidden
Failed to fetch [http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/source/Sources.gz](http://www.elisanet.fi/mlind/ubuntu/dists/edgy/fonts/source/Sources.gz) 403 Forbidden

Any suggestions?

---

### Post by johnc4510 on 2007-05-01
If  those are the only non fetches, might be that those 2 servers are down. Try again later

---

### Post by zvacet on 2007-05-01
You should upgrade only with official repos.If you are done with upgrade try this
```
sudo aptitude update && sudo aptitude upgrade
```

PLF didn´t exist anymore.It is medibuntu now.Look here
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by mlind on 2007-05-01
hiya,
replace http://www.elisanet.fi/mlind/ubuntu with *http://www.telemail.fi/mlind/ubuntu*

---

### Post by wesyde on 2007-05-03
I'm having a similar problem when I try to upgrade from 6.06 to 6.10.  Everything is fine up until the last of the 65 files is being downloaded.  The download starts, then hangs and eventually I get the error message

Failed to fetch [http://packages.freecontrib.org/ubun...tion-en_US.bz2](http://packages.freecontrib.org/ubun...tion-en_US.bz2) Could not connect to packages.freecontrib.org:80 (88.191.33.6), connection timed out

The odd thing is that at first it appears that my computer is able to connect, but then it just stops.  I've tried this several times, but always get the same result.

Using the aptitude command gave basically the same result.

---

