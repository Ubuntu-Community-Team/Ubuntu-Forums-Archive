---
title: "pre-install questions rh9 to ubuntu"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by syancey on 2007-09-11
I've been using Red Hat 9 for about 4 years now and for at least 2 of those I've been sporadically trying to upgrade some of the libraries, specifically the last 2 weeks glib and gtk so I can run gimp 2+. Everything goes smoothly until I try to install the supporting libs pango, cairo and atk. Especially atk. The terminal window says something about autopackage reading glib 2.12.13, but finding 2.2.8. I have spent hours searching the files and can't find the old version, but it must be there somewhere. All of the other configure scripts found the newest version. I should mention I configured first into the default location, then usr/local with a make clean in between.

I'm tired of going around in circles trying to get this done so I decided to switch to ubuntu. My biggest concern with the install is that the files in my home folder will be lost. Nothing, including the floppy, will mount so I can't back up anything to a cd or flash card. Since I can't burn the install cd I ordered one (hasn't arrived - just want to get everything ready in advance). The strange thing is that even though cds won't mount, I can get the rh install disk to run so I'm pretty confident it will be the same for ubuntu.

Will I lose everything on install? Can I rename the home folder to home-redhat or something? Am I panicking for no reason?

Any suggestions to avoid losing my data are appreciated.

Sharon

---

### Post by merlinus on 2007-09-11
You might use gparted live cd to free up some space on one of your partitions, and copy your /home data there.

Then do not format that partition during ubuntu install.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by reckless2k2 on 2007-09-11
WOW...that is amazing that you are sitll running RH9. that's what i started with. i'm just doing a nostalgia posting. memories. 

and again WOW.....

you are going to be so high on ubuntu coming from rh9..hahaha.

---

