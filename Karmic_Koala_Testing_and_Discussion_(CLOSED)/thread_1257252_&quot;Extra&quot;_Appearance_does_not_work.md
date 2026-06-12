---
title: "&quot;Extra&quot; Appearance does not work"
date: 2009-09-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lcohen999 on 2009-09-03
After a clean, fresh install of 9.10 I have run into one small problem.

Firstly, my nvidia card was not detected at all.  I added the nvidia PPA, installed 185 and everything seems to be working fine, now.  When I go into restricted drivers, it is now showing.

However, when I go to change my appearance to Extra, the system says "Searching for Drivers 0%" then hangs.

If I run compiz manually, I get this:

lcohen@lcohen-laptop:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

but no actual eye candy is working.  Any thoughts on what I am missing?

---

### Post by taavikko on 2009-09-03
Search function?

[http://ubuntuforums.org/showthread.php?t=1255964](http://ubuntuforums.org/showthread.php?t=1255964)

---

