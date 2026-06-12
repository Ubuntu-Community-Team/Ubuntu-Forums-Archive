---
title: "Compiling Plymouth"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by dolmoboy on 2010-08-01
Hi there :) well I'm making my own Plymouth theme, so to preview it I need to compile my own version of Plymouth with the X11 plug-in. So when I execute the autogen script, I get the following error:
```
checking for PANGO... configure: error: Package requirements (pangocairo >= 1.21.0 ) were not met:

No package 'pangocairo' found

```

So I did 
```
sudo apt-get install libpango1.0-dev 
``` and I get this error :( 

```
Los siguientes paquetes tienen dependencias incumplidas:
  libpango1.0-dev: Depende: libfreetype6-dev (>= 2.1.3) pero no va a instalarse
                   Depende: libxft-dev pero no va a instalarse
                   Depende: libfontconfig1-dev (>= 2.1.91) pero no va a instalarse
                   Depende: libcairo2-dev (>= 1.8.2-2) pero no va a instalarse
E: Paquetes rotos
```

Anyone knows why I have broken packages?

PD: If needed here is my sources.list

```
envy@Kiyumizu-deralin:~/plymouth/plymouth$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://es.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://es.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid universe
deb http://es.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://es.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

# deb-src http://ppa.launchpad.net/cybolic/ppa/ubuntu lucid mai

```

Thank you!

---

