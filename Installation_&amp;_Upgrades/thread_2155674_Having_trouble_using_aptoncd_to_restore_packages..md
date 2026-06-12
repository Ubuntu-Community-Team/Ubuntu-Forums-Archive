---
title: "Having trouble using aptoncd to restore packages."
date: 2013-06-19
forum: Installation &amp; Upgrades
---

### Post by ohmegatron on 2013-06-19
I recently upgraded from mint 14 to mint 15, and made an iso in aptoncd. I followed the instructions in this thread [http://ubuntuforums.org/showthread.php?t=1012128](http://ubuntuforums.org/showthread.php?t=1012128) and it seemed to be working, but then it did this:

 (there were a lot more of these .deb files.)
 /var/cache/apt/archives/libexpat1_2.1.0-1ubuntu1_i386.deb
 /var/cache/apt/archives/libffi6_3.0.11-2_i386.deb
 shared-mime-info
 install-info
 mintsystem
 desktop-file-utils
 gconf2
Processing was halted because there were too many errors.

Now when I try to sudo apt-get update, terminal produces this error:
apt-get: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.17' not found (required by /usr/lib/x86_64-linux-gnu/libstdc++.so.6)
Also when I try to install any package.
Is there anything I can do other than re-install?

---

