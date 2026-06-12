---
title: "How to compile an installed image for use with pxe boot"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by manuel2808 on 2011-03-11
[SIZE=3]Hello All;):P[/SIZE]

I'm working on a VDI project, and I’m in charge to create the basic operating system image to access to virtual desktops for End users clients.

I have created a basic image using Ubuntu server 10.10 using the miniIso install.
I have installed the citrix receiver, and everything is working well.

Now I want to create a PXE bootable image from my installation.

All what I have seen is a tuto to use diskless image, using NFS share, but this is not really what I want.

I would like the image will be downloaded into memory, so once the workstation is running we don’t need any extra networked resources (NFS server to store root fs by example).

I saw in the ThinStation project that this works, but the network kernel used actually does not include some Wireless drivers, and therefore is not usable for laptops.

So If someone knows how to...;)

Cheers

---

