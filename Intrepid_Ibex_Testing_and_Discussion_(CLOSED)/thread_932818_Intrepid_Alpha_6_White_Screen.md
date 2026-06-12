---
title: "Intrepid Alpha 6 White Screen"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by keenish27 on 2008-09-28
I tried to install Alpha 6 of Intrepid, however when I boot the cd I get a white screen.  This happens after the splash screen loads.  I then tried to boot in safe graphics mode and I get the same problem.  So I downloaded the alternate install cd.  It installed fine.  However, whenever I boot to Inrepid I once again get a white screen.  I know the login screen is loaded because of the little jingle that plays when the login screen loads.  However I have a completely white screen and can't do a thing.  Any ideas on how to fix this.  I'm running an ATI Radeon HD2900.  Also both monitors are connected via DVI cables.  Any help is appreciated.

---

### Post by UbuWu on 2008-09-29
Might be this bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/267185](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/267185)

If it looks like it is the same to you please comment there also adding your findings and logfiles.

---

### Post by sdowney717 on 2008-09-29
likely due to you using a very modern ATI card which is not going to work right now with xorg 7.4 and xserver 1.5 which are in Ibex.

Although I would think it should work with the free radeon driver.
I just went thru this white screen of death with an older x1300 pro.
I finally manged to switch to the free radeon driver which supports r515 chipset. ATI fglrx drivers are a pain. But I suppose when they work they are fast.

---

### Post by keenish27 on 2008-09-29
Thanks for the responses.  I don't know if it is a driver issue.  I mean I didn't get a chance to update to the fglrx drivers.  Usually vesa works with all.  Also I did have Hardy installed on this same machine with no problems.  When I get home from work I will post my log files on the bug report page.

---

### Post by UbuWu on 2008-09-29
Fglrx is currently not available on intrepid. The ati driver should work for your card though.

---

### Post by keenish27 on 2008-09-29
Well I was finally able to get intrepid to boot up without the white screen.  What I had to do was go into the xorg.conf and actually add ad driver entry under the configured video device section.  I was able to get "vesa" to work, however my resolution was way off.  Other than that the only driver I was able to get working was "radeonhd".  Guess I"m gonna have to wait till fglrx drivers are out.

---

### Post by UbuWu on 2008-09-30
Did you file a bug?

---

### Post by keenish27 on 2008-09-30
I'm going to.  I didn't get a chance to last night.  Took me quite a while to get up and running.  When I get home from work tonight I'm going to.

---

