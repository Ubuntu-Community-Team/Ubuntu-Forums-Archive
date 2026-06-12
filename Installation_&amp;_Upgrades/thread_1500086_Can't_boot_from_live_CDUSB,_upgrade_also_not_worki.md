---
title: "Can't boot from live CD/USB, upgrade also not working"
date: 2010-06-02
forum: Installation &amp; Upgrades
---

### Post by GenBattle on 2010-06-02
I've been having some serious problems with my hardware and this round of Ubuntu. As far as compatibility with my hardware goes, this would have to be the worst round of Ubuntu releases i have ever experienced (and i've been experiencing them since warty).

First I attempted to upgrade my 9.10 install to 10.04, and ended up with an issue where my network card appeared bricked in both Linux and Windows (i'd previously been running 9.10 with no such problems) [http://ubuntuforums.org/showthread.php?p=9354274#post9354274](http://ubuntuforums.org/showthread.php?p=9354274#post9354274)

As i posted in one of the support posts this is a serious hardware issue. The fact that this effectively bricks a piece of hardware is quite scary, especially when it causes problems even if you format (which less determined troubleshooters might do).

Once i got past this issue, i could not for the life of me install a proprietary ati graphics driver on 10.04. Apparently my driver got lost somewhere in the upgrade process, so i reinstalled several times. I also tried reconfiguring xorg and the ati driver, but all i ever got was messages about the driver not existing, even after attempting to install the version from the repository (which also apparently broke the package management system because the driver failed to install properly). I've had problems with low-quality ATi drivers and Ubuntu before, but nothing like this :confused:

Eventually i gave up and tried to reinstall Ubuntu. I set up a USB stick with the 64-bit Ubuntu CD image (using both unetbootin on windows and usb-creator on Ubuntu) but each time I boot my screen simply turns itself off and on repeatedly after showing the boot splash with the progress bar, indicating the signal could be out of range, or that output from the graphics card is completely screwed up. using the ctrl-alt-F keys didn't change the predicament at all, so i can't even access console.
I also tried burning a CD, but the 10.04 upgrade seems to have trashed my Ubuntu install to the point where the CD burning application just eats DVDs and throws errors.

Installing Ubuntu has always required a certain amount of persistence and knowledge, but this time it feels like it doesn't want me back :(

Using:
Intel i5 750 @ 2.66GHz
4GB DDR3-1600
ATi Radeon 5770 1GB

---

### Post by GenBattle on 2010-06-02
Bump.

Looking around this forum, there seem to be alot of posts about boot-time graphics issues with 10.04, but no real solutions... might end up reinstalling 9.10, or installing Mint or something.

by the way, the image i'm trying to boot off is the latest 10.04 x64 live CD

---

