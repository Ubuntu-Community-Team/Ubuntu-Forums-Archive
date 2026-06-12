---
title: "Maverick install issues"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by jasonjob on 2011-02-14
Have been considering moving from Karmic to a newer version for a while, but wasn't too pleased by the teething troubles of my last upgrade, so I've been putting it off.

My / partition screwed up (beyond the ability of e2fsck to repair!), so I decided what the hell, I have to do a complete re-install, why not move along now?  :)

Anyway, a few things have cropped up:

The big one - fglrx.  I have an ATI Radeon 3870 which worked perfectly under Karmic.  I CANNOT get it working under Maverick.  I see from research that this has been a big issue, but also that it is apparently fixed now.  But not for me :(

I have tried the open-source driver (using it right now) - reduced performance, and some of compiz is broken (notably reflection); not sure what else is underperforming, haven't played enough yet.

No matter which method I try (synaptic, apt, additional drivers, downloading from AMD's site), the proprietary driver just won't function.  The best I can get is installing it, but it doesn't appear to be used.  What really ticks me off is that it DID work for an hour or so until I re-started, and since then I can't even get it that far.  I gather that the right combination of Ubuntu kernel and ATI driver works, but I'm not sure which ones I've got, or how to tell.

Moving on...

Is it still possible to have an indicator for sound alone on the Gnome panel, rather than sound and mail?  Preferably one with a vertical slider, ala Karmic?

I use gnome-scheduler to launch deluge at 1 am, close deluge at 6.55 am, and shut down the computer at 7 am.  This now opens a terminal which remains open after deluge has closed - it didn't previously do this.  Is this a new feature, or have I screwed up my attempt to recreate my previous settings?

And just because I detest these sorts of things, how do I (can I??) remove all trace of Ubuntu One?

Glad to see that my dead-slow Firefox now performs as it should again :), and that the buttons are back on the correct side - yay!

Thanks

Jason

---

### Post by An Sanct on 2011-02-14
> **jasonjob said:**
> Is it still possible to have an indicator for sound alone on the Gnome panel, rather than sound and mail?  Preferably one with a vertical slider, ala Karmic?
...
Glad to see that my dead-slow Firefox now performs as it should again :), and that the buttons are back on the correct side - yay!
...
Jason

First :) the buttons are on the left or on the right :) (i would say, on the right is the correct way, but not all agree with me ;))
To change the buttons, press Alt + F2 (run application) and type "gksu gconf-editor", run it, browse to "Apps->Metacity->General" inside, find "button_layout"
(This is just for the next time, you will want to change their layout)

About the indicator search in synaptic for 'Indicator-messages' and remove it, then only the sound indicator will stay. In Maverick, the sound slider is horizontal ...

And for the video, I would try to update everything and then enable the proprietary drivers...

---

### Post by jasonjob on 2011-02-14
That's what I did to start with - clean install, check for updates, install all.    

At that point the graphics were quite slow, so I figured that the open driver was simply inferior to the proprietary one (I don't recall which I was using in Karmic, but I very strongly suspect it was proprietary) and installed it via additional drivers.  Which gave me an ugly text-based splash screen with the boot-up entries showing everywhere, and I could not enable desktop effects.    

At some point during my struggles, it all came together and worked for about half an hour, until I re-booted.  I then spent the better part of two days purging, re-installing and researching, to no avail...    

Buttons on the right for me :)  Thanks for the indicator tip!

---

### Post by QIII on 2011-02-16
After installing the fglrx driver, did you go directly to the terminal and execute

```
sudo aticonfig --initial
```?

The ugly splash will persist,  unless you are willing to take a chance on modifying the way plymouth works -- which is probably more trouble than it is worth for the 5 seconds you see it.

Moving buttons with gconf-editor is not the preferred method.

Look here:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by jasonjob on 2011-02-16
---
After installing the fglrx driver, did you go directly to the terminal and execute

```
sudo aticonfig --initial
```?
---

Yes - I've been through problems with the ATI driver before, so this time I thought I would be clever and follow the guides on the Ubuntu sites.  Still went wrong though :)

---
Moving buttons with gconf-editor is not the preferred method.

Look here:

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)[/QUOTE]
---

Didn't have to move them - I was indeed expecting to need to, but they turned up on the right on install.  Is this the default again?

---

