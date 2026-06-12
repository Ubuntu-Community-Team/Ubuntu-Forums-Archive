---
title: "Networkless install -- use alternate cd?"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by sadscientist on 2006-07-11
I have a couple of questions:

I just installed ubuntu-server, and tried a "sudo apt-get kubuntu-desktop" and was told kubuntu-desktop was an unknown package.

I'm thinking this is probably because my network wasn't set up during the installation, and I'm not sure how to configure it now, from the terminal.  (Or maybe I had the package name wrong?)

I'm tempted to just wipe my installation and reinstall everything using the desktop cd or alternate cd .. I think the desktop cd is what I wanted to install with in the first place, except that I didn't want to deal with the liveCD stuff.

Anyway.. one question is, will the desktop-cd install cleanly without a network connection?  (I'm confused about why the automatic configuration failed during the install last time.. since, this is the same computer and obviously the connection is working.  I'm using the DHCP server from my router to get my network info.. but unbuntu's installer claimed I "probably wasn't using DHCP"..)

Also, I tried a "sudo ifup eth0" and it said eth0 was an unknown device..  even if it's not "configured", shouldn't it be *known* just as a piece of hardware that's stuck in there?

---

