---
title: "Memory Stick"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by Hunter826242 on 2008-04-17
My laptop is a Sony Vaio VGN-FS750, with built-in Magic Gate Memory stick Pro Duo reader.
I installed Xubuntu and the reader wont read the stick. 
     How do i get it to work???

            :guitar:

---

### Post by warp99 on 2008-04-17
What version of xubuntu did you install? If it's Gutsy 7.10 there is a problem with the kernel modules:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/48987](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/48987)

You may need a kernel or module update. Open a terminal and issue the following:
```
uname -r 
```
then post the results to this thread.

---

