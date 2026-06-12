---
title: "Is KDE 4.4 RC1 Desktop Effects (OpenGL composting) an issue for anyone else?"
date: 2010-01-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2010-01-20
Is anyone else having a problem enabling OpenGL composting in the desktop effect options via the latest KDE 4.4 RC1? It happened to stop working during the Mesa changes, but with a number of updates to the mesa packages since it doesn't seem to be working again, whilst everything else now is. I'm just wondering if someone else is having the same problem, because I appear to be the only person who has reported back on this forum about this.

Screenshots of the problem are available via the attachments below, but that is what happens when I attempt to start Desktop effects for OpenGL. XRender works, but causes a number of VSync problems in 3D programs and doesn't work with full-screen video.

I've deleted the configuration files for KWin with no cure. I've also tried both Sevenmachines NVidia 195.22 drivers from the relevant PPA and the NVidia 190.53 drivers in the repositories with no luck. OpenGL composting has always worked on this machine up until last week.

A bug report via Launchpad has been raised on this, but its either being given little or no attention (for whatever reason) or parts of it are being quickly marked as invalid.

---

### Post by VMC on 2010-01-20
Mine works on an Intel i865 video chip:


What video graphics do you have?

---

### Post by tghe-retford on 2010-01-20
```
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GT] (rev a2)
```
I have a Zotac 8800GT AMP Edition 512mb GDDR3 Dual DVI PCI-E Graphics Card and I am using Sevenmachines 195.22 NVidia drivers from the NVidia PPA, because it works with Wine and 3D applications.

As I mentioned, OpenGL composting worked fine on this system before the mesa changes, and I am a bit puzzled why barely anyone else is having the same problem.

---

### Post by Universal344 on 2010-01-20
I guess I am lucky.  In the past I have had to resort to fglrx (*throws up a little in mouth) but with an update a few weeks ago I have full 3D compositing using only the radeon open source drivers.  However, I have had odd graphical glitches (with and without compositing) where colored squares will appear on screen.  I don't think I killed my graphics card because they always appear around specific objects and never randomly in the middle of the screen.  I am starting to think its Qt as it doesn't seem to happen in GTK+ apps.  Does anyone else have this issue?

P.S. already tried reinstalling right after alpha 2 released.

---

### Post by tghe-retford on 2010-01-24
Did a complete reinstall of Lucid to the latest daily, and it _still_ doesn't work! Still, nice to have a fresh install and to clear out the clutter.

---

### Post by xebian on 2010-01-24
No problem here.  nvidia 7300, 950.30 from nvidia.

I have KDE SC 4.4 RC2 though.  Why don't you upgrade now?

---

### Post by tghe-retford on 2010-01-24
> **xebian said:**
> No problem here.  nvidia 7300, 950.30 from nvidia.

I have KDE SC 4.4 RC2 though.  Why don't you upgrade now?
I've already reinstalled from the daily Kubuntu alternate image and updated today. I do have KDE 4.4 RC2 installed and yet it still fails to work. Bare in mind before the mesa updates, OpenGL composting always worked on this system. Nothing has changed in terms of hardware.

---

### Post by xebian on 2010-01-24
Can someone tell us how to embed the image instead of attachment?  TIA

---

### Post by xebian on 2010-01-24
> **tghe-retford said:**
> I've already reinstalled from the daily Kubuntu alternate image and updated today. I do have KDE 4.4 RC2 installed and yet it still fails to work. Bare in mind before the mesa updates, OpenGL composting always worked on this system. Nothing has changed in terms of hardware.

I don't trust those dkms, modaliases, etc.

Get rid of all those modaliases*, dkms, jockey* and install directly from the NV driver.

---

### Post by tghe-retford on 2010-01-24
Just to clarify with the attachment below (a picture tells a thousand words), RC2 is clearly installed and when I try to activate the OpenGL composting, this popup will appear telling me that it cannot activate any of the effects:

---

### Post by xebian on 2010-01-24
> **tghe-retford said:**
> Just to clarify with the attachment below (a picture tells a thousand words), RC2 is clearly installed and when I try to activate the OpenGL composting, this popup will appear telling me that it cannot activate any of the effects:

It means your driver is not set properly.


[ATTACH]144825[/ATTACH]

---

### Post by tghe-retford on 2010-01-24
> **xebian said:**
> It means your driver is not set properly.


[ATTACH]144825[/ATTACH]
The thing is, I am using sevenmachines PPA (nvidia-glx-195) because it works with Wine 3D and native 3D applications. The nvidia-current NVidia drivers from the Ubuntu repositories don't work at all with OpenGL composting, Wine 3D or native 3D applications. But what is puzzling me is how I appear to be the only one with problems with the drivers on this forum whilst others are suggesting that either the official or sevenmachines PPA drivers do work fine with KDE 4.4 RC1/2.

I thought that the usual fix for unique problems, reinstall Kubuntu and start afresh would work, alas it hasn't and the bug still persists even with a fresh reinstall.

---

### Post by buzzmandt on 2010-01-24
i'm using nvidia drivers from nvidia.com and i have no prob at all.  kde rc2 is awesome here.  geforce 5500 fx

---

### Post by autark on 2010-01-24
To be honest, I haven't been able to see the KDE desktop on this machine in Lucid at all, everything is black after the splash screen is finished. My other machine does it fine. This machine has nvidia graphics, the other machine has intel.

---

### Post by xebian on 2010-01-24
> **autark said:**
> To be honest, I haven't been able to see the KDE desktop on this machine in Lucid at all, everything is black after the splash screen is finished. My other machine does it fine. This machine has nvidia graphics, the other machine has intel.

This has been the issue in the early days. IMHO A2 already fixed this.

---

### Post by tghe-retford on 2010-01-25
We'll, now we have an interesting proposition. You have a choice:

Using nvidia-current, OpenGL compositing will work (hooray!) but 3D applications will not.
Using Sevenmachines PPA, OpenGL compositing will not work but 3D applications will.

The joys of testing, eh?

---

### Post by autark on 2010-01-26
> **xebian said:**
> This has been the issue in the early days. IMHO A2 already fixed this.

My bad. I didn't have all the needed KDE packages installed.

---

