---
title: "[SOLVED] How to manually install new linux kernel for 7.10"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by vames on 2008-08-07
Hi guys, can someone tell me what is the terminal code to download and install the new kernel upgrade? I just installed 7.10

---

### Post by zvacet on 2008-08-07
System>admin>software sources>check all under Ubuntu software tab (exept source) and under updates tab.Reload.

```
sudo apt-get update && sudo apt-get upgrade
```

That is if you want latest Gutsy kernel.If you want latest kernel read [this.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

### Post by vames on 2008-08-07
Thanks man, it works. :guitar:

---

