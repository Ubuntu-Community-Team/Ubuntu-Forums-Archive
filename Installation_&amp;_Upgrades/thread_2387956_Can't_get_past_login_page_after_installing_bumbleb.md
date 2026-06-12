---
title: "Can't get past login page after installing bumblebee/tensorflow/nvidia"
date: 2018-03-26
forum: Installation &amp; Upgrades
---

### Post by akshattripathi on 2018-03-26
I installed (or tried to) cuDNN, bumblebee, tensorflow, cuda and after I reboot, I cannot get past the login page. I tried a few solutions online:
Went to recovery mode
Dropped to root shell promt

Entered:
sudo apt-get purge nvidia*Got:
E: Could not create temporary file for /var/lib/apt/extended_states - mkstemp (
0: Read-only file system)
E: Failed to write temporary StateFile /var/lib/apt/extended_states
W: Could not open file '/var/log/apt/term.log' -- OpenLog (30: Read-only file system)
E: Sub-process /usr/bin/dpkg returned an error code (2)
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - pkgDPkgPM::Go (30: Read-only file system)What do I do?

---

### Post by ubfan1 on 2018-03-27
Try checking your filesystem, errors can force it to mount read-only.  Usually, install the Nvidia drivers first, and when those are working, install the cuda .deb file from Intel, then the cuda package from the Ubuntu repositories.

---

