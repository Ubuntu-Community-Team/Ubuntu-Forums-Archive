---
title: "Upgrade from 12.10 to 13.04 fails on ppa.launchpad.. packages not found"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by cookf on 2013-06-02
I am trying to upgrade my desktop from 12.10 to 13.04. It was totally successful on my laptop.

Searching the forum, I found a number of similar threads but following the suggested solution doesn't seem to work. I tried to upgrade via DVD (Ubuntu User) grays option of upgrade out. I can install a the new version of the top of 12.10 but am reluctant to do so (avoiding to install a long list of software again). 
Using software updater via the dash fails on a particular library not found (see below). Running sudo apt-get update provides a long list of which I have copied the last few lines in the quote below. It appears to me a single library can't be found. Can it be commented out? Any help is much appreciated.

```
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Ign https://private-ppa.launchpad.net quantal/main Translation-en_GB
Ign https://private-ppa.launchpad.net quantal/main Translation-en
Fetched 968 kB in 34s (28.4 kB/s)
W: Failed to fetch http://ppa.launchpad.net/libv4l/ppa/...-i386/Packages 404 Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ibjsb4 on 2013-06-02
There is no ppa package for 13.04, remove it.

[http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/](http://ppa.launchpad.net/libv4l/ppa/ubuntu/dists/)

---

### Post by cookf on 2013-06-04
Much appreciated. I'll give it a try when back home.

---

