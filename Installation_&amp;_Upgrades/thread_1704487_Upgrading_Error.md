---
title: "Upgrading Error"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by rawtoas on 2011-03-10
when I attempt to upgrade to ubuntu 10.4, so I can move on to 10.10, I get this error when I update packages(                                                                                                                                                        A problem occurred during the update. This is usually some sort of  network problem, please check your network connection and retry.      W:Failed to fetch [http://ports.ubuntu.com/dists/lucid/Release](http://ports.ubuntu.com/dists/lucid/Release) Unable  to find expected entry partner/source/Sources in Meta-index file  (malformed Release file?)  , W:Failed to fetch  [http://ports.ubuntu.com/dists/lucid-proposed/Release](http://ports.ubuntu.com/dists/lucid-proposed/Release) Unable to find  expected entry partner/binary-powerpc/Packages in Meta-index file  (malformed Release file?)  , W:Failed to fetch  [http://ports.ubuntu.com/dists/lucid-updates/Release](http://ports.ubuntu.com/dists/lucid-updates/Release) Unable to find  expected entry partner/binary-powerpc/Packages in Meta-index file  (malformed Release file?)  , W:Failed to fetch  [http://ports.ubuntu.com/dists/lucid-backports/Release](http://ports.ubuntu.com/dists/lucid-backports/Release) Unable to find  expected entry partner/binary-powerpc/Packages in Meta-index file  (malformed Release file?)  , E:Some index files failed to download, they have been ignored, or  old ones used instead. )      how do i fix this  Thanks

---

### Post by zvacet on 2011-03-11
In terminjal type

```
cat /etc/apt/sources.list
```

and post output here.

---

### Post by rawtoas on 2011-03-11
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release powerpc (20090421)]/ jaunty main
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic restricted main
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic partner restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic partner

deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted main
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security restricted main multiverse universe #Added by software-properties
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-proposed partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-proposed partner restricted main multiverse universe #Added by software-properties
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-updates partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-updates partner restricted main multiverse universe
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-backports partner restricted main multiverse universe
deb-src [http://ports.ubuntu.com/](http://ports.ubuntu.com/) karmic-backports partner restricted main multiverse universe

---

### Post by zvacet on 2011-03-12
```
gksudo gedit /etc/apt/sources.list
```

replace 

deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-backports main restricted universe multiverse

with 

#deb-src [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) jaunty-backports main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-backports main restricted universe multiverse


or just delete those two lines.After that save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rawtoas on 2011-03-12
i typed 
Sudo apt-get update
 and got this. . . 
 W: Failed to fetch [http://ports.ubuntu.com/dists/karmic/Release](http://ports.ubuntu.com/dists/karmic/Release)  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ports.ubuntu.com/dists/karmic-proposed/Release](http://ports.ubuntu.com/dists/karmic-proposed/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ports.ubuntu.com/dists/karmic-updates/Release](http://ports.ubuntu.com/dists/karmic-updates/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://ports.ubuntu.com/dists/karmic-backports/Release](http://ports.ubuntu.com/dists/karmic-backports/Release)  Unable to find expected entry  partner/binary-powerpc/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by zvacet on 2011-03-12
Only thing I can think of is to try to change server.You can do that under **software center>edit>software repositories** and change it to main.

---

### Post by rawtoas on 2011-03-13
i allready had it set for main and now it does this when i open update manager     Could not initialize the package information   An unresolvable problem occurred while initializing the package information.    Please report this bug against the 'update-manager' package and include the following error message:   'E:Malformed line 37 in source list /etc/apt/sources.list (dist), E:The list of sources could not be read.'

---

