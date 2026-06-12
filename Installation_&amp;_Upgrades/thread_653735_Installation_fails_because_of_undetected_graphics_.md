---
title: "Installation fails because of undetected graphics card?"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by satyavan on 2007-12-30
Installation of Ubuntu 7.1 on my laptop fails! I have an Asus X50N, 2Ghz AMD Turion 64x2 TL60, 2Gb ram, 160 Gb HD, which supports an Nvidia GeForce 7000M graphics card (screen works in 1280x800, 32 bit, 60 Hz mode).  I get the message: "Your screen and graphics card could not be detected correctly". I tried the "configure" option, setting the screen resolution, but the above Nvidia card isn't listed. Choosing some Nvidia generic driver or running installation with the drivers CD doesn't work either. With some configurations the system stalls entirely after the message: "Running local boot scripts (/etc./rc.local)"....

Has someone an idea what went wrong and how to fix this problem?

Satyavan

PS: Installation seems to work in graphics save mode, but it is low graphics and I would like to avoid this if possible.

---

### Post by phidia on 2007-12-30
If you can get the install to work in what you've called "low graphics mode" you can complete the install and then have synaptic install the proprietary nvidia driver after you've successfully completed the install. (see the multimedia and video forum here for the exact method on installing the nvidia driver) You could open a tty (another shell) while in the installer mode and issue "sudo dpkg-reconfigure xserver-xorg" and select the open source nv driver but I'm not sure if that's what you're looking for or really needing either.

Added: Actually once you have the install you can or should be able to enable the Nvidia driver from the System>Administration menu.  And if the graphic mode that works is too poor a resolution then the dpkg command I included above should get a more usable driver working.

---

### Post by satyavan on 2007-12-30
I tried this but unfortunately there seems to be still a problem with graphics. Ubuntu shows all the windows which stretch below the task bar. It is impossible to see the text below the screen and where to click to go forward in the installation. Dragging the size of the window is only allowed from the bottom edge which is invisible. Trying to resize with screen and graphics preferences does not work because all the configuration tests fail. Its like making an installation blindfolded :(

Can anyone help? :confused:

---

### Post by arsoft on 2007-12-30
Hello!
I have the same problem with this kind of the laptop (only CPU different, just 1 core AMD)...
PLEASE anybody HELP!!!

---

### Post by overdrank on 2007-12-30
@arsoft
@satyavan
Hi and have you tried the alt, and single click and hold with the mouse this will allow you to move the window up to enter the buttons.

---

### Post by phidia on 2007-12-30
Using the alt & left mouse button should work to move a window that's inacessible as overdrank says. 
Still, you should be able to get a workable resolution with the nv driver.
Did you try the dpkg-reconfigure command? That will allow you to select a usable screen rez.

---

### Post by satyavan on 2007-12-31
Ah... "alt click" works indeed. Thanks. :) Ok, here is the next problem for novices like me....

I don't understand how partitioning works. When I reach the "prepare disk space" step 4/7 and select a 40 Gb free space for partitioning manually, after setting for the root "mount point: / ", what kind of file system should one choose? "ext2" or ext3", or which and depending from what?

---

### Post by satyavan on 2007-12-31
Ok, I installed Ubuntu with file system ext3. 

But still problems with graphics. In the system/administration setting screen resolution does not work. As to the "dpkg-reconfigure command" it asks me a plethora of questions I didn't know how to answer for sure. Anyhow, despite having defined 1280x800 the screen resolution remains low. It finally tells: "xserver - xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080101144050". 

The graphics card issue in Ubuntu seems to be the hard problem here... :(

---

### Post by overdrank on 2007-12-31
> **satyavan said:**
> Ok, I installed Ubuntu with file system ext3. 

But still problems with graphics. In the system/administration setting screen resolution does not work. As to the "dpkg-reconfigure command" it asks me a plethora of questions I didn't know how to answer for sure. Anyhow, despite having defined 1280x800 the screen resolution remains low. It finally tells: "xserver - xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080101144050". 

The graphics card issue in Ubuntu seems to be the hard problem here... :(

HI and yes it seems that way as I am trying to help another user with a similar issue. This may prove to be of some help
[http://ubuntuforums.org/showthread.php?t=510352](http://ubuntuforums.org/showthread.php?t=510352)
Good luck!

---

