---
title: "upgrade from 9.04 to 10.04 issue"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by mons00n on 2011-06-09
Hi everyone,

I was having trouble figuring out how to upgrade my file server (running 9.04 x64 desktop) to 10.04 so I asked google.  It led me to this webpage: [http://serverfault.com/questions/278608/upgrade-ubuntu-9-10-to-10-04](http://serverfault.com/questions/278608/upgrade-ubuntu-9-10-to-10-04) which told me to run this command:

```

cd /etc/apt 
perl -i.bak -pe 's/jaunty/lucid/' sources.list
aptitude update 
aptitude dist-upgrade

```

It ran for a bit and now it says that it is running 10.04.2 LTS, but I am unable to get any updates.  When I open the update manager it tells me "Not all updates can be installed" and says that I need to run a partial upgrade.  When I hit partial upgrade it then tells me that "An upgrade from 'lucid' to 'jaunty' is not supported with this tool."

Any help you can provide in fixing the update manager would be greatly appreciated.  This comp serves as my web/sql/file server so it's pretty important I keep it functional.  Everything else seems to be working fine though which I can only assume is a good thing.

Here's a copy of my sources.list:
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner


## For 8.04 hardy repos ##
# deb http://hu.archive.ubuntu.com/ubuntu/ hardy universe
# deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy universe
# deb http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
# deb-src http://hu.archive.ubuntu.com/ubuntu/ hardy-updates universe
# deb http://ppa.launchpad.net/jcfp/ppa/ubuntu lucid main
deb http://ppa.launchpad.net/byobu/ppa/ubuntu lucid main
deb http://archive.ubuntu.com/ubuntu/ lucid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ lucid universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ lucid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ lucid-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports universe main multiverse restricted

```

---

### Post by mons00n on 2011-06-09
ugh just found this website: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

and it looks like only 9.10-->10.04 is supported.  I knew I shouldn't have done this late at night =(

So the system seems to think it's running 10.04 - 'lsb_release -a' returns 10.04, system monitor shows 10.04 as well.  I just cannot open Software Sources (nothing happens), and I'm assuming update manager seems to think I need to upgrade to 9.10 since it says that it does not support Lucid --> Jaunty

Is there anything I can do short of a reinstall?

---

### Post by collisionystm on 2011-06-09
> **mons00n said:**
> ugh just found this website: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

and it looks like only 9.10-->10.04 is supported.  I knew I shouldn't have done this late at night =(

So the system seems to think it's running 10.04 - 'lsb_release -a' returns 10.04, system monitor shows 10.04 as well.  I just cannot open Software Sources (nothing happens), and I'm assuming update manager seems to think I need to upgrade to 9.10 since it says that it does not support Lucid --> Jaunty

Is there anything I can do short of a reinstall?


Yes, you can try to manually add the lucid apt sources to get updates from. Here are mine from a brand new 10.04 install.

Do this......

```
cd /etc/apt/
```

```
sudo mv sources.list sources_backup
```

```
sudo nano sources.list
```

Paste this

> #deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

```
CTRL+X
```

Y to save

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by mons00n on 2011-06-09
Well I was able to get that to work.  Package manager just loaded up empty but I went through a hefty number of updates via command line and now the system wont boot :(

It stops at:

```
init: rc-default main process (2401) terminated with status 127
```

I'm thinking of throwing another drive in there and just going to town with a new OS and see if I can match the configuration.  I'm just not looking forward to reconfiguring apache/sql/samba

---

### Post by collisionystm on 2011-06-09
[http://ubuntuforums.org/showthread.php?t=763265](http://ubuntuforums.org/showthread.php?t=763265)

Look at the bottom post

---

### Post by mons00n on 2011-06-10
appreciate the links.  I just ended up reinstalling 10.04 on a new HDD and reconfiguring everything.  It wasn't *too* painful =)

---

