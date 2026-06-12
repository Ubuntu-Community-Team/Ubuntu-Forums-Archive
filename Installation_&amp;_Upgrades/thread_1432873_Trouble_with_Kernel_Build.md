---
title: "Trouble with Kernel Build"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by danben on 2010-03-18
Hi,

I just bought an HP Envy 15, and my first order of business is to try to get some version of Linux up and running.  I started by creating a USB boot device with Unetbootin using the 9.10 ISO.  This was functional, but there were a few hardware issues (as detailed at [http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15](http://www.chizang.net/alex/blog/2009/12/21/linux-on-the-hp-envy-15)) such as overheating and no mouse button functionality.

Still running off the USB drive, I followed the directions at [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild) to build the latest kernel.  This mostly went smoothly - I hit one snag toward the end when it couldn't find the UTS release version, but I got around that by appending the contents of /include/linux/utsrelease.h to /include/linux/version.h.

After rebooting, however, the USB drive is no longer recognized by the BIOS as a bootable device.  Was I incorrect in assuming that I would be able to do this?  I can install Ubuntu to the hard drive if I absolutely need to, but I was hoping to get a suitable working version running first.

Thanks,
Dan

---

### Post by tom4everitt on 2010-03-18
Partly incorrect, yes. The live cd that you have on your usb differs on a few points from a normally installed system. 

Easiest is probably to install ubuntu from one usb to another (or from a cd to a usb), then you will have normal system on the usb that you can test changes on.

Let me also tip you about this link:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

It contains the latest kernels built for ubuntu, saves some work :)

---

### Post by danben on 2010-03-18
Hi Tom,

Thanks for the quick response.  Next chance I get, I'll try the USB-to-USB install.

The patch in question can be seen at [http://patchwork.kernel.org/patch/67335/](http://patchwork.kernel.org/patch/67335/) ; is there any way for me to tell if it has made it into the latest kernel build (v2.6.34-rc1, in the link you sent)?  I tried searching for "synaptics" in the release notes, but it might have been included in an earlier release, or maybe it was noted differently - I don't know the procedure for such things.

Dan

---

### Post by tom4everitt on 2010-03-18
I must admit I have no idea on how to tell if the patch is built in. I'm sure someone else do though :)

---

