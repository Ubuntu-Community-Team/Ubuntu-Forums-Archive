---
title: "smbfs in virtual box"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by jaya28inside on 2010-10-20
gosh...
I think again, I faced up some troubles.

i run this command because previously I didn't completed my previous installation, instead i restart unproperly the machine. sigh :(

```
sudo apt-get install -f;
```

and then what i got is that

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba-common smbclient
Suggested packages:
  smbfs
The following NEW packages will be installed:
  samba-common smbclient
0 upgraded, 2 newly installed, 0 to remove and 98 not upgraded.
Need to get 0B/11.9MB of archives.
After this operation, 34.7MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package samba-common.
(Reading database ... 123747 files and directories currently installed.)
Unpacking samba-common (from .../samba-common_2%3a3.4.7~dfsg-1ubuntu3.2_all.deb) ...
Selecting previously deselected pack 
```

now... i was thinking perhaps this is because somebody changes my
repository source.list

but here's the quick cat over /etc/apt/source.list

```

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb http://my.archive.ubuntu.com/ubuntu/ lucid main restricted
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://my.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ lucid universe
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid universe
# deb http://my.archive.ubuntu.com/ubuntu/ lucid-updates universe
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb http://my.archive.ubuntu.com/ubuntu/ lucid multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid multiverse
# deb http://my.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb http://archive.canonical.com/ubuntu lucid partner
 deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```


don't ask me why i ommit the my.archieve.ubuntu.com

because those links are very slow even i'm also accessing from
that country (malaysia) sigh.

which one that i forgot to do?
My aim is just want to use smbfs again... sigh.

~ I need advice.

---

### Post by lemming465 on 2010-10-21
You need a bunch of thos missing repositories.  If the Malayian ones (suggested by your timezone city) are too slow, you want to replace them with some others, not disable them. Open up synaptic, pick Settings -> Repositories, and use the "Download from" dropdown "Other ..." dialogue to pick a more congenial server.  Re-enable all the standard Ubuntu repositories.  Then try doing the software updates.

---

