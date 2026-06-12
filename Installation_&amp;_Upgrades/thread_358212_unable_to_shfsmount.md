---
title: "unable to shfsmount"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by grado on 2007-02-10
hi,

When I try to mount a remote filesystem on my machine over ssh I get this error.

shfsmount: shfs filesystem not supported by the kernel

My machine:
Linux  2.6.17-11-386 #2 Thu Feb 1 19:50:13 UTC 2007 i686 GNU/Linux
remote machine:
SunOS 5.6 Generic_105181-28 sun4u sparc

Any idea why I am getting this?

Thanks!

---

### Post by Perkins on 2007-04-18
You are missing the shfs kernel module.

Install the shfs-source package and all its dependencies.
Install gcc if you don't have it already
Install the linux-headers package that matches your kernel version.

the shfs-source package should have forced installation of module-assistant, so now:

sudo module-assistant build shfs
sudo module-assistant install shfs
sudo shutdown -r now

That should get it working for you.

---

### Post by arnaldo on 2007-05-08
This should work, but it doesn't in feisty.  It looks like some data structures in the kernel were changed, and shfs-source was not upgraded to a compatible version.

---

