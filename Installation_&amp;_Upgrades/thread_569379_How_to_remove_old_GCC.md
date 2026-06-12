---
title: "How to remove old GCC?"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by beyonddc on 2007-10-07
Hi all, I just compiled and installed the latest version of GCC 4.2.1.
In general, do you need to uninstall the previous version of GCC after the new version was being installed?

If so, how do you uninstall old GCC?

Thanks

---

### Post by taurus on 2007-10-07
How did you install the older version of GCC?  If you used synaptic/apt-get/aptitude, then uninstall it with the same method.

Otherwise, you can always try

```
sudo apt-get remove build-essential
```

---

### Post by beyonddc on 2007-10-07
I installed the latest GCC by downloading the tarball file from GCC website and then..

1. ./configure
2. make
3. make install

---

### Post by Slim Backwater on 2007-10-07
> **taurus said:**
> How did you install the **OLD**er version of GCC?  
...

Essentially he's saying to remove the old version using the same method that you used to install it.  If it was via apt-get then use apt-get to remove it.  If it was installed with make install, try make remove.

._.

---

