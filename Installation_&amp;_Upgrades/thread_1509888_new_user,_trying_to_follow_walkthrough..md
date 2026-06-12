---
title: "new user, trying to follow walkthrough."
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by chedderslam on 2010-06-14
I am brand new to linux.  I am trying to foloow a walkthrough.

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Could not connect to packages.freecontrib.org:80 (34.52.53.34), connection timed out

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.freecontrib.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

How do I fix this?

---

### Post by amauk on 2010-06-14
it looks like you are following a really old guide

The error messages mention Dapper
which is a 4-year-old Ubuntu version, and no longer supported

can you post the contents of /etc/apt/sources.lst
```
gedit /etc/apt/sources.lst
```

and also exactly what you are trying to do
(a link to the guide you're using)

---

