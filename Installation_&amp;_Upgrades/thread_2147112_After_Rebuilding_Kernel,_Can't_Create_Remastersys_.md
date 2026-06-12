---
title: "After Rebuilding Kernel, Can't Create Remastersys Live System"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by forkenbrock on 2013-05-20
I'm having a problem with getting Remastersys to work on a live DVD or USB thumb drive.  I've been making live DVDs of my system for a little while with no issue.  Recently I followed the instructions below to update my kernel to 3.4, with an RT patch.

[http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel](http://askubuntu.com/questions/72964/how-can-i-install-a-realtime-kernel)

The kernel update and patching seemed to work fine (this was the first time I had rebuilt a kernel), but now Remastersys images give an error before finishing the boot process (with both DVD and thumb drive).  The error says:

[sda] No Caching mode page present
[sda] Assuming drive cache: write through

BusyBox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4.1) built-in shell (ash)

(initramfs) aufs mount failed



I found these two threads.  The first didn't work.  The second says something about recompiling the kernel with aufs enabled.  I'm not sure how to do that in the context of the instructions I followed above.  Also, this issue was with kernel 2.6 and the thread says it should be fixed in the future (there was no problem with the 11.04 version I started with on the main download site).

[http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning](http://askubuntu.com/questions/167343/what-is-a-asking-for-cache-data-failed-warning)
[http://ubuntuforums.org/showthread.php?t=1603807&page=3](http://ubuntuforums.org/showthread.php?t=1603807&page=3)


Your help in figuring out how to fix this is appreciated.

---

### Post by forkenbrock on 2013-05-22
Can anyone help with this?

---

