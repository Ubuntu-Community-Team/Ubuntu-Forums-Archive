---
title: "Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz -- activating Intel graphics drivers"
date: 2014-08-30
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-08-30
I have just replaced the motherboard and processor in one of my desktop PCs with an Intel(R) Core(TM) i7-4770K CPU @ 3.50GHz processor and MSI 7846 motherboard.  I have downloaed and installed the latest version (06) on the Intel graphics drivers.  However, I have yet to find a way to activate them.  Synaptic shows that the drivers are installed except for intel-microcode.  Additional drivers does not find the Intel drivers.  What do I do next?

Thank you.

John

---

### Post by TheFu on 2014-08-31
This isn't Windows. Use the package manager, Luke. ;)

Do not install graphics drivers outside the normal Ubuntu repositories. Going outside the package manager is asking for dependency issues at some point in the future - next month, next year. That means the system will become unpatchable.

So - I'd remove the package(s) installed and reboot. Then see if device manager offers a "proprietary driver" - if not, relax.

You can check which kernel modules are loaded with **lsmod** and using **lshw -C video**

---

### Post by cigtoxdoc on 2014-08-31
Thank you for your reply.  Information that you requested is attached.

John

---

### Post by JMB74 on 2014-08-31
Make sure that the package **xserver-xorg-video-intel **is installed

The Intel graphics installer from 01.org [https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-1.0.6-linux) works just fine, and the packages are built for 14.04 and versioned in a way that should not interfere with upgrades.

The driver and card should be autodetected and loaded by X.

If not check if there is a /etc/X11/xorg.conf in existence.

If so, _**back it up**_ then either remove or make sure it says:

```
Section "Device"
   Identifier  "Intel Graphics"
   Driver      "intel"   
EndSection
```

Also make sure there is not another file in /usr/share/X11/xorg.conf.d/ that specifies a conflicting driver for Intel graphics.

---

### Post by cigtoxdoc on 2014-08-31
Hello JMB74.

Thank you for your reply.  xserver-xorg-video-intel is installed.  There is no separate video card.  Video is part of the i7-4770K processor.  Supposedly Intel HD Graphics 4600.  There is no /etc/X11/xorg.conf file.  There is nothing in /usr/share/X11/xorg.conf.d that specifies a video driver. 

What is interesting is that the nouveau driver xserver-xorg-video-nouveau is installed,along with drivers for other video cards.  I thought nouveau was only for nVidia cards?  BTW, this was a clean install that supposedly wiped out everything else.

John

---

### Post by JMB74 on 2014-08-31
No, a clean install does drag in other video drivers. Can't remember the default set installed, but it is quite a few.

Linux should load drivers according to the hardware detected, so on a generic installation and in the kernel there are a wide set pre loaded to cover supported hardware. 

1st thing I would try is creating an xorg.conf to see if that forces the activation of the intel driver when X loads?

There are some discussion lists for intel graphics somewhere that might be able to help if that doesn't work.

---

### Post by TheFu on 2014-08-31
> **cigtoxdoc said:**
> Thank you for your reply.  Information that you requested is attached.

John

Sorry - I'm not going to view any PDFs. Too risky these days.

> 
You can check which kernel modules are loaded with lsmod and using lshw -C video
The key part of this was that YOU can check it.
I thought intel drivers were included with the kernel.  Let me check my intel running netbook - yep.  Never installed anything related to video on this box.
```
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:59 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:1800(size=64)

$ lsmod|grep video
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
video                  19476  1 i915
```
I didn't install anything extra.

BTW - there are almost 50 xserver-xorg-video-* packages installed. Most are not used.  Just because a package is installed or has any config file, that doesn't mean it is being used.

---

### Post by JMB74 on 2014-08-31
> **TheFu said:**
> I thought intel drivers were included with the kernel. 

The intel backend DRM is, but the main 2d driver and 3d mesa is not, and is part system package selection.

A default ubuntu install should have everything needed to get a intel card working, but as always there can be glitches and exceptions.

---

### Post by cigtoxdoc on 2014-08-31
Thank you.  Here is the information you requested:

root@john-MS-7846:/home/john# lshw -C video
*-display
description: VGA compatible controller
product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 06
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

john@john-MS-7846:~$ lsmod|grep video
video                  19476  1 i915

John

---

### Post by TheFu on 2014-08-31
So - it looks to me like the same driver from my system is being used there.

What does:
```
/usr/lib/nux/unity_support_test -p
```
say?

---

### Post by cigtoxdoc on 2014-08-31
Per your request

john@john-MS-7846:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Desktop 
OpenGL version string:  3.0 Mesa 10.2.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Not sure what this means.

Thank you,

John

---

### Post by cigtoxdoc on 2014-09-01
I took advantage of my Canonical support agreement to get help on this problem.  First, and very important, the Intel/Harswell graphics are not considered to be third-party graphics such as nVidia and AMD/Radon and are fully supported by Canonical.  Don't look for something under "Additional drivers" because they are part of the Linux kernel.  Second, if you run /usr/lib/nux/unity_support_test -p, you should see something like I posted yesterday.

John

---

