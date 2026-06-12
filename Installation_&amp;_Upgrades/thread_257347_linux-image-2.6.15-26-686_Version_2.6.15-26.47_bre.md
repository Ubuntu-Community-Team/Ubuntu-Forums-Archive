---
title: "linux-image-2.6.15-26-686 Version 2.6.15-26.47 breaks nvidia driver!"
date: 2006-09-14
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2006-09-14
linux-image-2.6.15-26-686 Version 2.6.15-26.47 breaks nvidia proprietary driver!  

automatic updates pushed this to me this morning, after installing Xsever wouldn't start!

I tried apt-get install nvidia-glx and it said I had the most current one already intalled.  Repeated nvidia-xconfig and still nogo!

changing:
Section Device
    Driver "nvidia" 

to: Driver "nv" in /etc/X11/xorg.conf let the next boot succeed.

Beware!

I'm downgrading now to 2.6.15-26.43.  I need the proprietary drivers since the X.org nv driver has a performance issue with the Xvideo extensions -- Fedora 5 has fixed the issue, X.org bugzilla lists it as resolved, but its still in Ubuntu 6.06!

--wally.

---

### Post by janbockaert on 2006-09-14
same problem here, i ll trie your fix. Thanks for posting.

---

### Post by wkulecz on 2006-09-14
Unfortunately I can't get the Nvidia proprietary drivers to work now.  I see three different 2.6.15 kernels -23 -25 & -26  Looks like I might need -24 and can't find it.

Ubuntu versioning system needs work!

--wally.

---

### Post by wkulecz on 2006-09-14
Here is the fix for now:

[http://www.ubuntuforums.org/showthread.php?t=257459](http://www.ubuntuforums.org/showthread.php?t=257459)

After doing this I have to boot the 2.6.15-23 kernel that gets setup to get Nvidia driver to work.  I've removed every kernel package newer than this to avoid confusion!


I missed the xserver 10.3 update fiasco because I was not an early Ubuntu adopter, but setting up multiple systems the past two days, this one bit me big time and has pretty much wasted today :(

Two update screw-ups in month, lets hope it stops and modivates some better testing before release!

--wally.

---

### Post by Zyzzyx on 2006-09-15
Ah, timing.

I had JUST opened Update Manager, it was loading as I opened this thread.

Hrmm...  made me think awhile.


<reads the 'fix' thread posted>

Well, looks like things are in hand if I run the updates now.  Guess I'll find out.

---

### Post by wkulecz on 2006-09-15
Did your kernel update work now?  I wouldn't have had a problem if I didn't need the Nvidia proprietary driver.  So if you've upgraded *and* are using the nvidia-glx driver please let me know how it went.

I'd like to upgrade to a 686-smp kernel to take better advantage of my hardware, but my image processing code runs well enough on the 386 kernel with the Nvidia-glx driver.

--wally.

---

