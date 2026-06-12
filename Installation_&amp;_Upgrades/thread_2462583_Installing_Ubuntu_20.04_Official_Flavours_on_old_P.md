---
title: "Installing Ubuntu 20.04 Official Flavours on old PC's which use nvidia-304 drivers"
date: 2021-05-23
forum: Installation &amp; Upgrades
---

### Post by fljarvis on 2021-05-23
The 3 basic steps required are described in some detail in the post
"Installing Lubuntu 18.04.4 on a troublesome old PC",
[https://ubuntuforums.org,showthread.php?t=2440098](https://ubuntuforums.org,showthread.php?t=2440098)

The 1st step, downgrading Xorg,  is different for Ubuntu 20.04 flavours 
than for Ubuntu 18.04 flavours.

It is implemented as follows:

-collect the following bionic video modules in a directory
xserver-xorg-core_1.19.6-1ubuntu4.9_amd64.deb
xserver-xorg-legacy_1.19.6-1ubuntu4.9_amd64.deb
xserver-xorg-video-amdgpu_18.0.1-1_amd64.deb
xserver-xorg-video-ati_18.0.1-1_amd64.deb
xserver-xorg-video-fbdev_0.4.4-1build6_amd64.deb
xserver-xorg-video-intel_2.99.917+git20171229-1_amd64.deb
xserver-xorg-video-nouveau_1.0.15-2_amd64.deb
xserver-xorg-video-qxl_0.1.5-2build1_amd64.deb
xserver-xorg-video-radeon_18.0.1-1_amd64.deb
xserver-xorg-video-vesa_2.3.4-1build3_amd64.deb
xserver-xorg-video-vmware_13.2.1-1build1_amd64.deb

-replace the focal graphics from this directory with the
command,  sudo dpkg --install  xserver*.deb

************************************************************************

For the 2nd step, downgrading the Linux kernel,  I tested with
the 4.14.175 kernel from
[https://kernel.ubuntu.com/~kernel-ppa/mainline/v.4.14.175](https://kernel.ubuntu.com/~kernel-ppa/mainline/v.4.14.175)

There are newer 4.14 kernels than this one, but they are all
designated as being in a test state.  V4.14.175 is the latest
one designated as stable.

***********************************************************************
The 3rd step, installing the proprietary NVIDIA drivers, is the same,
as described in enigma9o7's thread, "nvidia won't install",
[https://ubuntuforums.org/showthread.php?t=2396263](https://ubuntuforums.org/showthread.php?t=2396263)


Len E.

---

### Post by TheFu on 2021-05-24
Tutorials belong in the Tutorials sub-forum.  This sub-forum is for asking for help.
Is there a question?

Additionally, most Ubuntu flavors for 18.04 have lost support since April and shouldn't be used.  Only the Gnome3 DE and Ubuntu Server has support until 2023.  Not Lubuntu.

---

### Post by fljarvis on 2021-05-24
Hi TheFu:

No:  I don't have a question regarding this thread.

In your administrator role, can you relocate this post
to the correct sub-forum ??

I don't know how to do that.

Thanks !

---

