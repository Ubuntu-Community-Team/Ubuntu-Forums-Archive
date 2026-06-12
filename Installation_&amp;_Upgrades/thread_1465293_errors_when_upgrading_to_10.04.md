---
title: "errors when upgrading to 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by bonesz on 2010-04-29
I get the following error when attempting to upgrade to 10.04. I also get a popup that tell me that 3rd party sourced will be disabled and can be re-enabled after upgrade message

> W:Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz](http://download.virtualbox.org/virtualbox/debian/dists/lucid/non-free/binary-i386/Packages.gz)  404  Not found
, W:Failed to fetch [http://ppa.launchpad.net/rvm/libs/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/rvm/libs/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/c-korn/vlc/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/do-core/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/gnome-colors-packagers/ppa/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/lucid/main/source/Sources.gz](http://ppa.launchpad.net/anders-kaseorg/subversion-1.6/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.I have been trying to upgrade for over 2 hours without success

---

### Post by tommcd on 2010-04-29
> I get the following error when attempting to upgrade to 10.04. I also get a popup that tell me that 3rd party sourced will be disabled and can be re-enabled after upgrade message

Ubuntu is doing you a favor here by warning you of this.
Note that it is recommended to remove third party repos before doing a dist-upgrade:
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
Almost no one does this though. I believe this is a big reason why so many people have so many problems with dist-upgrades.
I would allow those repos to be disabled. Then add them them back after the upgrade. This will likely be the most fail safe and trouble free method to upgrade to 10.04.
Also, note that you should only do a dist-upgrade from 9.10 to 10.04, and not from earlier versions. Since 10.04 is an LTS release, it is also possible to upgrade from 8.04 LTS to 10.04 LTS.

And welcome to the Ubuntu forums!!

---

