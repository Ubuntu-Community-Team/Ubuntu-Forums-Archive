---
title: "Upgrade 10.04 to 10.10 fails: Package xserver-xorg-video-nouveau broken Depends"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by c901906 on 2011-01-26
Upgrade 10.04 to 10.10 fails: Package xserver-xorg-video-nouveau broken Depends 

Upgrading from 10.04 to 10.10 failed on a Dell 530 with NVidia graphics. Log entries below.

This is too much information: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993)

I'm hesitant because it sounds like I may accidentally disable my video.

Any better understanding of the problem or should I just wait? 

TIA!
Adam.

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

This log file entry from "/var/log/dist-upgrade/apt.log" appears to be the problem:

Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 81 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0

---

### Post by zvacet on 2011-01-29
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

```
sudo dpkg --configure -a
```

---

### Post by c901906 on 2011-02-02
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get dist-upgrade
```

```
sudo dpkg --configure -a
```

zvacet,

Thank you for responding. I still get the error (below). More people are posting to 614993 so I will just wait for it to sort itself out. 

Thanks again!
Adam.

Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 81 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0

---

### Post by h.aling on 2011-02-12
I had the same error and fixed it by removing xserver-xorg-video-nouveau prior to the dist upgrade:

```
sudo apt-get purge xserver-xorg-video-nouveau
```

---

### Post by c901906 on 2011-02-17
> **h.aling said:**
> I had the same error and fixed it by removing xserver-xorg-video-nouveau prior to the dist upgrade:

```
sudo apt-get purge xserver-xorg-video-nouveau
```

Thanks for responding.

Yes, that worked for me. I have a dual monitor setup on my nVidia card and was afraid I might break it. The upgrade worked flawlessly after I removed xserver-xorg-video-nouveau.

---

