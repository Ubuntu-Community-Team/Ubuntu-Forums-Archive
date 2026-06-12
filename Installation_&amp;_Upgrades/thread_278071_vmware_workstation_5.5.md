---
title: "vmware workstation 5.5"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by jnicita on 2006-10-15
I have a handfull of ubuntu installations at work and at home, I also have had no problems installting vmware workstation 5.5.2 build-29772 on them.

Today I tried to instal it on one of the last few machienes that are custom build boxes (i.e. not dells or hp's). So far I got it all installed, but when I try to fire up the virtual machine the sound reports

Failed to open sound device /dev/dsp: No such device
Virtual device sound will start disconnected.

It seems pretty easy as at least the device that it is trying to us doesnt exist, this is the first time I have gotten this error with respect to audio device. I have gotten it with incorrectly auto detected cdroms for instance, and I simply put in the correct /dev/hdc or hdd for my 3rd and 4th hd(x) ide device.

However, Im a little clueless in trying to figure out what audio devices I have, on this particular machine when ubuntu first finished its install it was pointing at a USB audio device and another audio device that was incorrect, why I am not sure, but I was able to use the sound confuration app (I forget which one) and point it to the correct of the 3 devices it had listed and sound for the ubuntu install worked correctly.

Any help on where to start here would be apperciated, as audio/video applications are the only reason to have vmware at this time (slingbox for instance, why those idiots cant make a linux version I wish they would) anyways, any help on where to start will be apperciated... Thanks

---

### Post by Mach1US on 2007-06-07
You can trythis guide
[http://www.slingcommunity.com/articl...r-on-Linux-OS/](http://www.slingcommunity.com/articl...r-on-Linux-OS/)
I have got it up and running , just need to figure out the audio driver problem.
if any know know the fix for that issue plese post to this thread , will be much appriciated.):P

---

