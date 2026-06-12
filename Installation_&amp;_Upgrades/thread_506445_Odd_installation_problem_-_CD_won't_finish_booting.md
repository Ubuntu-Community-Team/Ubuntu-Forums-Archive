---
title: "Odd installation problem - CD won't finish booting"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by RN3AOH on 2007-07-21
Here I have a fairly old laptop, with only 128 megs of RAM and a small HD, but a fairly fast CPU for the era (1200MHz). The thing's not mine, thankfully, and I promised to help with installing Linux on it.

First, I plugged it into my cluster and built Gentoo for it, but I always have problems properly setting up laptop hardware, so I decided to go the easy route -- the owner will have a hard time handling Gentoo, and with such a low spec machine, it only really makes sense when you have a distcc cluster to update, so I went with Xubuntu instead. Mind you, Gentoo worked on this machine for a week, compiling itself, so I have no reason to believe it's just broken.

First time I put the Xubuntu CD in, it booted fine, and I thought the problems were over, but they weren't -- the installer kept complaining that it can't create the partitions it wants, no matter what kind of partitioning I chose.

Ohwell, I thought, booted my Gentoo install CD and removed all the partitions.

Then the Xubuntu CD stopped booting at all. That is, by the time it actually starts X, the system seems to be completely frozen, with infrequent bouts of CD activity. I could not get it to finish booting to let me get at the installer a second time, at all, no matter what I did to HD partitions -- created new ones, removed them, et cetera. Same happens when I select the safe mode option.

I have tested the CD from the boot menu and it tells me it's fine.

What gives?

---

### Post by davidjmayo on 2007-07-21
A few suggestions

1 is the live CD OK (did you check MD5sum and/or use it in another computer to ensure it's good)

2 Even if the CD is OK live Cd has been known to be awkward. I never tried to install Xubuntu but I know ubuntu or kubuntu will (maybe) run on 128MB RAM but need 192MB for the install

3 Try the alternate CD which is text based so uses less sys resources

Note: as to 2 & 3 I have 256 RAM and couldn't get live cd to work on a basic machine (no add on video or sound cards)

4 if all that fails consider DSL( damn smal llinux) or puppy linux or any other lightweight version you know of instead

---

### Post by RN3AOH on 2007-07-22
The third approach, using the alternate CD sorta helped -- that is, it got halfway through the installation and then locked up when configuring anthy (which I'm not even sure is needed there, but it never asked me...)

I'm currently trying to install a commandline system and then build it up to X once it's actually running. What would be the packages I need to install for this to be a full xubuntu installation?

---

### Post by davidjmayo on 2007-07-23
> **RN3AOH said:**
> The third approach, using the alternate CD sorta helped -- that is, it got halfway through the installation and then locked up when configuring anthy (which I'm not even sure is needed there, but it never asked me...)

I'm currently trying to install a commandline system and then build it up to X once it's actually running. What would be the packages I need to install for this to be a full xubuntu installation?

If you want to do it that way use the server cd not the desktop cd. You can then add Xfce (Xubuntu X front end) like this [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

I know the link says adding XFCE to ubuntu or kubuntu but it;s the same principle.
Also look in the playing around section on the left of the psychcats page

As to number 4 in my previous post look at the bottom of the page linked above

HTH
David

---

