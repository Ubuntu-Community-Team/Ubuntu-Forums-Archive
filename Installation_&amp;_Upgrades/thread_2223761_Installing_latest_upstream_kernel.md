---
title: "Installing latest upstream kernel"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by Katzwinkel on 2014-05-12
Hi,
After sending a Bug report about a [WiFi-driver Issue]("http://ubuntuforums.org/showthread.php?t=2220855") I was told to test the newest upstrem kernel. I was told to download and install the latest v3.15 kernel[0].

But... How do I find the correct Kernel? 
At the [stated website ]("http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D") I can find several kernels with the version--Nr v3.15:
 v3.15-rc5-utopic
 v3.15-rc4-utopic
 v3.15-rc3-utopic
 v3.15-rc2-trusty
 v3.15-rc2-trusty
 v3.15-rc1-trusty

Should I just take the newest one? Does it matter that I use Xubuntu and not Ubuntu?

I run Xubuntu (apparently based on Ubuntu 14.04)
my kernel at the moment: 3.13.0-24-generic (#47-Ubuntu SMP Fri May 2 23:31:42 UTC 2014)
GCC version: 4.8 (i686-linux-gnu)
Xorg version: 1.15.1 (16 April 2014  01:40:08PM)

thanks all!

---

### Post by deadflowr on 2014-05-12
Quick Howto for you
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by pqwoerituytrueiwoq on 2014-05-12
This can help you, if you want something simple 
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
on step 4 use this command
```
KernelUpdateChecker -r utopic
```

---

