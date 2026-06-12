---
title: "apt-get not working signatures were invalid: NODATA 1 NODATA 2"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by andrewdn on 2016-09-15
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
**E: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: NODATA 1 NODATA 2**



"apt-get update" not working . Not able to install any software using apt-get . We uninstalled google-chrome browser in Ubuntu 12. Now we aren't able to reinstall it . Using ubuntu software center also we aren't able to install anything. Kindly assist us

---

### Post by speed... on 2016-09-15
Can you post the output of
```
[COLOR=#000000][FONT=&quot]cat /etc/apt/sources.list[/FONT][/COLOR]
```

Another user had the same issue, did you already checked their solution: [https://ubuntuforums.org/showthread.php?t=2202787](https://ubuntuforums.org/showthread.php?t=2202787)

---

### Post by andrewdn on 2016-09-19
I tried with all ubuntu forum related search results none of them working . So only requesting support

---

### Post by speed... on 2016-09-19
Can you post the output of
```
[COLOR=#000000]cat /etc/apt/sources.list[/COLOR]
```

---

### Post by howefield on 2016-09-19
Open up the update manager application and click on the Settings button, then deselect the "*Independent*" repository from the "*Other Software*" tab. Close out and you'll be asked for your password, enter it and the try sudo apt-get update again.

Are you using any software from the extras repository ?

---

### Post by andrewdn on 2016-09-20
```
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/


# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
```

Im not able to find "update manager" gui console in my Ubuntu 12 machine

---

### Post by howefield on 2016-09-20
> **andrewdn said:**
> Im not able to find "update manager" gui console in my Ubuntu 12 machine

OK, from your terminal use the following command..

```
sudo sed /extra/s/^/#/ /etc/apt/sources.list
```

This will disable the Independent (extras) repository and should allow you to sudo apt-get update and install software without issue. 

It is only a temporary fix though, depending on whether or not you are using software from that repository (there is very little in it so every chance that you are not) so you may need to re-enable the repository later on and fully fix the NO DATA error.

---

### Post by andrewdn on 2016-09-20
I entered **"**[COLOR=#000000][FONT=&quot]**sed /extra/s/^/#/ /etc/apt/sources.list"** command in terminal

[/FONT][/COLOR]Afterwards i tried to enter **"apt-get update"** . See the below response

[email]root@tag181:/etc/apt/trusted.gpg[/email].d# apt-get update
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [2,825 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [2,829 B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [2,842 B]
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [2,843 B]
Get:5 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1 Release.gpg [2,841 B]
Get:6 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release.gpg [2,839 B]
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg [2,835 B]
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [2,822 B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [2,838 B]
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg [2,843 B]
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg [2,845 B]
Get:12 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [2,821 B]
Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise Release [2,818 B]
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [2,841 B]
Get:15 [http://dl.google.com](http://dl.google.com) stable Release [2,825 B]
Get:16 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) precise-dell Release [2,835 B]
Get:17 [http://oem.archive.canonical.com](http://oem.archive.canonical.com) precise-oem-sp1 Release [2,837 B]
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [2,851 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release
**E: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures were invalid: NODATA 1 NODATA 2**

---

