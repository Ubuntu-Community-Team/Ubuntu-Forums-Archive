---
title: "apt-get update freezes"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by badgerofdarkness on 2008-07-23
I recently installed Ubuntu 8.04.1 to an 8 GB SD card to run from my eeePC. Ubuntu boots without a problem, and runs fine. In order to get the wireless card recognized on the eee, I needed to download some packages. First I ran

```
sudo update-rc.d -f linux-restricted-modules-common remove
```

to remove any conflicting drivers. Then I simply ran ```
sudo apt-get update
```. It runs until it gets to "Reading package lists... 96%", then it seems to freeze up. This happened to me once before, and when I forcefully reboot the machine, it corrupted my file system. Is there some fix I can use to either (a) rescue it from this state, or (b) make sure this doesn't happen next time?

This is my first post, so I hope it is in the right section of the forum. If not, please direct me to the right place!

Thanks,

TJ

---

