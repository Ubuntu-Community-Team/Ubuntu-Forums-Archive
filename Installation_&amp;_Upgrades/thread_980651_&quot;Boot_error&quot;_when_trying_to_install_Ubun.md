---
title: "&quot;Boot error&quot; when trying to install Ubuntu off USB stick."
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by NSD on 2008-11-13
Hey guys.
I'm having quite a bit of trouble installing Ubuntu 8.10 (actually, even getting to the installer ...) and was wondering if you could offer some advice.
My setup: IBM Thinkpad X60 Tablet. No external USB FDD/CD/DVD drive available.
My attempts: So I've made it such that I can boot off an OCZ Rally 2GB stick with Ubuntu on it, and take it from there. The only problem is, every time I pick the stick in the boot selection window I get the dreaded "boot error" message. I know the stick is fine because it works on every other machine I have in my house (3 desktops). So yes, I guess I do realize it's actually a problem with the laptop's crappy bios. Just wondering if anyone actually managed to get around it.
While googling, I found some instances in which people suggested altering the drive's geometry, in order for it to be recognized as USB-ZIP (instead of USB-HDD), but I found no clear way on how that is done. Any ideas, please ?
And yes, I know, worst case scenario - I'll have to get an external CD/DVD drive, but that's not an option right now (it would work for sure, because I've used one in the past). 
Thanks for reading :).

---

### Post by NSD on 2008-11-14
Anybody ? :(

---

### Post by linko47 on 2008-12-20
Did you figure anything out?  My X61 is doing the same thing.  I'll post back if I find a solution.

---

### Post by linko47 on 2008-12-20
NSD, I noticed from another forum that you were attempting this with the Slackware image.  I was attempting the same.  I have gotten this laptop to boot from usb before, so I'm thinking it may be this slackware image.

---

### Post by linko47 on 2008-12-20
Using unetbootin with the Slackware DVD works perfectly.

---

### Post by OolongBrothers on 2009-05-19
Hi,
I was trying something similar, making a bootable USB stick with the Ubuntu USB Startup Disk Creator. When I booted from the so created USB pen drive I got that shy "Boot error".
As it turned out after some research, the boot sector was not properly set up, the following command fixed that:
```
lilo -M /dev/sdx
```
Here sdx is the corresponding storage device identifier of the USB stick.

By the way, the following is a nice guide of how to get an Ubuntu/Mint install on a USB stick running with persistence:

[http://jertech.blogspot.com/2009/02/stick-of-mint.html](http://jertech.blogspot.com/2009/02/stick-of-mint.html)

Regards, Alex

---

