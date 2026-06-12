---
title: "apt-get update"
date: 2022-09-12
forum: Installation &amp; Upgrades
---

### Post by klapvogn on 2022-09-12
Hello, 

Im getting this with ```
apt-get update
```
[IMG]https://i.imgur.com/nDyASmD.png[/IMG]

What do I need to do to get rid of this

Here is my source.list

```

deb http://mirror.hetzner.com/ubuntu/packages impish main restricted universe multiverse
deb http://mirror.hetzner.com/ubuntu/packages impish-updates main restricted universe multiverse
deb http://mirror.hetzner.com/ubuntu/packages impish-backports main restricted universe multiverse
deb http://mirror.hetzner.com/ubuntu/packages impish-security main restricted universe multiverse
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ impish main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish main restricted


#  # Major bug fix updates produced after the final release of the
#  # distribution.
deb http://de.archive.ubuntu.com/ubuntu/ impish-updates main restricted
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish-updates main restricted


#  # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
#  # team, and may not be under a free licence. Please satisfy yourself as to
#  # your rights to use the software. Also, please note that software in
#  # universe WILL NOT receive any review or updates from the Ubuntu security
#  # team.
deb http://de.archive.ubuntu.com/ubuntu/ impish universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish universe
deb http://de.archive.ubuntu.com/ubuntu/ impish-updates universe
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish-updates universe


#  # N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
#  # team, and may not be under a free licence. Please satisfy yourself as to
#  # your rights to use the software. Also, please note that software in
#  # multiverse WILL NOT receive any review or updates from the Ubuntu
#  # security team.
deb http://de.archive.ubuntu.com/ubuntu/ impish multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish multiverse
deb http://de.archive.ubuntu.com/ubuntu/ impish-updates multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish-updates multiverse


#  # N.B. software from this repository may not have been tested as
#  # extensively as that contained in the main release, although it includes
#  # newer versions of some applications which may provide useful features.
#  # Also, please note that software in backports WILL NOT receive any review
#  # or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse


#  # Uncomment the following two lines to add software from Canonical's
#  # 'partner' repository.
#  # This software is not part of Ubuntu, but is offered by Canonical and the
#  # respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu impish partner
# deb-src http://archive.canonical.com/ubuntu impish partner


deb http://security.ubuntu.com/ubuntu impish-security main restricted
# deb-src http://security.ubuntu.com/ubuntu impish-security main restricted
deb http://security.ubuntu.com/ubuntu impish-security universe
# deb-src http://security.ubuntu.com/ubuntu impish-security universe
deb http://security.ubuntu.com/ubuntu impish-security multiverse
# deb-src http://security.ubuntu.com/ubuntu impish-security multiverse

```

UPDATE:

Found out i was on a old release, but I'm afraid to do a distro update, when I did something last time it ruined something up :-(

---

### Post by Impavidus on 2022-09-12
It's indeed an old release, but only one step away from the latest supported release (22.04). You could try an [EOL upgrade](https://help.ubuntu.com/community/EOLUpgrades) and if your system is reasonably clean, the chance of success is pretty good, but make sure you're ready for a new install anyway. Also consider the upgrade-by-installation, installing the new release over the old without formatting. I never tried it myself, but I've read it's quite reliable. It keeps your documents and installed applications, for as far as still available.

22.04 is an LTS (long term support) release. It has 5 years of support (3 years for the flavours), so you can use it until well after the release of the next LTS release. An LTS release comes out in April in even years. Impish or 21.10 was a non-LTS release, so only 9 months of support.

---

### Post by grahammechanical on 2022-09-12
Open Software and Updates>Updates tab. What is the setting for the panel "Notify me of a new Ubuntu version? If it is "Never" then change to either one of the other two settings. And then run Software Updater and you should get an offer to upgrade to Ubuntu 22.04 at the end of the update/upgrade process.

Regards

---

### Post by klapvogn on 2022-09-13
> **grahammechanical said:**
> Open Software and Updates>Updates tab. What is the setting for the panel "Notify me of a new Ubuntu version? If it is "Never" then change to either one of the other two settings. And then run Software Updater and you should get an offer to upgrade to Ubuntu 22.04 at the end of the update/upgrade process.

Regards

Hey,

I use Ubuntu as a server, so there is no GUI here. 


> **Impavidus said:**
> It's indeed an old release, but only one step away from the latest supported release (22.04). You could try an [EOL upgrade]("https://help.ubuntu.com/community/EOLUpgrades") and if your system is reasonably clean, the chance of success is pretty good, but make sure you're ready for a new install anyway. Also consider the upgrade-by-installation, installing the new release over the old without formatting. I never tried it myself, but I've read it's quite reliable. It keeps your documents and installed applications, for as far as still available.

22.04 is an LTS (long term support) release. It has 5 years of support (3 years for the flavours), so you can use it until well after the release of the next LTS release. An LTS release comes out in April in even years. Impish or 21.10 was a non-LTS release, so only 9 months of support.

Thanks for the explanation :-)

---

### Post by grahammechanical on 2022-09-14
To upgrade from Ubuntu 21.10 server to 22.04 server run this command after reading the accompanying web page

```
sudo do-release-upgrade
```

[https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction)

Regards


[URL="https://ubuntu.com/server/docs/upgrade-introduction"]


[/URL]

---

