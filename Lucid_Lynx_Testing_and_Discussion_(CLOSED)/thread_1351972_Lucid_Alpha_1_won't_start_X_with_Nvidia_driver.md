---
title: "Lucid Alpha 1 won't start X with Nvidia driver"
date: 2009-12-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-12-11
I've done this twice now. First I upgraded 9.10 using [FONT=Courier New]update-manager -d[/FONT] and then added the Nvidia driver. After a restart I get stuck at the text login prompt.

I figured I had done something wrong so I downloaded the ISO and installed that from scratch. The Nvidia driver again seemed to install fine but with the same problem after reboot.

Is there a fix for this in [FONT=Courier New]/etc/X11[/FONT] or somewhere, or do I need to reinstall again?

---

### Post by Robin Nixon on 2009-12-11
The solution here removed the nvidia drivers and got X back for me - : [http://ubuntuforums.org/showthread.php?t=1351375](http://ubuntuforums.org/showthread.php?t=1351375)

But should Ubuntu always report that I am in low graphics mode, though?

---

### Post by philinux on 2009-12-11
> **Robin Nixon said:**
> The solution here removed the nvidia drivers and got X back for me - : [http://ubuntuforums.org/showthread.php?t=1351375](http://ubuntuforums.org/showthread.php?t=1351375)

But should Ubuntu always report that I am in low graphics mode, though?

Welcome to ALPHA 1. Bugs are expected.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/494166)

---

### Post by kevpan815 on 2009-12-11
> **Robin Nixon said:**
> I've done this twice now. First I upgraded 9.10 using [FONT=Courier New]update-manager -d[/FONT] and then added the Nvidia driver. After a restart I get stuck at the text login prompt.

I figured I had done something wrong so I downloaded the ISO and installed that from scratch. The Nvidia driver again seemed to install fine but with the same problem after reboot.

Is there a fix for this in [FONT=Courier New]/etc/X11[/FONT] or somewhere, or do I need to reinstall again?

Try Using The Latest Beta NVIDIA Device Driver From [http://www.nvidia.com](http://www.nvidia.com), Instead Of The Integrated NVIDIA Device Driver, Which Is Broken At The Moment! It Worked 4 Me!

---

### Post by Universal344 on 2009-12-11
This is very interesting.  Similar thing happened to me with my ATI card.  I installed the fglrx driver from repos and nothing happened.  I checked and saw I had no xorg.conf file and figured it was due to the removal of hal.  So I created one and ran the ATI configuration.  When I restarted with my new xorg.conf, I got text login.  Once I removed the xorg.conf file though (drivers still installed), I got my graphical display back.  At the moment it seems advanced display drivers can't be running without causing X to fail.  I'll try reconfiguring X with vesa and see if it is drivers that cause the failure or simply having an xorg.conf file.:?

---

### Post by SoftwareExplorer on 2009-12-25
Have a look at this bug:[https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166](https://bugs.launchpad.net/nvidia-drivers-ubuntu/+bug/494166)

Lucid has a new Xserver/xorg version (that has MPX, woot!), and so that's problably why things are a little messed up for now. The bug report suggests using at PPA from the user sevenmachines, you might try that.

---

