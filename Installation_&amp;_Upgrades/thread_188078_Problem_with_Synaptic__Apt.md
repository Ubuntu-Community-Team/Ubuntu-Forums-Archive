---
title: "Problem with Synaptic / Apt"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by bmagill on 2006-06-03
Following an upgrade from Breezy to Dapper, I am having problems with apt.  It fails to load from repositories.  It seems that it is trying to connect to the localhost.  I don't know why.  I reactivated additional repositories post-upgrade through synaptic, but I have done nothing else to the config files.

How do I fix this?

Thanks


```
http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://packages.freecontrib.org/ubuntu/plf/dists/breezy/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://wine.sourceforge.net/apt/binary/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
http://cran.R-project.org/bin/linux/debian/stable/Release.gpg: Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)
```

---

