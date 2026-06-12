---
title: "Need the default sources.list of Ubuntu 20.04.1 LTS"
date: 2020-12-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2020-12-13
Hi
I have by mistake override the sources.list  of Ubuntu 20.04.1 LTS
I have googled but don't really know the content my sources.list 
so I will like to get the default create when one install it .

Thanks

---

### Post by ajgreeny on 2020-12-13
Here you go.
This is mine using **gb** archives from my Xubuntu 20.04, not the 20.04.1 version you asked for but that will make no difference.
I think Ubuntu has the universe repos disabled for some reason, but again, that will make no real difference to what you want or need.
```
# deb cdrom:[Xubuntu 20.04 LTS _Focal Fossa_ - Beta amd64 (20200416)]/ focal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://security.ubuntu.com/ubuntu focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://security.ubuntu.com/ubuntu focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://security.ubuntu.com/ubuntu focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse
#
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.

```
Copy the content shown and save as sources.list in your home then remove or rename the current version and move my version into the /etc/apt/ folder.

---

### Post by hoboy on 2020-12-13
Thanks

---

### Post by deadflowr on 2020-12-13
A barebones sources.list file can be found at /usr/share/doc/apt/examples.
Just copy it over to the /etc/apt/directory.
```
sudo cp /usr/share/doc/apt/examples/sources.list /etc/apt/sources.list
```
The file only has the main and restricted archives set,
so you'd need to enable the others yourself.
```
sudo add-apt-repository universe
sudo add-apt-repository multiverse
sudo apt update
```

---

### Post by ajgreeny on 2020-12-13
Ah, yes. I forgot about that one!
Never mind.  

How does my version work for you? Have you had to change to your own local repositories rather than the gb versions that I use?

---

