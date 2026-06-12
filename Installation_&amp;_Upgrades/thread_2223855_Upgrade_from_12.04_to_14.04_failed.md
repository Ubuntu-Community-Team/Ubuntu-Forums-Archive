---
title: "Upgrade from 12.04 to 14.04 failed"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by xxlray on 2014-05-13
I want to upgrade from Ubuntu 12.04 to 14.04

I start the update manager from my terminal using ```
sudo update-manager -d
```

The update procedure start but on "Setting new software channels" I get the following error message

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

This is my sources.list:```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise universe
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

# Opera
deb http://deb.opera.com/opera/ stable non-free

# subversion 1.7
# deb http://ppa.launchpad.net/dominik-stadler/subversion-1.7/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/dominik-stadler/subversion-1.7/ubuntu oneiric main
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

#Vmware Server
# deb http://archive.canonical.com/ubuntu feisty-commercial main

# wxWidgets/wxPython repository at apt.wxwidgets.org
# deb http://apt.wxwidgets.org/ natty-wx main # disabled on upgrade to precise
# deb-src http://apt.wxwidgets.org/ natty-wx main # disabled on upgrade to precise

# frei0r
# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main # disabled on upgrade to precise
deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu oneiric main
deb http://archive.ubuntu.com/ubuntu oneiric main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe main multiverse restricted

```

Can anybody help me to get the upgrade done?

---

### Post by plucky on 2014-05-13
```
# Opera
deb http://deb.opera.com/opera/ stable non-free

# frei0r
# deb http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu precise main # disabled on upgrade to precise
deb-src http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu oneiric main
deb http://archive.ubuntu.com/ubuntu oneiric main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ oneiric-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe main multiverse restricted
```

Try disabling these repositories and retry the upgrade.


Good Luck

---

### Post by Old_Grey_Wolf on 2014-05-13
In addition to what plucky said you also have maverick repositories that should be disabled.

```
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
```

Do an update then an upgrade before doing a release upgrade.

---

### Post by xxlray on 2014-05-14
Thanks for the suggestions - unfortunately they did not work. I ended up in creating a new sources.list for Ubuntu 14.04 using the [Ubuntu Sources List Generator]("http://repogen.simplylinux.ch/"). Afterwards I did "sudo apt-get update && sudo apt-get dist-upgrade". I had some dependency issues but the repeated use of "sudo apt-get -f install && sudo apt-get dist-upgrade" fixed it for me.
The only issues I found so far are that I had to remove and re-install pulseaudio and the volume indicator. Otherwise I had a humming sound coming from my speakers.

```
sudo apt-get -f install --reinstall pulseaudio
sudo apt-get -f install --reinstall indicator-sound indicator-sound-gtk2
```

---

