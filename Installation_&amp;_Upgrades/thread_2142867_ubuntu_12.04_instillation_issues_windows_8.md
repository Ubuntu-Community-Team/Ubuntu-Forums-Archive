---
title: "ubuntu 12.04 instillation issues windows 8"
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by mtrmtr on 2013-05-06
Hi, I'm having some trouble installing Ubuntu on my windows 8 hp2000 laptop. I've looked through previous forums and even taking these steps seems not to work. I created a new partition and disabled secure boot and legacy support like some previous posts have recommended. but when I enter my CD with Ubuntu on it, I select the option "install Ubuntu" I am met with sounds from my disc drive for a minute and then a black screen with nothing on it. I've waited for 30 minutes and nothing comes up. I also tried wubi and installed from within windows with no luck. I am met with an error message. I was wondering if I was missing a step or maybe I have to take some additional ones? Thanks for the help.

---

### Post by bcbc on 2013-05-07
Don't use Wubi - it doesn't work on computers that come preinstalled with Windows 8. 

Perhaps you have an nvidia or ati graphics card, in which case [you should use nomodeset to boot]("http://askubuntu.com/q/162075/14916"). Also, if the computer came with windows 8 preinstalled, then follow the instructions here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (that should have the latest), but it sounds like you have that part researched ok, just the nomodeset is required.

---

