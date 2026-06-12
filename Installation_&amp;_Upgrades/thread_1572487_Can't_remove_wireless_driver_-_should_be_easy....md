---
title: "Can't remove wireless driver - should be easy..."
date: 2010-09-11
forum: Installation &amp; Upgrades
---

### Post by rbrauns on 2010-09-11
Background info:

I just loaded the latest 10.04 Ubuntu to my brand new HTPC and it works 95% out of the box. Just need to get my USB based wireless card installed. WUA-2430.

What I did:

Searched the forums and installed ndiswrapper, got the device id 07di:03a8 and installed the neta5agu.inf driver as per instructions.

Problem: I only copied the .inf file but got an error message saying that the .sys and .bin files were missing.  They were because I didn't copy them and the instructions didn't say to copy them over. Copied them over and reinstalled the driver.

Got an error message, neta5agu already installed.

Tried removing the driver by:
ndiswrapper -r neta5agu  =ERROR: inapppropriate ioctl for device
ndiswrapper -r neta5agu.inf  =ERROR: No such file or directory

ndiswrapper -l yields: neta5agu invalid driver!

How to fix this?  I did search the forum but 99% of responses are how to install a driver using ndiswrapper and simply say to reinstall if errors.  Well, that is not working for me.

Thanks.

---

### Post by rbrauns on 2010-09-11
OK, I managed to remove the poorly installed .inf driver.  I had to type sudo ndiswrapper -r neta5agu command, then ndiswrapper -r neta5agu and it was gone. Still can't get my wireless card to work but I'm using 64 bit Ubuntu and a 32 bit XP driver so I'm going to try the Vista drivers.

---

