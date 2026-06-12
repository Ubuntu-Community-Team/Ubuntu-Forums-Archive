---
title: "nvidia CUDA driver"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by Grafens on 2011-12-15
I installed the nvidia driver from nvidia's website in order to use cuda which worked. But later when doing a routine kernel header upgrade the computer hung on the splash screen and the only way to get things working was to boot into a previous linux kernel through grub.
My questions are
Does ubuntu's generic/proprietary nividia drivers support cuda, if so what's the latest version number.

If I have to use nvidia(cuda) driver from their website will I need to reinstall it every time the kernel is updated.

I'm using ubuntu11.04

Thanks

---

### Post by MAFoElffen on 2011-12-15
> **Grafens said:**
> I installed the nvidia driver from nvidia's website in order to use cuda which worked. But later when doing a routine kernel header upgrade the computer hung on the splash screen and the only way to get things working was to boot into a previous linux kernel through grub.
My questions are
Does ubuntu's generic/proprietary nividia drivers support cuda, if so what's the latest version number.

If I have to use nvidia(cuda) driver from their website will I need to reinstall it every time the kernel is updated.

I'm using ubuntu11.04

Thanks
As far as I have wished to look into it and my understanding of that is... That the packaged nVidia drivers are the binaries made into a packaged form.  A few things are taken out (nvidia-installer for one) in order to do that.  I know they realistically and legaly can't change the code, as it is still "proprietary."

As far as the binaries vs. a kernel... Like with some other packages, have you reinstalled that driver on the current kernel?  That way the binaries compile on that kernel. That's what I usually do.... and that's what I had to do a couple weeks ago on a kernel change.

EDIT-- That seems to be the pro & con of binary or package.  The binaries, after install stay static/unchanged, unless you manually change or update them. Other changes in system may drift from... Or a binary install may be unaffected, because of that buffer. Packaged drivers are because they are connected are going to get updated. (good or bad).  Each one seems to balance out.

---

### Post by efflandt on 2011-12-15
Not sure what you are trying to do that you need drivers from nvidia website instead of Ubuntu packages of same drivers.  If you install drivers from nvidia website, you may need to do something about blocking nouveau, and possibly reinstall nvidia drivers after kernel updates.  I have never done that, so not sure how to reverse that if you did.

If you install Ubuntu specific packages of same drivers (typically through **Additional Drivers**), video drivers and related kernel modules are coordinated and matched during any updates of either.

If you need newer nvidia-current than is current by default, add x-swat to your repositories:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Then with **Update Manager**, "Check" for updates and install them.  x-swat nvidia drivers are 290.10

---

