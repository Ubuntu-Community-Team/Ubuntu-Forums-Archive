---
title: "[SOLVED] update manager 6.10 &amp;gt; 7.04 stuck"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by Lonneke on 2008-04-08
Hello everybody, 

Could it be that [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) is out of the air?
I'm trying to upgrade using the updtae manager, but I get stuck when preparing the installation at file 31 of 33.


[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free/i18n/Translation-en_US.bz2:) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out
[http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2:](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free/i18n/Translation-en_US.bz2:) Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

Thank you,

---

### Post by Partyboi2 on 2008-04-08
If you are upgrading from dapper to feisty I suggest disabling 3rd party repo's from your sources.list before upgrading if you have not already done so.
System>Admin>Software Sources>Third Party Software.

---

### Post by Lonneke on 2008-04-08
Thank you, 
That worked!!

---

