---
title: "nVidia GeForce8400 display problems after upgrade from 10.4 to 10.10 x64"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by mutineer612 on 2010-10-10
I recently upgraded from 10.4 to 10.10 x64 and found out the hard way that 10.10 has issues with nVidia due to newer version of Xorg 1.9.  I had the nVidia driver 'current' working with my nVidia GeForce 8400 when I performed the upgrade from 10.4, and after rebooting found that the system booted to a purple background image with no login prompt.  I tried booting into recovery mode by holding shift while booting and disabling the nVidia driver and rebooting.  

Now with the driver removed the system boots to purple background screen with the ubuntu status indicators (dots) and makes the drum sound normally followed by the login prompt, but I'm unable to see it and none of the function keys work to drop to a console.  However if I perform the reboot again with the drivers removed I'm able to hold down the shift key while booting and enter recovery mode again and then select safe graphics mode to access the system, and this seems to work ok, but I cannot get the system to boot without performing these manual steps.  

Any suggestions?

---

### Post by andrewthomas on 2010-10-10
did you delete your xorg.conf?

---

### Post by mutineer612 on 2010-10-11
Yes, I have deleted the /etc/X11/xorg.conf file with no change is system behavior.  :(.  It seems like this might be related to bug [#616394]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/616394") or [#626974]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/626974").

But I'm open to any suggestions from those who have been able to get nVidia cards working.

---

### Post by mutineer612 on 2010-10-22
Well, having no luck with this issue I've been forced to re-install Ubuntu 10.4 LTS.  I don't think 10.10 was ready for prime time given this issue with Xorg 1.9 not supporting the legacy Nvidia drivers.  For my situation there was no real significant improvement between versions, and the video adapter issue proved to be a huge pain.  

My Nvidia GeForce 8400 GS runs great using the Nvidia driver 195.36.24 with Xorg 1.7.6 on Ubuntu 10.4.  I did confirm my issue is not related to the above to bugs I mentioned as they are specific issues with the 96 and 173 Nvidia drivers, that being said I still certainly have an issue, possibly a different bug or compatibility issue.  I scoured the blogs and bug reports trying every cryptic suggestion to no avail.

I know that this issue not directly the Ubuntu teams fault and really falls on the Xorg folks, but I think this is a significant enough problem with the 10.10 release given the number of legacy video adapters in use with slightly less than new PC's running Linux.  

If the Ubuntu team knew this would break, it would have been nice not to go through all of the pain of upgrading, troubleshooting, and eventually backing down to a more stable release,  I'm sure there will be a fix in the coming months, but I will most likely stick with the LTS releases from here on out.

---

### Post by endotherm on 2010-10-22
the geforce 8200-8600 cards have never been fully compatible with the linux drivers. I have spent years trying to deal with TVOut and overscan issues, in particular with 8400GS cards from several different manufactures. The Nvidia cards also have problems with Plymouth (the new purple bootscreen stuff in 10.04-10).

on teh upside, the 7000 series, and everything greater than the 8800GT seem to work fine (except for plymouth).

---

### Post by stefan.hattrell on 2010-10-28
I've been struggling with this one for a few days now.

Tried lots of different suggestions but the only fix I've found is to remove the nvidia-current package ("tested by the Ubuntu team" though not with our hardware config) and manually install an older version of the Nvidia driver (256.53 I believe). 

System runs beautifully now!

---

### Post by chinaski on 2010-11-05
I had blank screen too after fresh install of Ubuntu 10.10 and installation of nVidia proprietary driver, current recommended version through System -> Administration -> Additional Drivers.

Tip here is to install older version (173) and not the current.

I have nVidia 8400 GS graphic card.

---

