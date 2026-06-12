---
title: "failed nvidia install"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by davedaveh on 2010-11-13
Have Ubuntu 10.10 with 96.43.18 Nvidia card.  Gui worked after install.  Sluggish video, so started to update the drivers.  Have been going around in circles installing from Nvidia web site, as well as Ubuntu package repository. I did try to purge nouveau as well.
Nvidia tried to install, but received error message about a missing script, install anyway?  Did not work. 
Had no problem with screen res before I lost gnome.
"Failed to load module "nvidia"
"Failed to load /usr/lib/xorg/modules/drivers/nvidia_drv.so"
Those messages still appear on my terminal after 'startx'.  I do have Gnome, but no vid driver. "No drivers available."
I am somewhat of a newbie, but have used command line.
At one point I had an empty xorg.conf.  Now after nvidia install:

Section "Device"
   Identifier  "Device0"
   Driver      "nvidia"
   VendorName  "NVIDIA Corporation"

I need to get GUI back, then work on tweaking video drivers.
Thanks.

---

### Post by koolblue3 on 2010-11-13
Change the driver section of xorg.conf from nvidia to nv. This should hopefully get GNOME back.

---

### Post by owise1 on 2010-11-13
nvidia 96.43.18 does not play nicely with Xorg 1.9 - see [http://ubuntuforums.org/showthread.php?t=1592628](http://ubuntuforums.org/showthread.php?t=1592628)

96.43.19 is available and looks like it might be getting close to being packaged - see [Bug 626974] Re: ABI change in xorg 1.9 breaks legacy nvidia-96 drivers in Maverick - [https://bugs.launchpad.net/bugs/626974](https://bugs.launchpad.net/bugs/626974)

---

### Post by owise1 on 2010-11-13
the easiest way to use the nvidia driver is this way [https://help.ubuntu.com/10.10/hardware/C/jockey.html](https://help.ubuntu.com/10.10/hardware/C/jockey.html)

---

### Post by davedaveh on 2010-11-13
Thanks.  Tried to edit file -- read only.
Oh yeah - forgot sudo.

Just got GUI back thanks.
Still no 'visual effects' improvement.  Nvidia settings utility only has minimal options.

Tried owise1's suggestion, but must have missed something.

Thanks Kool and Wise

 Now in "Additional Drivers" box, nvidia_96 is activated, but not "in use".  What gives with that?

---

### Post by owise1 on 2010-11-14
the current nvidia drivers in the 10.0 repository are buggered - will not work with XOrg 1.9.  I upgraded a machine to 10.10 and had it crash out to a command prompt - not very friendly.  I am now waiting for the new version to be packaged to save going through the hoops of running the nvidia install script and having to re-do it every time the kernel is updated.

I have been using the nouveau driver and it works fine for 2D but if you get an acceptable resolution for the nv driver stick with that.  I needed a 1440X768 resolution and nv could not provide it.

Have a read of the two links I posted - they also have detailed instructions on running the nvidia install script if that is the way you want to go.

---

### Post by davedaveh on 2010-11-14
T

---

### Post by davedaveh on 2010-11-14
Thanks for the sane and reasoned advice.  I'm still waiting for Linux to come closer to my short reach. It's been fun though.  Still want to join the elite class of Linux users.  For me, a slippery slope.
And I thought I could get my wireless card to work too!   ;-?

---

