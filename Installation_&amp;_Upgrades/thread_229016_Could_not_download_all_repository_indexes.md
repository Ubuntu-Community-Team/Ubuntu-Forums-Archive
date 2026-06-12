---
title: "Could not download all repository indexes"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by orb9220 on 2006-08-03
I get this in updater

http://packages.freecontrib.org/ubuntu/plf/dists/dapper/main/binary-i386/Packages.gz:[/url] 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/restricted/binary-i386/Packages.gz:[/url] 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/universe/binary-i386/Packages.gz:[/url] 404 Not Found
http://packages.freecontrib.org/ubuntu/plf/dists/dapper/multiverse/binary-i386/Packages.gz:[/url] 404 Not Found

Are these main repositories? Or can I remove them thru synaptic so upgrader dosn't error on checking.

---

### Post by taurus on 2006-08-03
Those look to me like some extra repos.  You can command them out by placing a # in front of those lines in /etc/apt/sources.list...  You can do it with synaptic or from a terminal with 

```

sudo gedit /etc/apt/sources.list

```
Then, update and upgrade it with

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by orb9220 on 2006-08-03
Thanks it was probally something I uncommented when I was trying out.

I fiqured as much but wanted to be sure.

Thansk

---

