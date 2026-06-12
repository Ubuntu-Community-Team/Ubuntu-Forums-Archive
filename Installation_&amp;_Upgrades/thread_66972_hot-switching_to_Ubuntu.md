---
title: "hot-switching to Ubuntu"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by lsiden on 2005-09-19
I've been using Gentoo on this system for several years and have gotten sick of having to rebuild 70 packages when something breaks.  I figure it's time to switch to something that doesn't require so much care and feeding as my Gentoo-based system has.  However, I don't feel like wiping my hard disk just to switch to a different package system.  

Is there some way that I can install the Debian "apt" package system on top of what I already have?  Is there some way that it can build it's package database by taking inventory of what I already have?  Since the  packages are the same - only the way of managing them is different - there should be a way to do this without having to start from scratch again.

---

### Post by Xian on 2005-09-19
You certainly don't have to wipe your HD to install Ubuntu. The install CD includes a nice partitioner so you can dual-boot with another OS. You only need a bit of free space to work with and you're on your way.

But to answer your question, no you can't install the apt package system on top of portage and have it detect your ebuilds so as to begin managing your system via a RPM style database. You could do the reverse (portage on top of apt) but the method you are describing will only lead to a broken installation.

---

### Post by aysiu on 2005-09-19
Theoretically, there may be a way, but...

1. It would probably have to be some kind of custom script. Can you program?
2. It's probably a bad idea, as Gentoo, as I understand it, is custom-built and compiled for your system. Ubuntu is a kind of one-size-fits-most, and their two file systems may not be the same, exactly.
3. How many packages do you have that you can't just take inventory yourself and then "mark for installation" in Synaptic the ones you want in your new Ubuntu installation?

You can always back up your settings and preferences.

---

