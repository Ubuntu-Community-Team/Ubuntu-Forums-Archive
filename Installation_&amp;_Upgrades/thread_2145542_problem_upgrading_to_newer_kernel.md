---
title: "problem upgrading to newer kernel"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by d0.higgs on 2013-05-15
Hi all,

I have finally (after three days of try and fail - where I was trying to install Mint) installed Linux (Xubuntu) on my Toshiba NB505 netbook.
right after installation is done, I tried to upgrade to the latest packages.
I am now having this error message every time I try to in/un-stall a package:
```
d0.higgs@d0.higgs:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-41-generic (3.2.0-41.66) ...
Running depmod.
Failed to run depmod
dpkg: error processing linux-image-3.2.0-41-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-41-generic; however:
  Package linux-image-3.2.0-41-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.41.49); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.2.0-41-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
d0.higgs@d0.higgs:~/Desktop$
```

what should I do to get rid of this trouble?

Thanks in advance to u all.

---

