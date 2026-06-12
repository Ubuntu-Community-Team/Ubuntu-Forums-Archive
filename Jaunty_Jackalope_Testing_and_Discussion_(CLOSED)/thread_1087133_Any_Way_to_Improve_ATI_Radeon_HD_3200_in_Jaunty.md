---
title: "Any Way to Improve ATI Radeon HD 3200 in Jaunty"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-03-04
Is there any way to get better performance from my** ATI Radeon HD 3200**?
Under 'Visual effects' I am stuck with 'None'
Any thing on the way to improve this situation?
Thanks

---

### Post by theApokalypsis on 2009-03-04
> **DougieFresh4U said:**
> Is there any way to get better performance from my** ATI Radeon HD 3200**?
Under 'Visual effects' I am stuck with 'None'
Any thing on the way to improve this situation?
Thanks

Coincidence,

I am running a 4870 (R6xx vs R7xx series i believe) and I am curious about getting compiz working on Jaunty.

fglrx (AMD proprietary) is out since they are lacking on the new xserver/xorg support, and I have been very bitter about using it lately and yearn to move back to an open source alternative... 



I dont mean to barge in on the thread :), but i know that recently the radeon-ati driver finally got 2D EXA acceleration for both the new chipsets? or am I mistaken?

Not to knowledgeable on EXA, but to add on to the OP is there any way to get compiz running as of now with the radeon or radeonHD open source driver? or are we still waiting a bit until the full 3d support?

sigh. to boot its the only thing Im waiting on before possibly making the jump.

---

### Post by tormod on 2009-03-15
See [http://ubuntuforums.org/showpost.php?p=6897695&postcount=39](http://ubuntuforums.org/showpost.php?p=6897695&postcount=39)

---

### Post by Yashiro on 2009-03-15
The is no working proprietary driver yet. You are stuck with the open source driver that does not support 3d/Compiz.

In the meantime, I suggest you try out Xubuntu. Even with the open source driver you will get a much nicer experience than with the standard Ubuntu.

---

### Post by theApokalypsis on 2009-03-15
ok, so no 3d support still but its in the works. I have been trying out the radeon (ati) and radeonhd drivers in Jaunty from GIT with the latest DRM module built from the r6xx/7xx origin. 

Radeon Driver:

Latests update got acceleration support. So this means you can play movies with no CPU spikes. Still seems a bit sluggish compared to radeonhd.

Radeonhd Driver:

I am currently running this driver, both have a feature parity pretty much but from testing with the DRM module and this one seems to yeild the best responsivness. 


No to mention that these drivers are more integrated with RanR so creating dual monitor set ups is a HELL of a lot easier (with different resolutions) and also you can actually restart the x server properly... AND no major issues or bugs I can see of, unlike AMD's fglrx crashing all the damn time.

Cant wait to run compiz...

If anyone is interested, below is the how to for building drivers and drm modules from git. there are PPA's out there with GIT builds for jaunty as well


[Configuring Radeon R600/R700 devices on Ubuntu Jaunty]("http://psung.blogspot.com/2009/02/configuring-radeon-r600r700-devices-on.html")


Radeon/Radeonhd development/feature chart
[http://wiki.x.org/wiki/RadeonFeature]("http://wiki.x.org/wiki/RadeonFeature")






EDIT: those PPA's I mentioned, lol they are actually Tormods who I noticed posted above there. :D

---

