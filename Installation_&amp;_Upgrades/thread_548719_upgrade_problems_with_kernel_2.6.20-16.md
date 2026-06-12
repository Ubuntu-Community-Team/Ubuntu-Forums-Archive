---
title: "upgrade problems with kernel 2.6.20-16"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by MattAd on 2007-09-11
I seem to be running into some problems running apt-get to upgrade my kernel to 2.6.20-16. In the middle of running apt-get upgrade, it produces the following:

```
Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.29) ...
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured

```

I'm not really sure what exactly the I/O error is that it keeps running into, but when I attempted to start using the new kernel, fsck starts running during startup. I've since switched back to my old kernel, but would like to know how to fix this, because it keeps coming up and slowing my laptop down every time I use apt to install something else.

---

### Post by dcstar on 2007-09-12
> **MattAd said:**
> I seem to be running into some problems running apt-get to upgrade my kernel to 2.6.20-16. In the middle of running apt-get upgrade, it produces the following:

```
Setting up linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.29) ...
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
Bus error (core dumped)
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured

```I'm not really sure what exactly the I/O error is that it keeps running into, but when I attempted to start using the new kernel, fsck starts running during startup. I've since switched back to my old kernel, but would like to know how to fix this, because it keeps coming up and slowing my laptop down every time I use apt to install something else.

And how much space do you have left in your root partition?

---

### Post by MattAd on 2007-09-12
> **dcstar said:**
> And how much space do you have left in your root partition?

Several gigabytes, I believe. I shouldn't be running out of space, although I do occasionally have errors that need to be fixed by fsck. Maybe this is part of a larger problem with my hard drive?

---

