---
title: "Could not initialize the package information"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by velickovic on 2008-10-07
I am stil noob for ubuntu, pls help!

> A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'sudo' is not known on line 58 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

What to do?

---

### Post by Pumalite on 2008-10-07
Post:
cat /etc/apt/sources.list

---

### Post by velickovic on 2008-10-07
what now? I type in terminal, and...?

---

### Post by Pumalite on 2008-10-07
Press 'Enter'
You will have an output
Copy and paste here

---

### Post by velickovic on 2008-10-07
marko@chika:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://rs.archive.ubuntu.com/ubuntu/](http://rs.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb  [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

sudo tee -a /etc/apt/sources.list

sudo apt-get update
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

---

### Post by Pumalite on 2008-10-07
Edit your sources.list and remove this:
'sudo tee -a /etc/apt/sources.list
sudo apt-get update'

First backup:
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
Edit:
gksudo gedit /etc/apt/sources.list
Remove ofending lines, save, exit.
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by velickovic on 2008-10-07
can this step - by - step? :)

---

