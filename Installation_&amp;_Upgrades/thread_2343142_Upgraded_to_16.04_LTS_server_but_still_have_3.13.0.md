---
title: "Upgraded to 16.04 LTS server but still have 3.13.0-101 kernel"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by WolfeWorks on 2016-11-13
I ran *do-release-upgrade* on one of my 14.04 LTS servers, got no errors and it runs, but I notice that it still has the 3.13.0-101 kernel (and only that version, all earlier kernels and all header files were deleted). A 16.04 LTS server instance on AWS has kernel version 4.4.0-47. Did something go wrong on my local server upgrade? How do I get the v4 kernel, or is that not a problem?

---

### Post by pme 72 on 2016-11-20
I ran into the same output when I upgraded Xubuntu14.04 LTS to Xubuntu 16.04 on my desktop. My issue was resolved by taking deadflowr's recommendation in this thread:

"https://ubuntuforums.org/showthread.php?t=2326507"

```
sudo apt update
sudo apt install linux-image-generic linux-headers-generic
```

---

