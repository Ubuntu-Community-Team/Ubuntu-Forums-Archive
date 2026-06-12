---
title: "After system update hung,&quot;Can't find a source to download&quot; bluez, blocks all installs"
date: 2015-05-01
forum: Installation &amp; Upgrades
---

### Post by mail21 on 2015-05-01
The other day my Ubuntu 14.04 was doing a regular update, when it apparently got stuck.  I regrettably didn't give it much thought at the time.

Since then I can't install anything without getting the errors:

```

E: Can't find a source to download version '5.20+upstream-201504030131~rev17820~pkg9~ubuntu14.04.1' of 'bluez:amd64'
E: Can't find a source to download version '5.20+upstream-201504030131~rev17820~pkg9~ubuntu14.04.1' of 'bluez:amd64'
E: Internal error: couldn't generate list of packages to download

```

I don't need Bluetooth support, so I first thought to simply remove the package, and found it wanted to also then remove gnome-shell and friends, like reported on the thread [Installing Bluez 5.x in Ubuntu(with Gnome 3.10)]("http://ubuntuforums.org/showthread.php?t=2185088").   And, even then, I can't remove it anyway, given:

```

dpkg: error processing package bluez (--remove):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting a removal
Errors were encountered while processing:
 bluez
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

... so I can't reinstall it (and don't care to have it anyway, beside the point) and I can't remove it.  Not sure how I would have ended up with a broken package on my system I don't have the sources for, I nonethless peeked in `/etc/apt/sources.list.d` and found a `vidplace7-bluez5-trusty.list` file with:

```

deb http://ppa.launchpad.net/vidplace7/bluez5/ubuntu trusty main

```

Yet, I don't see that in the list when I run `aptitude update`, as I thought I understood I should.

Thanks in advance for any hints.

---

### Post by mail21 on 2015-05-01
Solved my own problem.  Still would have to learn more to know how this happened, but all I needed was `apt-get autoremove`

---

