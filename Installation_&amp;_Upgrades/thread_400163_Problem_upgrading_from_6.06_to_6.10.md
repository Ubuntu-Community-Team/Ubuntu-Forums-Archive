---
title: "Problem upgrading from 6.06 to 6.10"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by endre on 2007-04-03
This problem has persisted for weeks now. I want to upgrade from Dapper to Edgy so that I can do a direct upgrade to Feisty when it comes, BUT: I can't!

Whenever I try to make the upgrade, it never get further than "preparing the upgrade," the first step, and then it counts up the 64 first files.... and then it stops just past 60... and I get the same error messages every time! Two to four files could not be fetched; this is the error message I got last time:

Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg) Klarte ikke å koble til [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), tidsavbrudd på forbindelsen
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper-plf/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper-plf/Release.gpg) Klarte ikke å koble til packages.freecontrib.org:80 (88.191.33.6), tidsavbrudd på forbindelsen
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently

All the files either time out or are moved...

What should I do?

---

### Post by taurus on 2007-04-03
When you upgrade from one version to another, it is a good idea to comment out all the 3rd party repos in /etc/apt/sources.list.  Therefore, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of those repos.

---

