---
title: "Installation issue UEFI related?"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by DracoMaille on 2013-01-25
I recently bought a new rig and I am having some issues getting ubuntu to work on it:

Toshiba Satellite (laptop)
AMD A10-4600 Quad Core w/ Radeon HD integrated   APU
4Gb ddr3 1600
640Gb HDD
UEFI bios

The computer came with Win 8 installed, but I junked it for Ubuntu ... here's the problem ... 

I was playing around with the packages and launch bar, trying to get my desktop to be exactly right for me.  I can't remember all of the packages I worked through, figuring out the best combo for me ... but I do remember that I started having issues after getting rid of several tweak packages.  Whenever I tried to minimize a window, the computer would virtually lock up (any action takes a full minute, even reopening the minimized window).  This occurred with EVERY program I tried, so I thought that it was probably something with the packages I deleted -- i figured reinstall was the best bet.

Reinstalled Ubuntu 12.10 and the wierd stuff started.  I could not change settings (like putting the date in the desktop clock).  I tried a few work arounds, with no success.

Then I tried a fresh install of 13.04 pre-release ... hoping that, if I'm going to face bugs then I'll try to help with the pre-release.  Problem is, my keyboard and touchpad mouse both stopped working -- the computer no longer recognized them -- and I was locked out (the bios still caught the hardware, but not Ubuntu)

So frustrated, and wanting to use my new rig, I downloaded 12.04.1 LTS ... but the secure boot function of UEFI could not load the boot disk (said there was an unrecognized certificate).

I re-downloaded the LTS ISO .. still no love.
I tried turning off the UEFI secure boot ... got halfway through the install, and then system locked, stopped install ... 

[B]EDIT:
[/B]Re-installed Ubuntu 12.10 when I got home from work.  First try did not work ... still same issue with keyboard and mouse not working.  Got frustrated and ate a sandwich, then tried again.  Somehow, everything went as planned.  I installed with no encryption, no LVM, and decided to postpone downloading the updates until after I could get the system up and running.  Got though the install ... and the updates (244 of them) and everything seems to be working well.

---

