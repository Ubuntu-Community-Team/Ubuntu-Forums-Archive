---
title: "First apt-get failure in YEARS"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by CaptSaltyJack on 2010-02-11
Wow. I just had apt-get totally bomb on me. I've never ever had this happen before, it's always been such an intelligent and clean process. But today's update on my 9.04 desktop system yielded the following results:

```

Setting up linux-image-2.6.28-18-generic (2.6.28-18.59) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-2.6.28-18-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-18-generic:
 linux-restricted-modules-2.6.28-18-generic depends on linux-image-2.6.28-18-generic; however:
  Package linux-image-2.6.28-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-18-generic; however:
  Package linux-image-2.6.28-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-18-generic; however:
  Package linux-restricted-modules-2.6.28-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.18.23); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.18.23); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-18-generic
 linux-restricted-modules-2.6.28-18-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm fairly confident I can't be the only person who ran into this in the recent batch of updates. How do I fix this and move on??

---

### Post by kansasnoob on 2010-02-11
Try:

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by CaptSaltyJack on 2010-02-11
Yep, tried clean, autoclean, autoremove, nothing will clear this stuff out. Something is hosed.

---

### Post by CaptSaltyJack on 2010-02-11
Fixed it. Ran "sudo apt-get remove linux-restricted-modules-generic linux-image-2.6.28-18-generic" then reinstalled those two and it works.

---

### Post by kansasnoob on 2010-02-11
Well post the output of:

```
df -H
```

BTW that is deliberately a capital H!

```
sudo du -sh /*

```

---

### Post by kansasnoob on 2010-02-11
> **CaptSaltyJack said:**
> Fixed it. Ran "sudo apt-get remove linux-restricted-modules-generic linux-image-2.6.28-18-generic" then reinstalled those two and it works.

Cooooooool!

---

### Post by tgalati4 on 2010-02-11
I'm not sure how to clean up MaxReports.  I'm not sure what the current maximum size is, but obviously you hit it.  I'm glad you found a work around.  Yes, even the apt package manager has bugs.

---

