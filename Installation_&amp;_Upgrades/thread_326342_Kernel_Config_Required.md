---
title: "Kernel Config Required"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by Grønn Demon on 2006-12-27
I'd like to compile a kernel module that requires a kernel .config. The package linux-headers is not enough because it lacks the kernel config.
Unfortunately the default kernel package does not support /proc/config either.

So my idea was to build a custom kernel with my own .config file.
I have of course read [this howto on how to compile a custom kernel]("https://help.ubuntu.com/community/Kernel/Compile").
Now I'm even more confused about what's the correct way to build a new kernel under (X)Ubuntu. The package manager recommended using "make-kpkg kernel_image".

I have compiled a kernel before, it's just that everything seems so different under (X)Ubuntu.
Also, I'd of course like to always have the newest kernel version - maybe there actually is a way to use linux-headers?
Oh, and I want to use the restricted-modules package.

Any help is highly appreciated.

---

### Post by az on 2006-12-27
> **Grønn Demon said:**
> I'd like to compile a kernel module that requires a kernel .config. The package linux-headers is not enough because it lacks the kernel config.
Unfortunately the default kernel package does not support /proc/config either..

The config for your running kernel is in /boot


> **Grønn Demon said:**
> 
So my idea was to build a custom kernel with my own .config file.
I have of course read [this howto on how to compile a custom kernel]("https://help.ubuntu.com/community/Kernel/Compile").
Now I'm even more confused about what's the correct way to build a new kernel under (X)Ubuntu. The package manager recommended using "make-kpkg kernel_image"..

You should not have to recompile the kernel to just build a module. What exactly to you want to build?

> **Grønn Demon said:**
> 
I have compiled a kernel before, it's just that everything seems so different under (X)Ubuntu..

Well, Ubuntu uses more recent versions of some of the basic tools.  It is also simpler to make your kernel into a package so that it can be easily and safely installed and removed.

> **Grønn Demon said:**
> 
Also, I'd of course like to always have the newest kernel version - maybe there actually is a way to use linux-headers?.

If you are going to recompile the kernel, there is no way you are going to always have the most recent version.  Just find a way to use the linux-headers.

---

