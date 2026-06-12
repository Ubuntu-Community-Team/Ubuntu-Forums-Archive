---
title: "error when installing libgtk2.0-dev"
date: 2017-01-15
forum: Installation &amp; Upgrades
---

### Post by smallcat9603 on 2017-01-15
Dear all,

I was trying to apt-get install libgtk2.0 on ubuntu 16.04 in my macbook, but I got the following error messages. 
I also tried to aptitude install it but it still not works. Then I tried all the solutions on the networks but with no result. 
Any help is appreciated!

```

sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgtk2.0-dev : Depends: libglib2.0-dev (>= 2.27.3) but it is not going to be installed
                 Depends: libgdk-pixbuf2.0-dev (>= 2.21.0) but it is not going to be installed
                 Depends: libpango1.0-dev (>= 1.20) but it is not going to be installed
                 Depends: libatk1.0-dev (>= 1.29.2) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.6.4-6.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by smallcat9603 on 2017-01-16
Does anyone know the solution for the bug? Thanks very much!

---

### Post by smallcat9603 on 2017-01-16
The problem seems to be that libgtk2.0-0 depends on **old, out-of-date packages** and the package system will not go back to the required older versions. 
Below is my** /etc/apt/sources.list**:
Any idea to correct the problem? Thanks a lot!!!

```

# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu xenial universe
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu xenial multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://jp.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```

---

### Post by mc4man on 2017-01-16
> **smallcat9603 said:**
> The problem seems to be that libgtk2.0-0 depends on **old, out-of-date packages** and the package system will not go back to the required older versions. 


Would install fine here on 16.04, Ex.

```
$ sudo apt -s install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gir1.2-gtk-2.0 libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev
  libxcomposite-dev libxft-dev x11proto-composite-dev
Suggested packages:
  libcairo2-doc libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  gir1.2-gtk-2.0 libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libgdk-pixbuf2.0-dev libgtk2.0-dev
  libpango1.0-dev libxcomposite-dev libxft-dev x11proto-composite-dev
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Inst gir1.2-gtk-2.0 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Inst libatk1.0-dev (2.18.0-1 Ubuntu:16.04/xenial [amd64])
Inst libcairo-script-interpreter2 (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Inst libcairo2-dev (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Inst [COLOR="#0000CD"]libgdk-pixbuf2.0-dev (2.32.2-1ubuntu1.2 Ubuntu:16.04/xenial-updates[/COLOR], Ubuntu:16.04/xenial-security [amd64])
Inst libxft-dev (2.3.2-1 Ubuntu:16.04/xenial [amd64])
Inst libpango1.0-dev (1.38.1-1 Ubuntu:16.04/xenial [amd64])
Inst x11proto-composite-dev (1:0.4.2-2 Ubuntu:16.04/xenial [all])
Inst libxcomposite-dev (1:0.4.4-1 Ubuntu:16.04/xenial [amd64])
Inst libgtk2.0-dev (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf gir1.2-gtk-2.0 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libatk1.0-dev (2.18.0-1 Ubuntu:16.04/xenial [amd64])
Conf libcairo-script-interpreter2 (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Conf libcairo2-dev (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Conf [COLOR="#0000CD"]libgdk-pixbuf2.0-dev (2.32.2-1ubuntu1.2 Ubuntu:16.04/xenial-updates[/COLOR], Ubuntu:16.04/xenial-security [amd64])
Conf libxft-dev (2.3.2-1 Ubuntu:16.04/xenial [amd64])
Conf libpango1.0-dev (1.38.1-1 Ubuntu:16.04/xenial [amd64])
Conf x11proto-composite-dev (1:0.4.2-2 Ubuntu:16.04/xenial [all])
Conf libxcomposite-dev (1:0.4.4-1 Ubuntu:16.04/xenial [amd64])
Conf libgtk2.0-dev (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
```

You should open Software & Updates & make sure under the Updates tab that the first 2 are enabled, xenial-security & xenial-updates as they don't appear to be.

---

### Post by smallcat9603 on 2017-01-17
This really works! Thanks very much!!!

> **mc4man said:**
> Would install fine here on 16.04, Ex.

```
$ sudo apt -s install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  gir1.2-gtk-2.0 libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev
  libxcomposite-dev libxft-dev x11proto-composite-dev
Suggested packages:
  libcairo2-doc libgtk2.0-doc libpango1.0-doc
The following NEW packages will be installed:
  gir1.2-gtk-2.0 libatk1.0-dev libcairo-script-interpreter2 libcairo2-dev libgdk-pixbuf2.0-dev libgtk2.0-dev
  libpango1.0-dev libxcomposite-dev libxft-dev x11proto-composite-dev
0 upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Inst gir1.2-gtk-2.0 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Inst libatk1.0-dev (2.18.0-1 Ubuntu:16.04/xenial [amd64])
Inst libcairo-script-interpreter2 (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Inst libcairo2-dev (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Inst [COLOR=#0000CD]libgdk-pixbuf2.0-dev (2.32.2-1ubuntu1.2 Ubuntu:16.04/xenial-updates[/COLOR], Ubuntu:16.04/xenial-security [amd64])
Inst libxft-dev (2.3.2-1 Ubuntu:16.04/xenial [amd64])
Inst libpango1.0-dev (1.38.1-1 Ubuntu:16.04/xenial [amd64])
Inst x11proto-composite-dev (1:0.4.2-2 Ubuntu:16.04/xenial [all])
Inst libxcomposite-dev (1:0.4.4-1 Ubuntu:16.04/xenial [amd64])
Inst libgtk2.0-dev (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf gir1.2-gtk-2.0 (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
Conf libatk1.0-dev (2.18.0-1 Ubuntu:16.04/xenial [amd64])
Conf libcairo-script-interpreter2 (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Conf libcairo2-dev (1.14.6-1 Ubuntu:16.04/xenial [amd64])
Conf [COLOR=#0000CD]libgdk-pixbuf2.0-dev (2.32.2-1ubuntu1.2 Ubuntu:16.04/xenial-updates[/COLOR], Ubuntu:16.04/xenial-security [amd64])
Conf libxft-dev (2.3.2-1 Ubuntu:16.04/xenial [amd64])
Conf libpango1.0-dev (1.38.1-1 Ubuntu:16.04/xenial [amd64])
Conf x11proto-composite-dev (1:0.4.2-2 Ubuntu:16.04/xenial [all])
Conf libxcomposite-dev (1:0.4.4-1 Ubuntu:16.04/xenial [amd64])
Conf libgtk2.0-dev (2.24.30-1ubuntu1 Ubuntu:16.04/xenial [amd64])
```

You should open Software & Updates & make sure under the Updates tab that the first 2 are enabled, xenial-security & xenial-updates as they don't appear to be.

---

