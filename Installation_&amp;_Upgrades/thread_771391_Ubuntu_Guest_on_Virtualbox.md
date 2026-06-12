---
title: "Ubuntu Guest on Virtualbox"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Kow on 2008-04-27
I installed Hardy via Virtualbox (XP host) and installed the guest additions just fine. I added the screen resolutions to xorg.conf however it doesn't make any difference. I go to "Screen Resolution" in preferences and only 800x600 and 640x480 are listed. My Windows XP is running @ 1280x1024.

---

### Post by Kow on 2008-04-27
Apparently Hardy's automatic driver detection (instead of using xorg.conf) has confused VirtualBox' Guest Additions. I had to modify xorg.conf to explicitly tell X11 to use the vboxvideo driver. This should be mentioned somewhere (perhaps a wiki?)

---

### Post by ivze on 2008-04-28
I confirm the bug! Have the same problems. Digging a bit in xorg.conf did not help. 
It would be wonderful, if there were some manuals how to do make it run or if it worked out-of-the-box.

---

### Post by vexingmodstwo on 2008-05-28
This is probably a total noob comment but I'm sure there are other noobs out there scratching their heads.

If you install the latest round of upgrades (the one with the latest kernel upgrade), you'll probably have to reinstall VirtualBox Guest Additions.

---

### Post by broham on 2008-05-28
I had the same problem a few weeks ago, and the answer below worked for me...

> **hurtstotalktoyou said:**
> This appears to be a problem with the monitor detection, not the video card driver.  Here's what I did:

1.  Go to System > Administration > Hardware Drivers and make sure your proprietary video card driver is disabled (the box should be unchecked).  Don't worry, you'll enable it later; just not now.  Reboot if necessary.

2.  Go to System > Preferences > Screen Resolution and choose the highest available resolution (usually 800x600).  This will allow you to navigate through Ubuntu more easily than at the lower resolutions associated with the proprietary driver.

3.  Go to System > Preferences > Main Menu > Applications > Other and make sure the "Screens and Graphics" box is checked.

4.  Go to Applications > Other > Screens and Graphics and select the option which best describes your display (LCD or CRT, etc.).  Do *not* use the "detect" function.  Also, do *not* choose "Plug 'n' play".

5.  Now go back to System > Administration > Hardware Drivers and enable your proprietary video card driver.  You will have to reboot for sure this time.

Even after these steps, I still am having trouble with the login screen, which does not display properly.  However, after logging in you should have little or no trouble getting higher resolutions.


---

