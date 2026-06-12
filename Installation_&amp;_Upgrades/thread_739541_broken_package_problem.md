---
title: "broken package problem"
date: 2008-03-29
forum: Installation &amp; Upgrades
---

### Post by rockyredhead on 2008-03-29
I am trying to remove broken package lib-vo-dev
What ever I do I run up against there being no oo2c-config file

for example 
sudo dpkg -P libooc-vo-dev gives

Removing libooc-vo-dev ...
/var/lib/dpkg/info/libooc-vo-dev.prerm: 13: oo2c-config: not found
dpkg: error processing libooc-vo-dev (--purge):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 libooc-vo-dev

---

### Post by Bubba64 on 2008-03-29
Have you looked for it in synaptic.

---

### Post by rockyredhead on 2008-03-30
I get the same message about ooc2config if I use synaptic package manager to try and remove this package

---

### Post by bapoumba on 2008-03-30
Which version of Ubuntu ar you running?
There is no version for this package past Feisty: [libooc-vo-dev]("http://packages.ubuntu.com/libooc-vo-dev")

Could you please paste your sources.list ?
```
cat /etc/apt/sources.list

```

---

### Post by rockyredhead on 2008-03-30
I did an upgrade in 3 steps from dapper to gutsy via internet.
This package is a hang over and stopping me getting any updates etc.
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

This is my sources list

## Uncomment the following two lines to fetch updated software from the network
# deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe

---

### Post by zvacet on 2008-03-31
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Now make your source list look like this

> #
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse



```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by rockyredhead on 2008-03-31
I made the changes and did the apt get.
the process suggested apt get -f install to fix problems
when I did this still the same problem....

Removing libooc-vo-dev ...
/var/lib/dpkg/info/libooc-vo-dev.prerm: 13: oo2c-config: not found
dpkg: error processing libooc-vo-dev (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 libooc-vo-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
:(

this is the content of libooc-vo-dev.prerm:

#!/bin/sh

set -e

case "$1" in
  remove)
    oo2c-config -r libooc-vo-dev
    install-info --quiet --remove /usr/share/info/VODoc.info
    ;;
  upgrade)
    install-info --quiet --remove /usr/share/info/VODoc.info
    ;;
esac


Unfortunately it refers to oo2c-config which does not exist!

---

### Post by bubba_169 on 2008-03-31
As a very last resort you could add the --force-all option to the dpkg command. Be warned this could mess up your packaging system and should be used with caution...

---

### Post by zvacet on 2008-03-31
```
sudo dpkg --force-remove-reinstreq lib-vo-dev
```

---

### Post by rockyredhead on 2008-03-31
using force still results in a failure to remove the package because the prerm script cant locate ooc2-config.  I have tried creating a ooc2-config file but may not be puting it in the
right place.

---

### Post by zvacet on 2008-03-31
Sorry,my mistake.It is 

```
sudo dpkg --remove --force-remove-reinstreq lib-vo-dev
```

and you can try 

```
sudo apt-get --purge remove lib-vo-dev
```

---

### Post by rockyredhead on 2008-04-01
Both those commands still come up against the same problem of the reference to the missing ooc2-config file in the libooc-vo-dev.prerm script

---

### Post by rockyredhead on 2008-04-03
I have solved this problem with help from nzlug
I created oo2c-config (not ooc2-config) in /usr/bin and made it executable
This enabled removal of the package.  I had to empty and remove the
/lib/oo2c directory myself and remove the wrongly named ooc2-config files I
made.  Everything is working.  Just installed 36 security updates.
Thanks for the suggestions people made.

---

