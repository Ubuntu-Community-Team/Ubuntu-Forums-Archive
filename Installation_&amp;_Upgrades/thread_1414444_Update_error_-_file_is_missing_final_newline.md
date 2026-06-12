---
title: "Update error - file is missing final newline"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by Alan001 on 2010-02-23
I have recently taken delivery of a Dell Inspiron mini netbook with Ubuntu on, and I am new-fangled ...

To install updates, I clicked the (orange down-arrow) button, and it compalined 

"E: /var/cache/apt/archives/linux-image-2.6.24-22-lpia_2.6.24-22.45netbook9_lpia.deb: files list file for package `libxcb-shape0' is missing final newline"

This is not easy for a beginner to understand!  Any ideas?

---

### Post by ajgreeny on 2010-02-23
Have you updated before with success?  Whether or not you have done so, it seems that the information thet the system has already obtained, and perhaps that package mentioned, is broken.  Try ```
sudo apt-get update
``` again in terminal, but if that gives the same error try removing all the cache from /var/cache/apt/archives with ```
sudo apt-get clean
``` and then try updating yet again.

You could always remove just that package if you prefer, by opening nautilus with root permissions```
gksudo nautilus
```then navigating to /var/cache/apt/archives and deleting the package, but be very careful; you can do great damage as root by removing something important, so once you have deleted that package shut down nautilus.

---

### Post by Alan001 on 2010-03-01
ajgreeny,

I've tried all of that, and no joy. 

It is trying to install 15 updates. Can I not do them one at a time? 

(Maybe it needs one of the earlier ones to be done to avoid the problem with the later one.)

---

