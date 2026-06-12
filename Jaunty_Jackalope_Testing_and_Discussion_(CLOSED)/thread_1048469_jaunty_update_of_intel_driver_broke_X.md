---
title: "jaunty update of intel driver broke X"
date: 2009-01-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lorenco on 2009-01-23
I have an 945GM on Thinkpad T60.  After this pm's update of the intel and DRI my X Video get's corrupt (even Terminal sessions)  I have to boot safe then change graphics to device = "vesa" to get an ugly 1024x768 :(

Anyone else out there have issues ?
ii  xserver-xorg-video-intel                       2:2.6.1-1ubuntu1                               X.Org X server -- Intel i8xx, i9xx display driver
?

PS edit:
I did try to go to the old version but it has the same issue, also tried dpkg-reconfigure -phigh xserver-xorg 
Still the same issue...

---

### Post by cyrilougarou on 2009-01-24
Same problem here 

lspci
...
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller 
...



Fresh install of jaunty and dist-upgrade yesterday: screen is blank (with green stripes at the top). I can't login.

---

### Post by impact on 2009-01-24
Jaunty is still not a finished realease so it's pretty obvious things break now and then. If you have decided to test the pre-release version, why don't you post your results in the Jaunty forum or better yet, look for a fix there?

---

### Post by AlexBellisBrown on 2009-01-24
Yup... this should definatly be in the Jaunty Devs forum. Post there and see if they can help. :)

---

### Post by cyrilougarou on 2009-01-24
1) I know it's obvious we have problems with this alpha version.
2) I already reported this bug in the launchpad
3) I always try to communicate my problems or confirm problems and i often get (or give) answers in many places (not only in the launchpad).
4) I dont understand why you remind me such obvious things and can't see any interesting things in your "reply".


Now that obvious things were said, i'd like to say that an update fixed the problem but generated a new one: compiz is slow (first time on an intel card)

---

### Post by Starks on 2009-01-24
Try the following driver in the mean time.

[https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_i386.deb](https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_i386.deb)

or

[https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_amd64.deb](https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_amd64.deb)

---

### Post by klange on 2009-01-24
I believe it's an incompatibility with the current X server and DRM libs. Last I heard, we should wait until a new set of drivers is pushed into the updates in the coming weeks.

Also, there is a dedicated thread for Intel graphics issues: [http://ubuntuforums.org/showthread.php?t=998754](http://ubuntuforums.org/showthread.php?t=998754)

---

### Post by spanishnerd on 2009-02-28
> **Starks said:**
> Try the following driver in the mean time.

[https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_i386.deb](https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_i386.deb)

or

[https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_amd64.deb](https://launchpad.net/%7Exorg-edgers/+archive/+files/xserver-xorg-video-intel_2.6.99.1+git20090102.1f61e979-0ubuntu0tormod_amd64.deb)

Can someone please upload the i386 ver. of the driver? :(

---

