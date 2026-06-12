---
title: "X Wont Start Yet Again - When Will Ubuntu Fix  Bug 89853??"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by dave3000 on 2007-05-17
Just blew about 5 hours trying to figure this out.  I'm a new user switching from Windows.

But I have the same problem that siefer132 reported an hour ago (except I don't have ATI video - its Intel 915).  

The problem is I'm booting from 7.04 live cd, and X crashes.

I had tried 6.10 installation last month and ran into the same problem!
Decided to wait for new release thinking that this would surely be fixed.  no such luck.

How could is possibly be acceptable to release 7.04 with this known issue that's been around since at least 6.10?  It's probably turning away potential new users in droves.

bug report here:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

related blog entry here:
[http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/](http://www.mikesplanet.net/2007/04/installing-ubuntu-704-ati-x-cards/)

Resolution to an apparently older version of the bug here:
[https://wiki.ubuntu.com/ResolutionForBug57153](https://wiki.ubuntu.com/ResolutionForBug57153)
(this resolution doesn't work for me, nor do the other two or three I've found and tried.)

And many other reports of users trying to install from live cd and not able to start X server!!!

Looks like I have to pitch this live cd in the trash and go download the alternate CD and start again.

Or, can someone recommend another Linux distribution I should try?

From a brand new user perspective, this really doesn't look good for Ubuntu.

my hardware: Toshiba m65-s809 notebook 17" 1440x900 Intel integrated 915 chipset.

---

### Post by jerrylamos on 2007-05-17
With any of the Intel graphics chips, built into the motherboard, absolutely first thing to do is to select the Bios and look for "shared video memory".  The default setting is usually 1024K which doesn't work with Linux.  Bump it up as high as it will go, 4096K or 8192K.  The chip actually uses some of main memory I have 65546K "video window" on one of my computers, and the "shared video memory" is set to 8192K.  After I did that it came up O.K.., 1024x768.

Now that machine has a 17" 1280x1024 LCD which I had to set with:
sudo dpkg-reconfigure -phigh xserver-xorg
On an install I did that once.  On CD Live, every boot.  I think it would be once on CD Live "persistent" with USB pen drive volume casper-rw, however that's broken on 7.04.  Works on 6.10 and 6.06.

Cheers, Jerry

---

### Post by dave3000 on 2007-05-17
Jerry,
Thanks, I'll give that a try late tonite.
Dave

---

