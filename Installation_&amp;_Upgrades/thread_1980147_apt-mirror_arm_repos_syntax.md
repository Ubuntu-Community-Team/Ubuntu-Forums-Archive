---
title: "apt-mirror arm repos syntax?"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2012-05-14
I'm trying to setup an apt-mirror local repo for Pandaboard ES (OMAP4) systems using apt-mirror.

It all seems to work for deb-amd64 lines but fails for what I think the arm lines should be:
```
deb-armhf http://us.archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
```


I've also tried using deb-arm and deb-armel instead of deb-armhf.

The error message is:
```
Proceed indexes: [PPPPPPsh: 1: cannot open archive.ubuntu.com/ubuntu//dists/precise-updates/main/binary-arm/Packages.gz: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 445.
```


If I comment out the arm lines the deb-i386 and deb-amd64 lines I've put it as a syntax test appear to complete correctly.

---

### Post by wkulecz on 2012-05-15
Bump,

Nobody using apt-mirror with arm (OMAP4)?

Is there a better place to be asking about Precise on ARM?

---

### Post by wkulecz on 2012-05-22
Just in case anyone finds this via Google it seems the OMAP4 stuff is not in the "normal" Ubuntu repos.

This /etc/apt/mirror.list line appears to be downloading:
```
deb-armhf http://ports.ubuntu.com/ubuntu-ports precise main restricted universe multiverse
```

Obviously this forum is not the place for Ubuntu on Pandaboard ES or other ARM/OMAP help :(

---

### Post by easy2love on 2013-02-10
i need to setup an repo mirror for ARM, thanks!

---

