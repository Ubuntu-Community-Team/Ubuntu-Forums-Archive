---
title: "Upgrade: Fiesty Fawn Fails Fetch"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by cpk666 on 2007-05-01
[COLOR="Blue"]Trying to upgrade to 7.04 using the update manager, get the following errors:[/COLOR]

Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/Release.gpg](http://www.getautomatix.com/apt/dists/edgy/Release.gpg) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), connection timed out
Failed to fetch [http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix.com/apt/dists/edgy/main/i18n/Translation-en_US.bz2) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (216.120.255.9), connection timed out
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
[COLOR="Blue"]
CK[/COLOR]

---

### Post by AmyRose on 2007-05-01
Automatix is not recommended at all by the Ubuntu team. [https://help.ubuntu.com/community/Automatix](https://help.ubuntu.com/community/Automatix)

Note the warning: *Please note that Automatix2 is a third-party utility, developed and maintained independently by the Automatix Team and is not supported or recommended by Ubuntu.*

You may have to disable the automatix lines in your sources.list or, in a worst-case scenario, do a clean reinstallation of Feisty. Automatix's servers go down a lot, which is part of the reason it's not recommended.

---

