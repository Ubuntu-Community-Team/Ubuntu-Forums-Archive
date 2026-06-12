---
title: "Kernel Downgrade"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by Sir Boss on 2008-08-11
I'm having problems with my wireless card, and I've read that it that problem was caused by a kernel upgrade.  I'd like to download to an older kernel version, 2.6.24-11, and try downgrading, but this is no longer found in the repository.  Where could I find this package?

---

### Post by logos34 on 2008-08-11
hmm, I don't remember any -11 hardy kernel.  Are you sure about that?  It's not listed anywhere [here.]("http://packages.ubuntu.com/")

---

### Post by Sir Boss on 2008-08-11
see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201180](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201180)
(bug 201180) maybe I'm misreading it?

---

### Post by logos34 on 2008-08-11
oh, -11 kernel in hardy alpha prerelease.  I don't think you want to roll back to that (assuming you can even find it).  

If you don't find a workaround by googling, this is just the situation where you might consider compiling a custom kernel with the requisite module(s) built-in.  

[http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

---

