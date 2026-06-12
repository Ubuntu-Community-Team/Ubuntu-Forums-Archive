---
title: "Proprietary Drivers"
date: 2013-12-23
forum: Installation &amp; Upgrades
---

### Post by sagemaster210v2 on 2013-12-23
Hello,

I had recently installed Ubuntu to my laptop, and I have done some research on things to do after installing Ubuntu, One of these things included allowing the use of my video card, which was supposedly found under the "Additional Drivers" tab in "Software and Updates" application included with the installation. But anyway, when I had opend the tab, and waited for the application to find my drivers, it said that "No additional drivers found". So I was wondering if there was a fix to this, or is it that my video card is unrecognizable, I'd appretiate some kind of imput that can really help me, thanks. And heres what I have accquired on from the teriminal regarding my graphics card:
*-display               
       description: VGA compatible controller
       product: RS690M [Radeon Xpress 1200/1250/1270]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=64
       resources: irq:44 memory:f0000000-f7ffffff memory:f8100000-f810ffff ioport:9000(size=256) memory:f8000000-f80fffff

---

### Post by Bucky Ball on 2013-12-23
Run this command in a terminal:

```
sudo lshw -C video
```

Post the result back here, thanks.

---

### Post by grahammechanical on 2013-12-23
Are you connected to the internet? Additional Drivers searches online repositories. If you installed Ubuntu with the option to install third party software ticked, then the installation would have installed a proprietary video driver as part of the process. If you have proprietary video drivert, then it usual to have a settings manager for the driver installed as well. You may find it in the Dash>applications. Also if you go to System Settings>Details you will find information on the video driver in use. If Details says something with "Gallium" then you are using the open source driver called Nouveau. You will also find that the experience is listed as "Standard." That is usual whether we are using proprietary or open source video drivers. I have never seen it say anything else.

Regards.

---

