---
title: "no internet: missing xserver-org and ati driver after upgrade to Edgy"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by skryn on 2007-05-25
Hi, I've been having the same kind of problem that a lot of people had, that my graphics card didn't get installed. But xserver-xorg is also missing. I cannot connect to the internet, and am stuck on command line. I do have the CD for Edgy 6.10, but I can't get xserver-xorg to install off of it. 

Tried sudo apt-cdrom add
and then sudo apt-get install xserver-xorg xserver-xorg-video-ati

but there is "no installation candidate" for either.

Typical error messages include: 
Fatal error: no screens found
(EE) No devices detected

is there a way to do this through USB, and download the deb files I need and install them from a USB drive through command line?

---

