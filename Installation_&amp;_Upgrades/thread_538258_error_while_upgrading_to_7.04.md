---
title: "error while upgrading to 7.04"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by wesmsl on 2007-08-29
I am trying to upgrade ubuntu from 6.10 to 7.04.  When I try to update using the update manager I get an error message:

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

Any ideas how I can fix this so I can upgrade?

Thanks,

---

### Post by merlinus on 2007-08-29
You might try commenting out those lines in /etc/apt/sources.list.  It seems they refer to breezy!

-merlin

---

