---
title: "Ubuntu iso image"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by brian8765 on 2012-11-16
Hi,
I downloaded the 64 bit version of ubuntu 12.10 and I noticed that the size of the file (800.1 MB) is different to the one that is downloadable straight from the server (750 MB or something like that)
Why is this the case?
Thanks

---

### Post by sffvba[e0rt on 2012-11-16
It is possible that the way sizes are calculated differ (for some 1024kb = 1mb and 1024mb = 1gb etc.) while others go (1000kb = 1mb and 1000mb = 1gb).

*Please note that I am not using kb, mb or gb correctly as I am not sure now the correct way of writing them to mean what they should.*

If you are in doubt if the iso you downloaded is correct do a checksum on it: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


404

---

### Post by Mr_JMM on 2012-11-16
> **brian8765 said:**
> Hi,
I downloaded the 64 bit version of ubuntu 12.10 and I noticed that the size of the file (800.1 MB) 
Where from? From Canonical it's ~763MB.

> **brian8765 said:**
> is different to the one that is downloadable straight from the server (750 MB or something like that)
What server?

If you're comparing the iso from the upgrade option then it could just be that the upgrade version doesn't require every file again.

Bottom line: Download directly and check MD5sums. If they match you're good to go, don't worry about the finished download size.

---

