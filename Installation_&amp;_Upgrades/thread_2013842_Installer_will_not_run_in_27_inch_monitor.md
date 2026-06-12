---
title: "Installer will not run in 27 inch monitor"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by hannuh on 2012-07-01
Here is something the programmers of the Ubuntu installation should take a look at:
I was having major problems with installation and I thought the problem was my newer Nvidia cards. First this happened Quadro 2000 video card, then same thing with GTX 560 Ti.
It turns out that the problem is the monitor I am using for this computer.
The Ubuntu installer will not run in a Samsumg SyncMaster P770 27 inch monitor. Once you boot from the Live CD, you get a smaller (maybe 24 inch) image on the screen, with the cursor blinking and that's it.
 When I switch the monitor to a 24 inch SyncMaster SA350 (24 inc) the installer will run. However, once the installation is complete, including the nvidia driver installed, I can switch to the 27 inch and Ubuntu will run just fine.
The splash screen will run in a reduced size, but once the login screen comes up, Ubuntu begins to use full screen.
Both monitors have native resolution of 1920x1080, but the problem seems to be physical dimensions of the screen. 
I don't know if this is the case with all 27 inch monitors, or just the Samsung SyncMaster P770.
So, the workaround is:
- install Ubuntu with with a smaller monitor, but same resolution
- once nvidia drivers have been installed, you can switch to the 27 inch.
Hannu

---

### Post by efflandt on 2012-07-02
Which Ubuntu version were you installing?  It seems to change a little each version.  For 10.10 I did not need any kernel boot parameters at all.

When I installed 64-bit 11.10 I did not need any kernel boot parameters for install.  But after install I had to use **nomodeset** for nvidia drivers in order to boot without getting "no signal" on my screen after grub menu.

64-bit 12.04 was just the opposite.  When I booted install iso from USB, I just got a blinking cursor forever, right through the drum roll.  So I had to use **nomodeset** for install, but installed 12.04 system with nvidia drivers does not need any boot parameters.

So **nomodeset** kernel boot parameter is the first thing to try for video issues.

Video is GTX 550 Ti connected DVI to HDMI to 32" 1080p HDTV (which can do all the usual PC video modes).

---

### Post by hannuh on 2012-07-02
My original attempt was Ubuntu 12.04, in which I got just the blinking cursor. Then I tried 11.10, it ran a few command lines and died.
I also tried Mint 13 and Mint 12 KDE, same thing.
 
The only thing I discovered later on that if I get the timing right, I can get to "Compability Mode" and then the installer comes up.
Now, I have never tried to install from the Live CD's compability mode, I don't know if it would work. 

However, as I said, all of them will install normally on the smaller 24 inch monitor and the nvidia driver automatically chooses the right 1920x1080 resolution.

Would you be able to change the kernel parameters when you are running the Live CD, and if so, how?
Thank you,
Hannu

---

### Post by darkod on 2012-07-02
Yes, you can modify boot parameters from live cd too. You have instructions here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

