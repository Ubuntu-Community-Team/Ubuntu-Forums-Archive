---
title: "linux image naming confusion"
date: 2009-08-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-16
Hi!

Let's see:

```
$ sudo aptitude -V search linux | grep image
p   linux-backports-modules-karmic- - Backported drivers for server kernel image
p   linux-image                     - Generic Linux kernel image.
v   linux-image-2.6                 -
p   linux-image-2.6.31-1-rt         - Linux kernel image for version 2.6.31 on I
i   linux-image-2.6.31-3-generic    - Linux kernel image for version 2.6.31 on x
c   linux-image-2.6.31-4-generic    - Linux kernel image for version 2.6.31 on x
i A linux-image-2.6.31-5-generic    - Linux kernel image for version 2.6.31 on x
p   linux-image-2.6.31-5-server     - Linux kernel image for version 2.6.31 on x
p   linux-image-2.6.31-5-virtual    - Linux kernel image for version 2.6.31 on x
p   linux-image-2.6.31-6-generic    - Linux kernel image for version 2.6.31 on x
p   linux-image-2.6.31-6-server     - Linux kernel image for version 2.6.31 on x
p   linux-image-2.6.31-6-virtual    - Linux kernel image for version 2.6.31 on x
i   linux-image-generic             - Generic Linux kernel image
p   linux-image-rt                  - Rt Linux kernel image
p   linux-image-server              - Linux kernel image on Server Equipment.
p   linux-image-virtual             - Linux kernel image for virtual machines

```You see, I have  linux-image-2.6.31-5-generic installed, but  linux-image-2.6.31-6-generic exists. As far as these packages have different names, there is nothing to upgrade:

```
$ sudo aptitude -v -P safe-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?]
```The question: what must I do to make new kernels included (hooked) in upgrade?

Small related question: what does 'new' status mean in 'update' output? Is it just informative, and it is safe to 'forget-new'?

---

### Post by taavikko on 2009-08-16
Just wait for the linux-meta (linux-image-generic) package to be upgraded which then depends on the latest kernel.

If cannot wait, just manually install the latest kernel and headers.

ps. aptitude doesn't require sudo for all the actions..

---

### Post by ilna on 2009-08-16
> **taavikko said:**
> Just wait for the linux-meta (linux-image-generic) package to be upgraded which then depends on the latest kernel.Aha, I see, thanks.
> **taavikko said:**
> ps. aptitude doesn't require sudo for all the actions..Well, just arrow-up was used in konsole :-)

---

