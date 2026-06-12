---
title: "Karmic RC installation on VMware Fusion - tools"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mfox on 2009-10-23
Here is a bit of information that might help Mac users with a Karmic virtual machine installed with VMware Fusion.  I did two such installations since RC came out.  The first was with VMware Fusion 2.0.6 on a Mac mini.  The good news is that the xorg problem that resulted in a black screen after installing vmware tools with the Karmic beta is no longer a problem.  The bad news is that not all the tools work with the 2.0.6 tools package.  The one in particular that doesn't is drag and drop from Mac to virtual machine, though you can drag and drop the other way.  However, I did a second installation using the VMware Fusion 3 beta.  Although a lot of error-type messages flashed by during the tools installation, all the tools seem to be working, including drag and drop from Mac to vm!  I'm going to see if the Fusion 3 tools can be carried over to 2.0.5 by copying them onto a USB stick and moving them into the 2.0.6 vm.  Meanwhile, it's at least good news to know that upgrading to Fusion 3 will give you a fully functional tools package for Karmic.

Two other notes for installing Karmic on a Fusion vm.  First, I found that I had to do the installation from a live image; booting up the image and attempting to install directly from the menu without running Karmic in the live image didn't work.  The second is that I continue to have a sound problem in Karmic that I never experienced in previous Ubuntu versions, with the sound playing mp3's and mp4's being slow-motion and with low pitch.  Removing pulse-audio and gstreamer pulse-audio solves the problem.

I hope this information helps some of you Mac users who like Ubuntu.

---

### Post by uselpa on 2009-10-24
Thanks for the typ regarding the removal of pulseaudio, worked perfectly!

---

