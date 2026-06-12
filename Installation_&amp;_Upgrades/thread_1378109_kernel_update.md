---
title: "kernel update"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by xtracool_protik on 2010-01-11
Hi,
 I've just updated to 9.10, as it seems my webcam(Dell Inspiron 1525 Omnivision webcam) is not working anymore.
 So I read about a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462336]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462336"). Which advices that I should get kernel 2.6.32.2 to solve webcam issue.
 However at same time Ubuntu disclaimer about compiling custom kernels [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile"). says I should not compile custom kernels.
 I'm confused cause 
 1. both links are from official Ubuntu sources.
 2. If I compile and use new kernel do I still get updates for that kernel?

Thank you

---

### Post by xtracool_protik on 2010-01-12
Bump

---

### Post by xtracool_protik on 2010-01-12
I'm getting impatient :( guess I'll just upgrade it

---

### Post by slakkie on 2010-01-13
You can manually compile it and create a package out of it, then you should be able to upgrade if a newer version is released on the repo's.

---

### Post by Linuxforall on 2010-01-13
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/)

Use Ubuntu's compiled kernel and you will have no issues.

---

### Post by wlraider70 on 2010-01-13
is there any benefit to compiling the kernel myself?

---

### Post by xtracool_protik on 2010-01-13
Thanks a lot Linuxforall,
 One more issue if u don't mind, can I add that ppa for latest kernel developments?

---

