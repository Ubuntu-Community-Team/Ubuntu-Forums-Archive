---
title: "When upgrading, 404's from packages.freecontrib.org?"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Nick Wilson on 2007-01-06
Hi everyone, 

Im trying to upgrade my wife's machine from Dapper to Edgy using the official method but it keeps stalling becuase of a couple of 404's being thrown out by packages.freecontrib.org

```

Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/free/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://packages.freecontrib.org/plf/dists/edgy/non-free/binary-i386/Packages.gz 404 Not Found

```

I've checked. They're not there. 

Any ideas?

---

### Post by taurus on 2007-01-06
I think the site is down (or even dead) so you need to comment it out by placing a # in front of it in /etc/apt/sources.list...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Nick Wilson on 2007-01-06
I had thought of doing that but wondered if it might bork the upgrade. 

Will give it a go, thanks.

---

### Post by taurus on 2007-01-06
Actually, it is better to comment out the third party repos in /etc/apt/sources.list when you do an upgrade...

---

