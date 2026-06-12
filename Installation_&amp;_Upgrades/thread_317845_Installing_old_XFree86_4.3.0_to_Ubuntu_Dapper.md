---
title: "Installing old XFree86 4.3.0 to Ubuntu Dapper"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by vemon on 2006-12-13
Hi!

The question:

Is there a way to install XFree86 4.3.0 to Ubuntu Dapper as a ubuntu package? I found that version of XFree from Hoary universe  repository with the name "xserver-xfree86". Can there be any complication when installing that package to Dapper or is it even possible? My need for X is very simple: just running mplayer. I will probably not even need a window manager.

Background / Problem:

I'm building a HTPC on top of Fujitsu-Siemens Activy 300 Mediacenter PC which has a display adapter (SGI/TVIA CyberPro5000) that only works with X using a closed source driver module from TVIA. The driver happens to be compiled against XFree86 4.3.0 and because of that doesn't work with the X.org shipped with Ubuntu Dapper.

For the record:

---

### Post by an.echte.trilingue on 2006-12-13
I would really strongly recommend that you use debian sarge to do this.  It has XFree86 4.3.0 by default, I would wager that it will be supported for a lot longer than Dapper, and by using apt-pinning you can still update to etch or simply install a few packages from the etch repositories without un-installing XFree86.  Be sure to grab an install CD for "stable" before etch gets released later this month.

Just my two cents.

Take care,
-mat

---

### Post by vemon on 2006-12-13
Thank you, maybe I'll try sarge.

Do you know how good is sarge's support for WiFi? I have a brand new 54G USB WLAN -stick and i'd like to use it in the HTPC. One of the reasons I deployed Dapper to the machine was that I have some experience in setting up 54G wlan with it.

... of course it mostly depends on the kernel and I am well able to compile my own when needed. Still it would save a lot of time if the distro would have out of the box (or at least near out-of-the-box) support for my 54G WLAN USB stick and for wireless devices in general.

---

### Post by vemon on 2006-12-14
I installed sarge and got XFree86 4.3.0. It was also really painless to install mplayer via the debian-multimedia -repositories. Thank's for the advice!

Unfortunately I only get blue screen when playing video with mplayer using the tvia driver so the installation didn't bring me any additional value...

---

### Post by an.echte.trilingue on 2006-12-15
Sorry I did not check in in a couple days.

Are you sure that the blue screen is the driver's fault?  I wouldn't give up just yet.  Try installing a DE to see if it is all video output or just mplayer that is causing this.  It is probably an mplayer configuration problem, IMO.

---

