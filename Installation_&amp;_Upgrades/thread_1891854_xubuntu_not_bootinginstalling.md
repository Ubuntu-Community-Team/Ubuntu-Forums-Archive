---
title: "xubuntu not booting/installing"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by cman12 on 2011-12-06
I have an old laptop, a dell inspiron 2650 with Windows Xp on it. It is not running well so I wanted a lightweight os on it. I made a CD of Xubuntu and popped it in. I tried a regular install by booting from CD but when I do that, I click install, then its a black screen with a _ flashing in the upper left hand corner. It does this for a long time and then it turns into a blank screen.

I then booted to windows and popped the CD back in and installed it inside of windows. It said it installed correctly, so I restart. I get the choice of booting into windows or Xubuntu. I choose Xubuntu and it gives me the message:

try hd(0,0): ntfs5: error: "Prefix" is not set.

Any help with this? Thanks.

---

### Post by MAFoElffen on 2011-12-06
> **cman12 said:**
> I have an old laptop, a dell inspiron 2650 with Windows Xp on it. It is not running well so I wanted a lightweight os on it. I made a CD of Xubuntu and popped it in. I tried a regular install by booting from CD but when I do that, I click install, then its a black screen with a _ flashing in the upper left hand corner. It does this for a long time and then it turns into a blank screen.

I then booted to windows and popped the CD back in and installed it inside of windows. It said it installed correctly, so I restart. I get the choice of booting into windows or Xubuntu. I choose Xubuntu and it gives me the message:

try hd(0,0): ntfs5: error: "Prefix" is not set.

Any help with this? Thanks.
How much memory and what is your video in your laptop?

EDIT-- Haven't heard from you, so... I do a lot of installs on older Dell laptops.

Yours has Nvidia NV11 as graphics, so if you use a "nomodeset" switch at the Advanced Install Menu of the LiveCD it would Boot the LiveImage fine. You would have to do the same after the install (or use safemade) until you installed your graphics driver.  The Nouveau 3D Experimental would be your best choice of a Graphics driver.

What would be the biggest concern is Memory. That laptop came standard with 128 MB DDR. I've installed Xubuntu on that... Runs using the XFCE desktop in that, but slow. Xubuntu's DE will bounce the limits of that depending what you have loaded... That laptop max'es RAM at 512MB... Recommended that if you can, upgrade the memory to somewhere between 256MB-512MB.  If not, then use the Lynx branch of Puppy, which will run in that and is a branched distro of Ubuntu Lynx.

---