### Post by stereosteve on 2011-02-18
I have problems similar to jasonbob. After many hassles, I finally got my Radeon 3000 (integrated into the mobo) to work correctly and used it successfully for several days.

Yesterday, I applied an update, rebooted and now go to a TTY terminal. After following the guide [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide) and uninstalling fglrx and reinstalling it, I could never execute fglrxinfo (received message that it couldn't open display (null)).

Now, I have disabled xorg.conf (by renaming it) and I have a crude display.

I am reading that xorg.conf is now deprecated and a Kernel Management system is in place. When I try to check that out using dmesg | grep drm, I get nothing. Another symptom pointing to the same thing is that the fglrxdrm module can't be found while starting the X server.

---

### Post by jasonjob on 2011-02-25
Okay, I've fixed most of my issues :)

This web page turned out to be essential: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But only in the last few days - it is NOT the same page as when I installed 10.10 - the thing that tipped me off was the reference to driver version 11.2 - was still on 10.something when last I looked, and had very different instructions.

So, I followed the instructions for option 2 - download and install from ATI  - as far as I could.

You can't identify whether or not your specific card is supported on the AMD page, you just have to hope it is in one of the series listed.

The aticonfig command, it turns out, SHOULD be sudo aticonfig --initial -f (that last -f is vital and made all the difference).

fglrxinfo works ONLY after a restart, and until then will give a segmentation fault, even after you correctly run the aticonfig

There may or may not be a restart required before aticonfig will work; you MUST use "additional drivers" from the Administration menu before anything will work - installing the drivers as above doesn't actually cause your machine to start using them.

Still don't have a pretty start-up splash screen, but I can live without that for now :)  If I feel energetic and adventurous again I might have a play with it, but for now I have what I consider a functioning system.

[EDIT]  DO NOT TRY TO FIX THE DAMNED PLYMOUTH / SPLASH SCREEN
It just doesn't work, and the hassle of finding this out, having a machine that cannot start X and is unresponsive after the failure to start X, and trying to work out just how to fix all this IS NOT WORTH IT!!
There are some aspects of Ubuntu that I loathe every bit as much as Windows, and this is now one of them.

Seriously people, if you WANT Ubuntu to be adopted by the average computer user, get this crap together.  I'm an IT professional and I hesitate to alter the slightest thing for fear that I will spend the next week trying to fix something.  3d video cards are a standard part of any machine the average person buys from a shop, if they can't get it to work then they WILL simply install Windows.

---

### Post by jasonjob on 2011-02-28
And the longer-term result of farting about with updates and the splash-screen is a complete clean re-install.

Installed the ATI driver before(almost) anything else on my clean machine and it works this time:

confirm through Additional Drivers - no proprietary driver
confirm through synaptic - fglrx not installed

install human theme

sudo apt-get install libqtgui4

sudo sh ati-driver-installer-11-2-x86.x86_64.run --buildpkg Ubuntu/maverick

sudo dpkg -i *.deb

FAIL

fix broken package in synaptic

sudo dpkg -i *.deb

sudo aticonfig --initial

REBOOT

fglrxinfo results in:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3870
OpenGL version string: 3.3.10524 Compatibility Profile Context

Appearance - set to EXTRA

Success!

and then

install compizconfig-settings-manager

install compiz-fusion-plugins-extra

which function first time.

Lesson for my next install (think I'll wait until I REALLY have to again) - do the video first, before any other installations mess with something.

---

### Post by jasonjob on 2011-03-21
Update Manager gave me a new kernel.

Video driver fell over with the same problem that caused my re-install - just could not start X after the start-up splash-screen.  Occasionally get the odd glitchy start-up that fails, but works next time - not here, no matter what it won't start except in recovery mode (selecting failsafe graphics)

Going on a hunch, I un-installed the Radeon driver, re-booted with the open driver, re-installed the Radeon driver from scratch (which involved re-compiling a kernel module apparently customised to the kernel at the time - something I spotted by chance during the big re-install), re-booted...

And it worked.  

But it's still just as far from user friendly as I can imagine.  Rebuilding the video driver with every kernel update seems crazy to me - ESPECIALLY IF THERE IS NO DOCUMENTATION OF THIS NEED.

Haven't tried re-starting X while the machine is running yet, and don't care to - just could not get it to do it since installing Maverick.

---

