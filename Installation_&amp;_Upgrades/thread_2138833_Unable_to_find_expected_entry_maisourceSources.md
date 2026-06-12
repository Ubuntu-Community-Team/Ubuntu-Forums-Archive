---
title: "Unable to find expected entry mai/source/Sources"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by rudeboyskunk on 2013-04-25
Howdy guys, I just did a fresh install of Ubuntu 13.04 64-bit and was adding all of the usual extra repositories and everything that I use, and then all of a sudden I did a sudo apt-get update and got this:

```
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release  Unable to find expected entry 'mai/source/Sources' in Release file (Wrong sources.list entry or malformed file)
```

Anybody seen this before?  Know how to fix it?  I can't update my system and install certain programs because of it.  Any help would be appreciated.

---

### Post by rudeboyskunk on 2013-04-25
Nevermind; I'm an idiot.  I re-checked my /etc/apt/sources.list, and saw that the "n" was missing off of "main" in one of the sources.  #-o

---

