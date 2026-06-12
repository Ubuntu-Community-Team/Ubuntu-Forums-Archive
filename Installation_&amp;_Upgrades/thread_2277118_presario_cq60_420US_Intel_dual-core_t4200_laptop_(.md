---
title: "presario cq60 420US Intel dual-core t4200 laptop (ubuntu14.04 amd64)"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by pmcfortifi on 2015-05-06
I am looking for information on the kernel.  After running the command sudo ls -l version in /proc/ I get the output "-r--r--r-- 1 root root 0 May  6 15:14 version"
Does this mean I need root access?  How can I get more information on the kernel? I need a comparison between the standard kernel and how it was compiled on my system when I installed ubuntuamd64 from usb-boot.

---

### Post by ubfan1 on 2015-05-06
Well, ls shows it exists,so to examine the contents use
cat /proc/version

---

