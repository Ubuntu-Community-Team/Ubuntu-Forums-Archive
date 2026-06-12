---
title: "Custom Kernel 2.6.19 nVDIA driver installation problem"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by rpradeep on 2006-12-09
Yesterday i was able to successfully compile and install the 2.6.19 kernel from ubuntu kernel source 2.6.19-7.11.

But when i try to install the nvidia drivers it compile to 100% of kernel modules but says it cannot install.

When i go through the nvidia-installer.log it says error about config file and ask to make oldconfig and make prepare.. but did not help.

Any Idea please..?

---

### Post by rpradeep on 2007-01-02
I have solved this problem. The thing is a file is missing in kernel/linux/config.conf (if i remember correctly) but a file is available as configfs.conf so i make a link to configfs.conf to config.conf and installation go smoothly.

---

