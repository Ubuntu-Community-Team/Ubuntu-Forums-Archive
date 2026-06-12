---
title: "nvidia upgrade problem with 6.06 on amd64"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by marcosw on 2006-11-09
Last night I upgraded a couple of packages on my amd64 system running Ubuntu 6.06 LTS after synaptic told me new versions were available.  Here is the history:

Commit Log for Tue Nov  7 19:29:27 2006

Upgraded the following packages:
linux-restricted-modules-2.6.15-27-amd64-generic (2.6.15.11-5) to 2.6.15.12-1
linux-restricted-modules-common (2.6.15.11-5) to 2.6.15.12-1


Today I rebooted my computer but X refused to start and gave me the message:

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but
this X module has the version 1.0-8762.  Please make sure that the kernel
module and all NVIDIA driver components have the same version.

I assume this is related to the update of the linux-restricted-modules that happened the night before.  

I've generated the nvidia-bug-report.log file and have a /var/log/Xorg.0.log file, but they are too long to append to this message but can post portions if someone tells me what is relevant.

Any suggestions how to fix this (short of reinstalling the OS, which I'm not considering, yet)?

marcos

---

### Post by angkor on 2006-11-09
Try removing nvidia-glx and reinstall it with:

```
sudo aptitude install linux-restricted-modules-`uname -r` nvidia-glx
```

I had the same problem once and this worked for me.

---

### Post by suxen on 2006-11-13
Yep, worked for me as well.

---

