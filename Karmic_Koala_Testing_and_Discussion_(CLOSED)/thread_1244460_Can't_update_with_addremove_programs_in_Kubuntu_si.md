---
title: "Can't update with add/remove programs in Kubuntu since this morning"
date: 2009-08-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Arla on 2009-08-19
After downloading the latest updates this morning, I now get the following error message when I try to search for new programs with the add/remove program option.

Error Type: Error Value: 'PackageKitCache' object has no attribute '_dict' File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1966, in main() File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1963, in main run(args, options.single) File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 1925, in run backend.dispatcher(args) File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 632, in dispatcher self.dispatch_command(args[0], args[1:]) File : /usr/lib/python2.6/dist-packages/packagekit/backend.py, line 599, in dispatch_command self.search_name(options, searchterms) File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 542, in search_name for pkg in self._cache: File : /usr/share/PackageKit/helpers/apt/aptBackend.py, line 196, in __iter__ for pkgname in sorted(self._dict.keys()): 

Sudo apt-get install still seems to work just fine.

How does one get the latest updates using Sudo apt-get since I will need to do that until this is fixed?

---

### Post by fifth on 2009-08-19
Glad its not just me :D

[http://ubuntuforums.org/showthread.php?t=1243694](http://ubuntuforums.org/showthread.php?t=1243694)

Out of curiosity, have you rebooted since the update?

---

### Post by Arla on 2009-08-19
Have now (and still have the same issue), the one thing I do notice is that when I was running Ubuntu 9.10 I was on the -6 version of the kernel, where it seems to be on -5 for Kubuntu, not sure if that's important or not.

sudo apt-get upgrade and sudo apt-get update still seem to work, so it's really just the graphical interface that isn't working right now.

---

### Post by ezsit on 2009-08-19
> How does one get the latest updates using Sudo apt-get since I will need to do that until this is fixed?

sudo apt-get update
sudo apt-get upgrade

The first command updates the repositories and the second command upgrades all available software to the latest versions.

---

### Post by Arla on 2009-08-19
Thanks, I've played a bit and since decided I'm going to stick with Ubuntu for now, I found KDE very slow to startup, and not really worth the extra effort for the one program I like from it (digiKam) so I'll just use digiKam under Gnome.

I've been running into a number of update issues the last day or so (having re-installed Ubuntu, and installed all the latest updates, I kept getting gdebi crashes when trying to install trueCrypt).

---

