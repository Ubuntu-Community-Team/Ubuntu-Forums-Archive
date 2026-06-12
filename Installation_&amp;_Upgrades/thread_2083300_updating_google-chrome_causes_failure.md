---
title: "updating google-chrome causes failure"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2012-11-12
I am using 11.10 64 bit
and each time I reboot the machine I get to see an unusual pop up which says "An upgrade 12.04 is available" then it lists some of the packages installed on my system and asks if I want to upgrade to get rid of this annoying message I click on upgrade and after showing me it "seemingly" starts downloading some thing and at some arbit point it says update failed and asks me to check my internet connection.

Here are my sources.list file 
```

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```

and the folder /etc/apt/sources.list.d/ has following files


/etc/apt/sources.list.d$ ls
```

google-chrome.list           shutter-ppa-oneiric.list.save
google-chrome.list.save      sunab-kdenlive-release-oneiric.list
google-talkplugin.list       sunab-sunab2-oneiric.list
google-talkplugin.list.save  sunab-sunab2-oneiric.list.save
shutter-ppa-oneiric.list

```
now google-chrome.list has
```
deb http://dl.google.com/linux/chrome/deb/ stable main

```
and google-chrome.list.save has
```

deb http://dl.google.com/linux/chrome/deb/ stable main

```

google-talkplugin.list has
```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main

```
google-talkplugin.list.save has
```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/talkplugin/deb/ stable main
```

let me know where can I look for the failed updates log I will post because I am doing it via gui.
~                                                                               
~

---

