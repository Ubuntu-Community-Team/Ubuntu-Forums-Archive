---
title: "Choppy video after installing NVIDIA drivers"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by MRAB54 on 2007-12-16
Hello,

I just recently installed a custom kernel, 2.6.22.9.  On my generic install of 7.10, I was able to just go into restricted modules and install nvidia drivers that way no problem.  Restricted modules does not want to work w/ my custom kernel so I installed nvidia driver 100.14.19 manually.  

Resolution and everything looks fine, problem is, none of the desktop visuals like wobbly windows work, browser scrolling is very choppy etc.  

Everything seems to be loading very snappy otherwise, when I had just the default video before installing drivers, scrolling etc was normal and smooth.

Any help would be great.

---

### Post by MRAB54 on 2007-12-16
Figured out my problem.  Did not even think to uninstall the "restricted driver" through my other kernel before I installed these new drivers which was conflicting and doing some weird stuff.

I uninstalled all drivers that I could and reinstalled and it works fine.

---

