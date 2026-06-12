---
title: "KMS &amp; Intel 855 (i915) &amp; Kernel 2.6.30-9 hang"
date: 2009-06-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by handaxe on 2009-06-16
xserver-xorg-core: 2:1.6.1.901-2ubuntu1
 xserver-xorg-intel: 2:2.7.99.901+git20090615.3da549f5-0ubuntu0sarvatt
kernel: 2.6.30-9-generic
Display controller: Intel Corporation 82852/855GM Integrated Graphics Device 

 Enabling KMS via either "options i915 modeset=1" in  /etc/modprobe.d/i915-kms.conf or "modprobe i915 modeset=1, /etc/init.d/gdm start" leads to a system-wide freeze (hard-off or SysReq B (only that key works)). Mode change apparent in console. Testing shows that hang begins at X startup. No debugging obtained yet locally or by remote (many tries) and nothing entered in logs, but binary and misplaced text is injected into "messages" and other logs. **Works fine without KMS**.


 **NOTE: kernel: 2.6.30-8-generic does not present this problem for me.**


Anyone out there with Intel 855 and running KMS under kernel 2.6.30-9-generic?


If you do test and find problems please refer to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387978](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/387978)


Tnx

---

