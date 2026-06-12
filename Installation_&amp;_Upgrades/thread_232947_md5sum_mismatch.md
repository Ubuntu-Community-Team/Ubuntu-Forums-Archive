---
title: "md5sum mismatch"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by Richard Kimber on 2006-08-09
Having used Dapper on my desktop for some time, I decided to upgrade the Breezy installation on my laptop.  However, doing apt-get update first, gave me the error:-

[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-amd64/Packages.gz) MD5Sum mismatch

There seems to be nothing wrong with my network connection, and I've not done anything funny with my Breezy installation.

How do I get round this?

---

### Post by mlind on 2006-08-09
There's been a lot of related problems with main Ubuntu repositories lately, especially security.ubuntu.com. I guess you'll either have to change to another mirror or try until you succeed.
For list of mirrors see [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive)

If you're wondering why there's no corresponding mirror for security.ubuntu.com, you just need to use **distribution name** (dapper-security) with the mirror you select.
For one of the US mirrors repository list would be
```

deb http://mirror.cs.umn.edu/ubuntu **dapper** main restricted multiverse universe
deb http://mirror.cs.umn.edu/ubuntu **dapper-updates** main restricted multiverse universe
deb http://mirror.cs.umn.edu/ubuntu **dapper-security** main restricted multiverse universe

```

---

