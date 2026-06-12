---
title: "Installing RawTherapee 4.2-2"
date: 2015-06-23
forum: Installation &amp; Upgrades
---

### Post by kf6sgy on 2015-06-23
I'm really sorry if this has been answered. I've read many pages talking about how to install an unstable/testing version of 1 package on a stable release but it seems things within sources.list and apt-pinning might have changed, or I'm simply just misreading.

I'm running Xubuntu Vivid and I want to install RawTherapee from Willy. In sources.list I've attempted to to put "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) willy universe", "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) testing universe", "deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) willy testing". These all fail once I run sudo apt-get update.

Based on this site, [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html), and another, I wrote file /etc/apt/preferences.d/prefernces containing the following:
"Package: *
Pin: release a=stable
Pin-Priority: 700

Package: *
Pin: release a=testing
Pin-Priority: 650

Package: *
Pin: release a=unstable
Pin-Priority: 600"

Even the Ubuntu Documentation on pinning is wrong, it mentions editing /etc/apt/apt.conf which doesn't exist. [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) The Pinning Howto states to create a file within /etc/apt/preferences.d/ for the specific package that's being updated. I'm just not sure how to go about this with so many differing instructions.

---

