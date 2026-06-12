---
title: "Problems installing proprietary video drivers on dual card laptop"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by slowtrain on 2012-06-04
So, I'm taking the leap & trying Ubuntu on a laptop.  Pretty good, but when I try to install the ATI / AMD proprietary FGLRX, installation fails.  I get this error:

WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver

Ok, I could try downloading and installing the Catalyst driver directly from AMD.  I did only this (ran the installer, nothing else--I suspect there's more I should have done), and used admin access to switch the driver to the Intel graphics card rather than the AMD Radeon card.  I figured this would let the laptop run with less power and I could switch if I did any gaming.  On reboot, I got the "Failed to start the X server" msg.  Had to reinstall Ubuntu.

Does anyone know if it's safe to install the Catalyst driver directly?  Would installing Catalyst switch my graphics card use from the Intel to the Radeon (bad for power consumption)?  What about installing the open source flgrx drivers?  Is there any way to switch easily between cards?

Any thoughts would be much appreciated!

---

### Post by zvacet on 2012-06-05
Did you tried to install driver from **additional drivers**?

---

### Post by slowtrain on 2012-06-06
Hi zvacet:

Yes, what I meant was that when I tried to install the driver from Additional Drivers, I got the following error in /var/log/jockey.log:  

WARNING: /sys/module/fglrx_updates/drivers does not exist, cannot rebind fglrx_updates driver

I tried to install several times, after reboots.  I always get the same error.

---

### Post by slowtrain on 2012-06-06
Played with it some more.  I get the above mentioned error when I try to directly install the proprietary FGLRX driver post-release update.  

I SEEM able to install the proprietary FGLRX driver (not post-release update), or so the Additional Drivers seems to think.  But, it doesn't seem to be working, even after a reboot.  I tried running some 3D games (Megaglest, Alien Arena) and it instantly crashes.  Also tried glxgears, which I gather is a standard test.  I get this:

$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12


When I look to see what jockey.log says after installing the proprietary FGLRX driver, there seem to be some error msgs, chiefly:

2012-06-06 18:25:49,773 DEBUG: unbind/rebind on driver /sys/module/fglrx/drivers/pci:fglrx_pci: device 0000:01:00.0
2012-06-06 18:26:10,623 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-06-06 18:26:10,624 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

Maybe the problem is caused by my also having installed the xserver-xorg-video-radeon driver?  Not sure I should try uninstalling it--could bring down my video, or?

---

### Post by slowtrain on 2012-06-09
Interesting.  I entirely removed the proprietary drivers from my system.  Now, 3D graphics seem to work.  It looks like xserve-xorg-video-radeon, which is installed, provides some 3D and was being blocked by my partially installed fglrx drivers.  I don't need much by way of 3D, so this probably will do the trick.

Incidentally, I did try removing xserve-xorg-video-radeon and installing the proprietary drivers.  That didn't work.

---

