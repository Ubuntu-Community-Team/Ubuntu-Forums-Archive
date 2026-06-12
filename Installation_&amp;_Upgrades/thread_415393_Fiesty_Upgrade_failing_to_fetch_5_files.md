---
title: "Fiesty Upgrade failing to fetch 5 files?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mahlersreincarnation on 2007-04-20
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
Failed to fetch [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/i18n/Translation-en_US.bz2](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/non-free/i18n/Translation-en_US.bz2) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)

To the more experienced linux users out there, what's going on? What can I do to solve this?

---

### Post by mahlersreincarnation on 2007-04-20
Bump?

---

### Post by Newmaniese on 2007-04-26
from your etc/apt/souces.list you should remove all third party software. This should fix your problem.

---

