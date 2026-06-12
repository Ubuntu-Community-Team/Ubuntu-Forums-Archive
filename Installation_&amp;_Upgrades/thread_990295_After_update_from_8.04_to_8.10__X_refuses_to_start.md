---
title: "After update from 8.04 to 8.10:  X refuses to start with fglrx, module missing?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Frando on 2008-11-22
Hey everyone.

I have a Mobility Radeon HD2600 graphics card. I was using the proprietary fglrx driver in 8.04 (Hardy) without any problems. Everything including 3D acceleration worked perfectly.

Now, I just upgraded to 8.10 Intrepid. And now X refuses to start with Driver "fglrx" in xorg.conf. With the line removed, it starts with some default drivers but without hardware acceleration of course.

Here's an excerpt of Xorg.0.load of a failed startup of X.

> (II) LoadModule: "fglrx"
 
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
        compiled for 1.4.99.906, module version = 8.55.2
        Module class: X.Org Video Driver
(II) Primary Device is: PCI 01@00:00:0
(WW) Falling back to old probe method for fglrx
(II) ATI Proprietary Linux Driver Version Identifier:8.55.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.552                    
(II) ATI Proprietary Linux Driver Build Date: Oct 28 2008 21:22:33
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0
(WW) Video driver ABI version of the X server is 4.1
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(--) Chipset Supported AMD Graphics Processor (0x9581) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x89e29a8

The full log and also the xorg.conf used can be found here: [http://pastebin.com/m32a5f5cc](http://pastebin.com/m32a5f5cc)

I have installed linux-restricted-modules and xorg-driver-fglrx. I tried reinstalling both without success. 

A '```
sudo modprobe fglrx'
``` results in "FATAL: Module fglrx not found.". 

So, the error seems to be that the fglrx kenrel module can't be loaded. Further investigating, it seems the module is simply not present for the current kernel (2.6.27-8), as '```
find /lib -name fglrx
```' returns only ```
/lib/linux-restricted-modules/2.6.24-21-generic/fglrx
``` and nothing else.

I tried building the module with ```
sudo m-a a-i fglrx
``` but no success, I got a blue console screen telling me that building failed and I could either VIEW, CONTINUE or STOP, wheres the latter two simply would quit and VIEW would show an empty log file (containing only a date line).

So, I'm quite confused by now, especially because it used to work perfectly in 8.04 and because I haven't found any bug reports detailing my problem. Any help is greatly appreciated. 

Where exactly is the problem? Is it the missing module? If so, why could building it with m-a fail, or how else could I get the module?

Regards,
Frando

---

