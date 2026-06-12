---
title: "Installation of Marvell Yukon driver"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by markusan on 2011-02-11
[B]I originally posted this message in the beginners forum, but thought it was better placed here. I will remove the other thread once this issue has been resolved.
[/B]             
                                                                I am trying to install the Marvell Yukon driver for the 88E8056 LAN port and I have a kernel header mismatch. I am using Ubuntu 10.04 but thinking of switching to Ubuntu 10.10.

I have seen very similar problems on the forums, but not the exact versions so I was wondering if anyone has a good solution. The installation proceeds to the point where it checks the kernel header version.

Check kernel header version (kernel:2.6.32 != Header:2.6.32.15+drm33). [failed]

The installation script gives a list of possible solutions. One of them is to overwrite current include/version.h with the include/version.h currently running.

At the end of the installation the following is given:
Your kernel versionL2.6.32-24-generic
Your header version:2.6.32.15+drm33.5


Does anyone have a solution for my problem? I am very new to Linux in general and especially Ubuntu, so I do not feel comfortable tampering with the kernel. Any help would be greatly appreciated! :smile:

---

### Post by foresto on 2011-10-26
If you're using Ubuntu 11.04 (Natty), the package I built for this driver ought to make your life easier.  Here's my announcement:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

### Post by MAFoElffen on 2011-10-27
> **markusan said:**
> [B]I originally posted this message in the beginners forum, but thought it was better placed here. I will remove the other thread once this issue has been resolved.
[/B]             
                                                                I am trying to install the Marvell Yukon driver for the 88E8056 LAN port and I have a kernel header mismatch. I am using Ubuntu 10.04 but thinking of switching to Ubuntu 10.10.

I have seen very similar problems on the forums, but not the exact versions so I was wondering if anyone has a good solution. The installation proceeds to the point where it checks the kernel header version.

Check kernel header version (kernel:2.6.32 != Header:2.6.32.15+drm33). [failed]

The installation script gives a list of possible solutions. One of them is to overwrite current include/version.h with the include/version.h currently running.

At the end of the installation the following is given:
Your kernel versionL2.6.32-24-generic
Your header version:2.6.32.15+drm33.5


Does anyone have a solution for my problem? I am very new to Linux in general and especially Ubuntu, so I do not feel comfortable tampering with the kernel. Any help would be greatly appreciated! :smile:
Try this
```

sudo aptitude install linux-headers-"uname -r"

```
That wil install the header file for whatever kersion version you are currently running on...

---

