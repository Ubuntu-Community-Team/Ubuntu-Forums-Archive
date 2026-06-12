---
title: "Ugh Resolution Hosed"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by burgechris on 2008-05-28
ok...I'm rather a newbie with Ubuntu/Linux.  That said, I had a successful 7.04 version with dual monitor support (used Envy).  Now that I have upgraded to 8.1 (?), my resolution has dropped from 1024x768 to 800x640 and only 1 monitor.  Sigh.  Being a developer, this really sucks.  I have done various iterations/variations of the below until I'm blue in the face and was wondering if anyone could help.

Uninstalled Envy, Installed EnvyNG, Uninstalled Envy, Installed NVIDIA, Uninstalled NVIDIA.  

Sigh.  I'm about ready to sacrifice a chicken to the Ubuntu X11 gods so I'm looking for any sort of help.  My system consists of the following:

AMD 64  (yes I have 64 bit installed)
NVIDIA GeForce 7600 PCI
Digital and Analog monitors of the Dell 1907FP

I'm sure that the xorg.conf would be needed but I don't want to spam the board if it isn't so I'll wait to see if anyone requests it.

Thanks,
Chris

---

### Post by iaculallad on 2008-05-28
> **burgechris said:**
> ok...I'm rather a newbie with Ubuntu/Linux.  That said, I had a successful 7.04 version with dual monitor support (used Envy).  Now that I have upgraded to 8.1 (?), my resolution has dropped from 1024x768 to 800x640 and only 1 monitor.  Sigh.  Being a developer, this really sucks.  I have done various iterations/variations of the below until I'm blue in the face and was wondering if anyone could help.

Uninstalled Envy, Installed EnvyNG, Uninstalled Envy, Installed NVIDIA, Uninstalled NVIDIA.  

Sigh.  I'm about ready to sacrifice a chicken to the Ubuntu X11 gods so I'm looking for any sort of help.  My system consists of the following:

AMD 64  (yes I have 64 bit installed)
NVIDIA GeForce 7600 PCI
Digital and Analog monitors of the Dell 1907FP

I'm sure that the xorg.conf would be needed but I don't want to spam the board if it isn't so I'll wait to see if anyone requests it.

Thanks,
Chris

Posting your /etc/X11/xorg.conf file would help.

---

### Post by burgechris on 2008-05-28
:lolflag:

Apparently sleep does a body good.  I woke up.  Took care of the kids and re-uninstalled the NVIDIA drivers, packages and Envy packages that the package manager downloaded.  I then re-downloaded the NVIDIA drivers directly from NVIDIA. CTRL-ALT-F1 out.  

Then

cd <downloaded NVIDIA path>
sudo init 3
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
DID NOT ALLOW IT TO INSTALL 32 bit drivers
gave me some warnings
sudo init 5
sudo /etc/init.d/gdm restart

Badda Bing Badda Boom.  And it works better than before!  In the 7.04 Ubuntu I used envy and had a problem saving changes to xorg.conf along with implementing some of the capabilities of the card!

Thanks!

---

