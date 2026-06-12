---
title: "Does Lucid implement the latest intel vga drivers?"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sonnet on 2010-04-22
I just wnat to ask if the Ubuntu devs patched the .32 kernel with intel drivers from .33 as it seems offer major improvements as stated here and confirmed by other users:
[http://intellinuxgraphics.org/2010Q1.html](http://intellinuxgraphics.org/2010Q1.html)
[I]xf86-video-intel 2.11.0:
* Support for new DRI2 APIs, allowing page flipping to occur for swaps that are full-screen and not rotated. 
mesa 7.8:
* i965 driver adds support for the following extensions: GL_EXT_draw_buffers2, GL_ARB_fragment_coord_conventions, GL_APPLE_object_purgeable. 
* i915 driver adds support for the following extension: GL_APPLE_object_purgeable. 
* Much improved support for EGL in Mesa. 
kernel 2.6.33:
* Page flipping (reduces memory bandwidth consumption for full screen apps). < br> * Improved tiled rendering support (execbuf2 interface which allows for finer grained fence register management, increasing performance). 
* Improved support for Intel® HD Graphics (in Intel® 2010 Core i7/i5/i3 Processor Series).
major fixes against the last release[/I]

---

### Post by clhsharky on 2010-04-22
HI sonnet

> Does Lucid implement the latest intel vga drivers?
NO

> I just wnat to ask if the Ubuntu devs patched the .32 kernel with intel drivers from .33
If you want to contact a dev, I would use IRC #ubuntu-devel channel, and ask there.


The packages

2D driver: xf86-video-intel 2.11.0 release
3D driver: mesa 7.8.1 release 
Libdrm: libdrm-2.4.20 release
(xserver-1.8.0 is recommended to use with this package)

Can be installed from this PPA
[https://edge.launchpad.net/~xorg-edgers/+archive/ppa](https://edge.launchpad.net/~xorg-edgers/+archive/ppa)

Kernel: 2.6.33 debs from this page
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.2-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.2-lucid/)

Sharky

---

