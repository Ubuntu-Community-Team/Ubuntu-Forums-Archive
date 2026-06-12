---
title: "Fix Broken Package"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by khabib on 2007-02-08
Dear Ubuntu-ers,
I am a newbie and just a user of Ubuntu. Ihad problem after trying to install xCHM for Debian from [http://packages.debian.org/unstable/x11/xchm](http://packages.debian.org/unstable/x11/xchm). It requires many nested dependency, and I decided to cancel installation.
A problem came when I want to update package from Synaptic.  I got message that it cannot proceed and I had to do fixing by running "sudo apt-get install -f".
When I did it, I got error as follows:

[FONT="Courier New"]
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 libc6: Depends: tzdata but it is not installable
 libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-11 is
installed
 libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20.4) but 2.3.6.ds1-11
is installed
 libgcc1: Depends: gcc-4.1-base (= 4.1.1-21) but it is not
installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be
caused by held packages.
E: Unable to correct dependencies[/FONT]


could you please let me know how to resolve this problem?
How to find a "broken" package through synaptic and fix it?

Thankx

---

### Post by rtmie on 2007-02-09
Try:

sudo dpkg --configure -a

---

### Post by khabib on 2007-02-09
> **rtmie said:**
> Try:

sudo dpkg --configure -a

Thanks for the suggestion, but it seems not working.  The error still persists. Hope other suggestion will soon come :)

---

### Post by rtmie on 2007-02-09
It looks like there is a problem with the version of libc6 you have installed, you may have gotten this as a dependency of your attempted xCHM install. Not really sure what you can do here. Perhaps try:
sudo apt-cache --reinstall install libc6


Rob

---

