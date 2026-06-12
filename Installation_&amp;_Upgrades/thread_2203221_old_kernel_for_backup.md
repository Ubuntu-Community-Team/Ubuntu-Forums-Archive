---
title: "old kernel for backup"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by omkarkalbag on 2014-02-02
Hi,

This is my very first post on this forum!

First some details abt my system:
I started using Ubuntu since 12.Jan.14 and am a big fan of Ubuntu now.
My system runs on Ubuntu 12.04.4 LTS; Kernel: 3.2.58 (old) 3.4.0 (new)
H/w details: 64-bit Arch, 2GB Ram, 5GB SWAP Mem, AMD 3200+ 64bit Dual Core.

After doing extensive research on how to update the kernel, I managed to successfully upgrade it from 3.2.58 to 3.4.0
Following the instructions of the blogpost, I also managed to successfully remove old kernel from the system using ubuntu tweak.

But after reading more on stability issues, I realised that it is important to have older kernels in case of fallback or unstability of latest kernel.

But in my case, I have already removed old kernel 3.2.xx

Now I want to download older version 3.2.xx but run the latest 3.4.0 only.
I get the GRUB Screen on boot as I have dual boot with Win XP (Which I use only once a month) and Ub 12.04
**Now my Q is**: Will ubuntu detect and run the latest kernel or the last installed kernel? Do I have to update any thing related to kernel (System updater shows nothing to update after kernel upgrade, I also checked driver compatibility, no issues)
Will the GRUB show previous kernel? and In case of instability/crash/freeze/driver incompatibility issues, how do I use older version of kernel?

Although I am not a absolute beginner, I am not so experienced in Linux too.
Looking from help from experienced users!!
Thnx in advance.):P

---

### Post by grahammechanical on 2014-02-02
You can run

```
sudo update-grub
```

and see what kernels are available. You may have more than one version of Linux kernel 3.4.0. In which case one of those kernels can act as fallback kernel. Provided it works. If an newer kernel works it is unlikely to suddenly stop working. In the case of an upgrade to a newer kernel that does not work so well, then we can boot into a previous kernel that did work. That is the idea behind keeping at least one previous kernel.

You may get an upgrade to a newer version of Linux 3.4.0 in a few weeks/months. Ubuntu 12.04.4 comes out in a few weeks that most likely will contain a newer kernel than 3.4. And so the present 3.4 kernel will become your fallback.

For reference, Ubuntu Trusty Tahr (14.04 to be) has Linux kernel 3.13.0. So, things progress.

Regards.

---

### Post by tgalati4 on 2014-02-02
No need to worry about a problem that does not exist.  After a year of updates, you will have a handful of 3.4.XX kernels and each of those can be a backup kernel to boot into.  It's a lot of effort and little gain putting an old, major-release kernel on your system.

---

