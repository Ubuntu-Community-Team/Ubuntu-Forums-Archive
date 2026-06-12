---
title: "Installing using up-to-date packages"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by mightyiam on 2009-11-17
Dear friends,

I'm looking for a way to make custom installation media which has the latest packages so that the system installed is already up-to-date.

By latest packages I mean packages from the <release>-updates and <release>-security archive sections.

First purpose of this is encountering less bugs during and after installation.

And the second purpose is that I won't have to upgrade packages after installation, or that I won't have to update *as many* packages after installation (depending on the up-to-date-ness of my media).

I think that for me, the best option would be to have all the packages on a USB stick/flash drive. This way it will be a fast installation and the media is very portable. This would require a workaround for systems which can't boot from USB (A custom GRUB CD perhaps?)

A bonus would be for me to learn how to put further packages on the media and have them installed by the installer. I would use this to install extra packages by default like packages from Medibuntu.

---

### Post by phillw on 2009-11-17
Hi,

The alternate install cd may be what you are looking for. I'm not sure how often that image is updated tho'.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Regards,
Phill.

---

### Post by mightyiam on 2009-11-18
> **phillw said:**
> 
The alternate install cd may be what you are looking for. I'm not sure how often that image is updated tho'.

Dear Phill,

Perhaps I didn't explain myself clearly enough.

I'm looking to learn how to make *my own* installation media. While it may be based on the original media, perhaps the alternate CD, it is not just it.

---

### Post by PRC09 on 2009-11-18
Maybe try the daily build for each distro such as:

[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by mightyiam on 2009-11-18
> **PRC09 said:**
> Maybe try the daily build for each distro such as:

[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)
Dear PRC09,

Thank you but it seems that for karmic, the 'release' and 'current' are the same:
[http://cdimage.ubuntu.com/releases/karmic/release/MD5SUMS](http://cdimage.ubuntu.com/releases/karmic/release/MD5SUMS)
[http://cdimage.ubuntu.com/dvd/current/MD5SUMS](http://cdimage.ubuntu.com/dvd/current/MD5SUMS)

---

### Post by phillw on 2009-11-18
> **DawnLight said:**
> Dear friends,

I'm looking for a way to make custom installation media which has the latest packages so that the system installed is already up-to-date.

By latest packages I mean packages from the <release>-updates and <release>-security archive sections.

First purpose of this is encountering less bugs during and after installation.

And the second purpose is that I won't have to upgrade packages after installation, or that I won't have to update *as many* packages after installation (depending on the up-to-date-ness of my media).

I think that for me, the best option would be to have all the packages on a USB stick/flash drive. This way it will be a fast installation and the media is very portable. This would require a workaround for systems which can't boot from USB (A custom GRUB CD perhaps?)

A bonus would be for me to learn how to put further packages on the media and have them installed by the installer. I would use this to install extra packages by default like packages from Medibuntu.

I *think* I may understand what you are wanting .... The Istallation without using internet to get the updates ?  In which case I *think* you want to look at something like APTonCD  [http://blog.dipinkrishna.info/2009/08/aptoncd-create-local-removable.html](http://blog.dipinkrishna.info/2009/08/aptoncd-create-local-removable.html)  gives you an over-view of what it does.

I'm thinking along the lines of alternative cd type install, then run APTonCD to get all the updates / codecs etc - you can then update the image for APTonCD as often as you want

An option to APTonCD is [http://keryxproject.org/](http://keryxproject.org/)  you may want to have a look at that one, also.

Hope this helps,

Phill.

---

