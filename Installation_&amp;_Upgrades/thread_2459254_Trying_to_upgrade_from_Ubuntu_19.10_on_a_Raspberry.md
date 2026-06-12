---
title: "Trying to upgrade from Ubuntu 19.10 on a Raspberry Pi 4"
date: 2021-03-14
forum: Installation &amp; Upgrades
---

### Post by taumu on 2021-03-14
I think the issue is the /etc/apt/sources.list. I get the error when trying to upgrade this distro.

```
sudo do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife


Please install all available updates for your release before upgrading.



```

My sources.list is

```
deb http://ports.ubuntu.com/ubuntu-ports focal main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal-updates main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal universe
deb http://ports.ubuntu.com/ubuntu-ports focal-updates universe
deb http://ports.ubuntu.com/ubuntu-ports focal multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-updates multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-backports main restricted universe multiverse
deb http://ports.ubuntu.com/ubuntu-ports focal-security main restricted
deb http://ports.ubuntu.com/ubuntu-ports focal-security universe
deb http://ports.ubuntu.com/ubuntu-ports focal-security multiverse

```

Googling a bit, it seems that the issue might have been that the release is not supported anymore and the repositories have been moved? So some suggests that any ubuntu.com repos should be renamed to old.ubuntu.com, but I am not sure how that works for ports.ubuntu.com. Does anyone know what a correct sources.list should look like so the distro can be upgraded. I would like to upgrade to 20.04 or 20.10. This is on a Raspberry Pi 4 with 4GB, so I have a 32 bit version.

```
#uname -a
Linux raspberry-pi-1 5.3.0-1030-raspi2 #32-Ubuntu SMP Sun Jul 12 21:23:11 UTC 2020 armv7l armv7l armv7l GNU/Linux

```

---

### Post by grahammechanical on 2021-03-14
I do not think that the old-releases method will work. I am guessing  that you have Ubuntu Touch from Ubports. Upgrades should come from  Ubports. I am thinking that upgrades come though what are called Over  The Air Upgrades (OTA)

[https://ubports.com/blog/ubport-blogs-news-1/post/ubuntu-touch-ota-14-release-3728](https://ubports.com/blog/ubport-blogs-news-1/post/ubuntu-touch-ota-14-release-3728)

How did you install Ubuntu Touch on this device? Did you follow these instructions?

[https://ubports.com/blog/ubport-blogs-news-1/post/raspberry-pi-114](https://ubports.com/blog/ubport-blogs-news-1/post/raspberry-pi-114)

There is a version of Ubuntu for the Raspberry Pi that is supported by Ubuntu developers.

[https://ubuntu.com/raspberry-pi](https://ubuntu.com/raspberry-pi)

Regards

---

### Post by guiverc on 2021-03-14
I'll provide the standard link for EOL Upgrades

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

It'll explain what you ordinarily do, however like @grahammechanical, I'm not sure it will help you as you're using a PORT of Ubuntu and not a mainstream Ubuntu.  (I've never tested it with a ports system)

Changing all *eoan* to *focal* is a debian approach to upgrades; it works for Debian yes, and sometimes for Ubuntu, but Ubuntu makes a lot more use of python & other tools, and thus the `do-release-upgrade` adds an order to the process that ensures the system will boot & be stable post-upgrade (not needed for Debian)

There was a specific bug that prevent 19.10/eoan from upgrading once EOL was passed; (a file had been failed to be moved (or been wrongly erased) thus preventing the upgrade from being seen as possible; this has since been fixed for the mainstream systems.  I had a look for the bug & traces but failed to find it (to remind myself of details), but maybe that wasn't fixed for ports....

Later add:  *this is some of what I was searching for - [https://discourse.ubuntu.com/t/no-release-file-for-eoan-in-old-releases-ubuntu-com/19817](https://discourse.ubuntu.com/t/no-release-file-for-eoan-in-old-releases-ubuntu-com/19817) but it's still missing the Canonical fix part of the equation that occurred on launchpad or the like (too long ago for me to remember & I get too many hits on my emails to find it)*

---

