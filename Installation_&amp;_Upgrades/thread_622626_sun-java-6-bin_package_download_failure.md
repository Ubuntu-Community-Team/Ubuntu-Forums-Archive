---
title: "sun-java-6-bin package download failure"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by torpethin on 2007-11-25
I am not exactly sure how or when this problem arose. I neglected it for a while by not downloading anything, but now I need to address it. 

For some reason java did not install correctly, and I have no idea how to fix this. If you have any insight, please help. 

When I try to install anything I get this:

> kyle@MARTHA:~$ sudo aptitude install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libflac++5c2 liboggflac3 libpng12-dev linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  fuse-utils libfuse2 libntfs-3g0 
The following packages have been kept back:
  bsdutils cdrecord cupsys cupsys-bsd cupsys-client cupsys-common firefox 
  firefox-gnome-support genisoimage gnome-system-tools libcupsimage2 
  libcupsys2 libflac7 libnspr4 libnss3 libpng12-0 libpoppler1 
  libpoppler1-glib libsmbclient libssl0.9.8 
  linux-restricted-modules-2.6.20-16-generic mkisofs mount openssl 
  poppler-utils samba-common smbclient sun-java6-bin util-linux 
  util-linux-locales wodim zsnes 
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 ntfs-3g 
0 packages upgraded, 4 newly installed, 0 to remove and 36 not upgraded.
Need to get 0B of archives. After unpacking 717kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the sun-java6-bin package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
kyle@MARTHA:~$ 


I don't know where to go from here. 

Thanks for you guidance. Don't hesitate to ask for clarification.

---

### Post by rsambuca on 2007-11-25
What happens when you run a 

sudo apt-get update && sudo apt-get upgrade

---

### Post by torpethin on 2007-11-25
> W: GPG error: [http://packages.dfreer.org](http://packages.dfreer.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D4C9CD8F7572013D
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems
kyle@MARTHA:~$ apt-get update 
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
kyle@MARTHA:~$ 


hm....don't know.

---

### Post by rsambuca on 2007-11-25
You are missing some keys for your repos.  Post the output of ```
cat /etc/apt/sources.list
```

---

### Post by torpethin on 2007-11-25
> kyle@MARTHA:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty exaile
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb [http://packages.dfreer.org](http://packages.dfreer.org) feisty main
deb [http://jbrout.free.fr/download/debian](http://jbrout.free.fr/download/debian) binary/
kyle@MARTHA:~$ 


i became distracted last night. Apologize for the lack of immediacy. Thanks for your help.

---

### Post by kashes911 on 2008-06-29
Well i am having the same problem. Was installing limewire, ans as a dependency it was installing sun-java6-bin .But the installation failed.Now i am not able to  do any thing with apt-get,synaptics,update manager. I am getting the same error

E: The package sun-java6-bin needs to be reinstalled, but I can't find an archive for it.

here my source.list

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-backports restricted

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://pkg-gnome.alioth.debian.org/debian/](http://pkg-gnome.alioth.debian.org/debian/) experimental main

deb [http://www.dtnrg.org/debian](http://www.dtnrg.org/debian) etch contrib
deb-src [http://www.dtnrg.org/debian](http://www.dtnrg.org/debian) etch contrib

deb [http://ppa.launchpad.net/woodypl/ubuntu](http://ppa.launchpad.net/woodypl/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/woodypl/ubuntu](http://ppa.launchpad.net/woodypl/ubuntu) gutsy main

deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main

deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-updates restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

deb [http://packages.bosslinux.in/boss](http://packages.bosslinux.in/boss) anant main contrib non-free

deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) gutsy restricted
deb [http://ubuntu.mirrors.tds.net/pub/ubuntu/](http://ubuntu.mirrors.tds.net/pub/ubuntu/) gutsy-updates restricted

---

