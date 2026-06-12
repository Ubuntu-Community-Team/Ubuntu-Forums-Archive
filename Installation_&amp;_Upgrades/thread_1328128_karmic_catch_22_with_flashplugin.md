---
title: "karmic catch 22 with flashplugin"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by gwm on 2009-11-16
Hi,
I upgraded last night and have a catch 22 error.
synaptic tells me that flashplugin is broken.
I can't remove the package, because it isn't there and I can't install it because it is there but broken.
I've deleted every file I can find on my system that has flashplugin as part of it's name. I've done all the apt-get and dpkg things I can find on the forum. still I have this problem.

Where is this information stored so that I can go there and manually remove all reference to this package? Then perhaps I can do a clean install.

apt-get tells me:
Package adobe-flashplugin is not installed, so not removed

and then it says:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed

the full exchange is:
> sudo apt-get remove --purge adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Where is this information stored so that I can go there and manually remove all reference to this package? Then perhaps I can do a clean install.

Any help would be appreciated

---

### Post by slakkie on 2009-11-16
You might want to have a look here: [http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/](http://blog.opperschaap.net/2009/11/13/upgrade-flash-on-ubuntu-after-a-release-upgrade/)

---

### Post by gwm on 2009-11-16
Thank you Slakkie,
That did it!
All I needed was to add the following line to /etc/apt/sources.list

> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

:p :D :) :P

---

