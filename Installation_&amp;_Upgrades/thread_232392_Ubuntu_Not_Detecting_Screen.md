---
title: "Ubuntu Not Detecting Screen"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by detuneyourradio on 2006-08-08
I've had Ubuntu on my laptop for several months now and I really dig it.  I've been wanting to put it on my main machine for a while now, but I haven't been able to as my job requires use of Visual Studio (yuck!).  However, I'm off to college so no more job, hence, no more requirement for Window$. 

I popped the Ubuntu 6.06 disc in my drive and ran it, but I the x.org config gives me a "no screens found" error.  The last bit of the detailed server output is as follows: 

```
(II) Primary Device is: PCI 04:00:0
(II) ATI: Candidate "Device" section "ATI Technologies, Inc. Radeon X800 (R430 UO)".
(WW) ATI:  PCI Mach64 in slot 4:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 4:0:1 could not be detected! 
(EE) No devices detected.  

Fatal server error: 
no screens found
```

If I boot the live cd in "safe graphics mode" it works but doesn't let me select a widescreen resolution (I've got a DELL 21" Widescreen and a 15" regular - both flat panels - that I use together ... I know using a dual monitor set up with two completely different monitors is cheesy, but I'm not up in the cash department and it's better than nothing ... ).  Now, I'm pretty good with Ubuntu, but I'm a hardware idiot.  I custom built my main machine, and it's got an ATI X800 video card and a 3.2 p4 prescott 64bit.  (now, if I'm correct, I downloaded the normal 6.06, not the one for 64bit processors because I want to stick with 32bit until more support comes out for 64 bit, so I shouldn't have problems in that department, yes?) 

So basically, am I just screwed, or is there a way around it?  I know the general rule of thumb is that if a distro doesn't recognize more than 1 piece of your hardware, to just try a different one, but I really dig Ubuntu so I'm willing to work hard to get it working. :) 

Kyle

---

### Post by zxee on 2006-08-08
I'm not familar with the exact ati card you have but ati support for linux seems to be improving. You should be able to get your graphics card recognized. You can try this from the livecd. > dpkg-reconfigure xserver-xorg and take a look at this thread on monitor set up;
[http://www.ubuntuforums.org/showthread.php?t=228366&highlight=wide+screen](http://www.ubuntuforums.org/showthread.php?t=228366&highlight=wide+screen)

---

