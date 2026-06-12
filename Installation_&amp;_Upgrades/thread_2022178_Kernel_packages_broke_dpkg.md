---
title: "Kernel packages broke dpkg"
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by schmii on 2012-07-10
After a usual update, dpkg gives me the following message when I run apt-get.
[IMG]http://gyazo.com/872187844503412c8ec7a82fb86c3048.png[/IMG]
By the way, this exact error pops up with any package.
When I run apt-get -f install, I get this:
[IMG]http://gyazo.com/e600c1446a32a45d18ba1d532f1d4e5a.png[/IMG]
Thanks in advance for any help.
Being without apt-get is torture for me.:(

---

### Post by Cheesehead on 2012-07-10
Please post the contents of your /etc/apt/sources.list

---

### Post by schmii on 2012-07-10
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main multiverse universe restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main multiverse universe restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main multiverse universe restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) precise main # disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) precise main # disabled on upgrade to precise
# GDM2Setup
# deb [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu) karmic main #GDM2 Setup Utility disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu) karmic main #GDM2 Setup Utilitydeb [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu)  jaunty main disabled on upgrade to precise
# deb [http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu](http://ppa.launchpad.net/danielgtaylor/ppa/ubuntu) oneiric main
# deb [http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) precise main # disabled on upgrade to precise
# deb-src [http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu](http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu) precise main # disabled on upgrade to precise
deb [http://repo.dc949.org/](http://repo.dc949.org/) lucid main

---

### Post by schmii on 2012-07-11
Nobody?

---

### Post by dino99 on 2012-07-11
your sources.list is a mess, remove everything but the precise lines, then save and update .

---

### Post by raja.genupula on 2012-07-11
you can use this also 

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Cheesehead on 2012-07-11
dino99 is right.

The kind of error you have tends to occur when a user has more than one release (like precise) in their sources.list, or if they have subscribed to an especially cutting-edge PPA that includes it's own cutting-edge dependencies. You seem to have the former problem.

---

### Post by schmii on 2012-07-11
Thanks guys, cleaning up my sources.list did the trick!

---

