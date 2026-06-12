---
title: "Problems with ati drivers, envy, computer booting  and video..."
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by hoti0101 on 2008-07-07
Sorry if this has been posted before, I have been searching but was unable to find anything.  I am a noob to ubuntu, but ever since (try to) upgrade my video card driver, things have started to not work so well.

I had a working (quite well) ubuntu 8.04 desktop and clicked an icon that said I haven't installed restricted drivers for my video card (ATI Firegl X2 256).  I decided to give it a shot even though I know ATI drivers have had problems in the past.  It installed and when it rebooted my desktop wasn't available (blank screen).  I ctrl-alt-del to reboot, and ran a few commands to redo what I did (don't remember what, got help from the forums).  

While I was searching for an answer I ran across Envy and decided to try that.  Ever since installing it my desktop only boots into a visible desktop 1/4 the time and I can't see video on any movie files I have (sounds plays just fine, codecs have been installed).  I did uninstall Envy once and try to use the default display, but it was much worse than before, so I tried to reinstall Envy again with the same results.  The Envy drivers appear to be working, since the 3D is much better than it used to be. 

Any idea how to get my desktop to boot every time?  What is up with the movie files not displaying (they are playing, I can here them!)?  I know I am an idiot for not backing up my xorg.conf file and for messing with a perfectly good desktop (I was curious).  Help would be mucho bueno.

---

### Post by VitaLiNux on 2008-07-07
> **hoti0101 said:**
> Sorry if this has been posted before, I have been searching but was unable to find anything.  I am a noob to ubuntu, but ever since (try to) upgrade my video card driver, things have started to not work so well.

I had a working (quite well) ubuntu 8.04 desktop and clicked an icon that said I haven't installed restricted drivers for my video card (ATI Firegl X2 256).  I decided to give it a shot even though I know ATI drivers have had problems in the past.  It installed and when it rebooted my desktop wasn't available (blank screen).  I ctrl-alt-del to reboot, and ran a few commands to redo what I did (don't remember what, got help from the forums).  

While I was searching for an answer I ran across Envy and decided to try that.  Ever since installing it my desktop only boots into a visible desktop 1/4 the time and I can't see video on any movie files I have (sounds plays just fine, codecs have been installed).  I did uninstall Envy once and try to use the default display, but it was much worse than before, so I tried to reinstall Envy again with the same results.  The Envy drivers appear to be working, since the 3D is much better than it used to be. 

Any idea how to get my desktop to boot every time?  What is up with the movie files not displaying (they are playing, I can here them!)?  I know I am an idiot for not backing up my xorg.conf file and for messing with a perfectly good desktop (I was curious).  Help would be mucho bueno.

Well, friend, I haven't had an Ati card so far, but it could be helpful for you:
>  Re: getting ATI drivers working, can't get rid of Mesa
Well, I've found a way to make it work.

Were's how I've done it:

I did a Ubuntu 8.04 fresh install, and then used the "Add and Remove" under "Applications" and selected a package named: "ATI binary X.Org driver" and installed it. After doing so, I've selected "System / Administration / Hardware Drivers" and enabled the "Ati accelerated graphics driver" and rebooted the machine. And this was the output of # fglrxinfo:

display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7412 Release
__________________
----------------------------------------
Asus A6VA
Ubuntu 8.0

---

