---
title: "E: Error, pkgProblemResolver::Resolve generated breaks"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by Zulan on 2012-06-01
Hello!

I have ubuntu 12.04 server x64. I have been trying to get libusb to work and tried a whole bunch of stuff. Now I have ended up in something I cant fix. I try to remove c++ with apt-get remove c++. I get a bunch of text and then it ends with:

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I have no idea what to do now, any ideas?

---

### Post by zvacet on 2012-06-03
Try with 

```
sudo apt-get dist-upgrade
```

---

