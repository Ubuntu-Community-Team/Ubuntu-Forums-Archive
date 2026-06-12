---
title: "Where is kernel source?"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by bobbygr on 2005-07-28
I'm new to the Ubuntu distribution.  I need to compile some things that need the kernel source (VMWARE).  I installed the kernel source package.  I navigated to /usr/src and can't seem to find where the source is in this distribution.

Could someone tell me where the kernel source (header files, etc.) are stored?

Thanks very much....


Bob

---

### Post by az on 2005-07-28
To compile a kernel module, most of the time you do not need the full source, but only the kernel headers.  The package you need is linux-headers-2.6.18-5-386 (may be different if you installed the 686 or another kernel)

You will find it unpacked in /usr/src with the appropriate symlink in /lib/modules/2.6.10-5-386/build so that most configure scripts can find the linux-headers directory automagically.

The source package puts a tarball in /usr/src.  You have to unpack it, configure it and compile it to make use of it.  If you need the full source, you would have an easier time of using the linux-tree package instead of the kernel-source.  Search synaptic for the long description.

---

