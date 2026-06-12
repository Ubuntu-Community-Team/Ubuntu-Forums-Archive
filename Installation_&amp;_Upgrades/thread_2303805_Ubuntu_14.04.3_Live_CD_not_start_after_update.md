---
title: "Ubuntu 14.04.3 Live CD not start after update"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by pol2095 on 2015-11-21
Hello,

I tried to update Ubuntu 14.04.3 LTS Live CD via the "Update Manager", download and installation went well, he asked me to restart, then I restart Ubuntu I have this message "initramfs unable to find a medium containing a live file system" and it doesn't start.

Thanks

---

### Post by ubfan1 on 2015-11-22
I assume you had set up the live media with persistence, otherwise, updates are pointless.  How big was your persistence file?  The 1G minimum persistence file would be pretty quickly filled up with updates.  Of course, not all the updates will be seen, like the kernels -- the way the live media starts prevents actually using an updated kernel sitting in the persistence file.  Not sure what could cause your error.  If you start grub, and edit out the word "persistent" on the kernel boot line (starting with vmlinuz I think), can you boot? (Or rename the casper-rw file so it's not found).  You can always make another casper-rw file bigger than the first if filling it up's the problem.

---

