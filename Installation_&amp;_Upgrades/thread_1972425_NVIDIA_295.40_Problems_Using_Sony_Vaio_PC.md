---
title: "NVIDIA 295.40 Problems Using Sony Vaio PC"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by sAndshark8 on 2012-05-03
I was using 10.04 and it worked well and I decided to upgrade.

I installed 12.04 on a Sony SZ780 with a Nvidia Gforce 8400M GS accelerated graphics card. XORG NVIDIA Panel says it is using 295.40 driver. This driver causes the computer to boot extremely slowly.....like three or more minutes.  And, the computer will not fully shut down.  When choosing the shut down option and then clicking the next are you sure shut down message box, the computer shuts down the OS, but leaves the fan and power lights on.  To fully shut down I have to hold down the power switch.  The same thing happens on restart.  It stalls after it looks like the OS is down with the fan and power on and will go no further.

This Sony has two graphics options. 1) .performance.accelerated graphics or2) stamina low graphics.  

I earlier used this same computer with the graphics switch set to the stamina low graphics option and it booted find and shut down fine, but only used Unity 2D.

The problem started when I used the 12.04 Settings application to check for proprietary drivers and it installed 295.40.  Settings gives the recommended driver and another drive option.  Both options install 295.40.  NVIDIA also pushes 295.40. The Nvicia XORG panel info doesn't show errors and looks normal.

Is there a way around this problem, or has UBUNTU issued an OS that will not properly run on the Sony PC?

---

### Post by Pablo Pablovski on 2012-05-03
295.49 driver released.

[http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-295.49-driver-uk.html)

---

