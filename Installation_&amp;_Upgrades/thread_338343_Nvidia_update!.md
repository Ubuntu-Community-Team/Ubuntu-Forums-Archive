---
title: "Nvidia update!"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by moonliter on 2007-01-14
when I want to update nvidia-glx from terminal I am getting this:

```
The following NEW packages will be installed:
  linux-image-2.6.17-10-386 linux-restricted-modules-2.6.17-10-386 nvidia-glx
0 upgraded, 3 newly installed, 0 to remove and 2 not upgraded.

```

Why is this happening? when I type  uname -r shows me
2.6.17-10-generic. I didn't have this problem before. It start to happening when I  uninstalled nvidia-glx driver with this command:
```
sudo apt-get --purge remove nvidia-glx linux-restricted-modules-`uname -r` linux-restricted-modules-common
``` 

I had to do this because newest updated nvidia-driver gave me troubles with X,so I try to back on  before driver.So how to fix problem with installing nvidia-glx without 386 image and also I have problems with X.I tryed suggested site ```
http://albertomilone.com/latest_nvidia_udsf_edgy.html
```
and used both metods but didn't help me

---

### Post by moonliter on 2007-01-15
anyone?

---

