---
title: "Ubuntu 14.04 loop installation cannot boot"
date: 2014-05-14
forum: Installation &amp; Upgrades
---

### Post by noorez on 2014-05-14
If Ubuntu 13.10 is installed in a virtual disk image (wubi style), and booted via the loop device, it works fine, however, this fails in Ubuntu 14.04. After some googling, the workaround is to set the 'ro' kernel flag to 'rw' on the loop installation. I was a bit curious about this so in both cases, I dropped to a root shell in the recovery mode and tried the following:

mount -o remount,rw /host/ubuntu/disk/root.disk 
this works in Ubuntu 13.10 loop installation but fails in 14.04. The error received is that the loop device is write-protected. 

Why would this behaviour change like this?

---

