---
title: "X broken after Breezy to Dapper upgrade"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by jmelton on 2007-07-28
I upgraded to Dapper Drake today, and it hasn't been altogether smooth.  The first problem was that I ran out of disk space during the upgrade (even though my 2.8gb root partition was only 71% full prior to the upgrade).  Geez, I thought Ubuntu was supposed to be so easy--you'd think there'd be a warning that there was a space problem before apt used up all the space in the partition!  In any case, deleting the cached files from the install took me down to 2.3 gb, and as far as I could tell things were going to run smoothly.

But when I rebooted the system to see if Ubuntu would start okay, I got the following error message: "unable to open /dev/agpgart (no such device)," and as a result X would not start.  I checked /dev and there is in fact a file there named agpgart, so I'm not sure what to make of this.  Is it possible that there's supposed to be another file pointing to this device file that's missing?  Any suggestions for what to do next?  Thanks!

---

### Post by tbroderick on 2007-07-29
What video driver are you using? Try a reinstall of the driver.

---

### Post by jmelton on 2007-07-29
I was actually able to get into X by modprobing agpgart, intel_agp, and drm.  I didn't do an lsmod beforehand, so I'm not sure which of these weren't loaded by the kernel during boot, but I assume agpgart was missing.  To answer your question, my xorg.conf file says my graphics driver is "i810."

But now that I've been able to get back in, I've realized that there are a number of problems with things not being up and running that are supposed to be.  I have no sound, although as far as I can tell the relevant modules seem to be active.  My network connection was not active.  That was easy to fix by turning it on in "networking," but obviously the fact that it wasn't active already when I logged in indicates that something isn't working right during boot.

And oh, I forgot to mention before, the latest kernel version installed, 2.6.15-28, won't work at all.  I get a fatal error message to the effect that it can't find my root partition the moment it starts to boot.  I'm running on kernel 2.6.12-10 instead.

---

### Post by jmelton on 2007-07-29
Well, all I did was reinstall the kernel that wasn't working, 2.6.15-28, and now not only does it boot, but absolutely everything that was broken or not set up at login before is now working perfectly!  

So I gather that what went wrong during the upgrade is that somehow, because I didn't have enough space on my root partition to allow room for both the cached install files and the significantly expanded new version of Ubuntu to fit on it, the download and/or install of the kernels went awry.  

It sort of amazes me that the result was that there was just enough wrong to mess up detection of my sound card, make me fiddle with a few things to get X going, and make me have to turn some things on manually that I shouldn't have had to, but yet for the most part everything worked fine.  I'm glad it turned out to be so simple to fix everything--just reinstall a kernel--but the geek in me wishes I had a little better understanding of what was wrong.  Maybe someone who's more Linux-literate than I am could enlighten me?

---

