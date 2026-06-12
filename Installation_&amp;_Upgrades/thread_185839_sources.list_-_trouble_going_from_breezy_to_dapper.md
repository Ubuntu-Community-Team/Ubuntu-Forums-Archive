---
title: "sources.list - trouble going from breezy to dapper"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by beforewisdom on 2006-06-01
Hi;

I was told that upgrade from breezy to dapper I should replace "breezy"  with "dapper" in my /etc/apt/sources.list then run the update manager.

I got these error messages trying to run the update manager

==========================================================
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

tp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz: Unable to fetch file, server said 'Failed to open file.  '
[http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/dapper/Packages.gz:) 404 Not Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz:) Unable to fetch file, server said 'Failed to open file.  '
[http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/dapper/Sources.gz:) 404 Not Found
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '
[ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/dists/dapper/non-free/source/Sources.gz:) Unable to fetch file, server said 'Failed to open file.  '
[http://kubuntu.org/packages/kde351/dists/dapper/main/binary-i386/Packages.gz:](http://kubuntu.org/packages/kde351/dists/dapper/main/binary-i386/Packages.gz:) 404 Not Found
========================================================


Can anyone post a clean sources.list that I can use to have the package manager upgrade me from breezy to dapper?

Thanks!

---

### Post by aysiu on 2006-06-01
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

