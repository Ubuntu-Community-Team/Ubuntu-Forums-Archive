---
title: "Filter x from apt"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by Joentjuh on 2011-07-23
Is there any way to filter certain packages from apt?
Say, I'm running a headless machine and don't want to install Xorg (accidentally). Can I 'blacklist' the xorg-server package and thus filter all packages depending on xorg? (so they don't even show up in aptitude/'apt-cache search').

Or, in my case, kdebase-runtime and some other things like MTAs.

Not talking about synaptic, but the pure and 'basic' apt (and aptitude) software.
Since you can already 'hold' a package, why not blacklist?
I've seen [somewhere]("http://linux.derkeiler.com/Mailing-Lists/Debian/2009-07/msg00479.html") that this could be done with  /etc/apt/preferences by using "Pin"... But never could get this to work and I'm under the impression this only works if a version of this package is already installed.

I understand I could always write something myself that acts as an intermediary and intercept the Packages file between any PPA/official source and filter any package in my mask -- which seems like a lot of superfluous work, but prevents the system of even knowing there is any such package... But it's not dynamic and thus am hoping something like this already exists.

---

