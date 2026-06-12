---
title: "Unmet dependencies during Open Broadcaster install"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by Exacom on 2015-10-22
Hello Ubuntu Forum,

sorry for a pretty specific problem, although it's said to happen very often with other programs. I am trying to install Open Broadcaster Software ([https://obsproject.com/download#linux)]("https://obsproject.com/download#linux") on a pretty fresh Lubuntu 14.04 LTS, so I haven't had that much time to **** things up. At first I followed the install guide given by OBS developers on their websites. While the required ffmpeg install worked without problems, trying to install OBS results in this:

```

exy@ThinkPad:~$ sudo apt-get install obs-studio
[sudo] password for exy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 obs-studio : Depends: libqt5gui5 (>= 5.2.0) but it is not going to be installed or
                       libqt5gui5-gles (>= 5.2.0) but it is not installable
              Depends: libqt5widgets5 (>= 5.2.0) but it is not going to be installed
              Depends: libqt5x11extras5 (>= 5.1.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

So naturally I installed these missing packages manually via Synaptic Package Manager. This resulted in the installation working, but OBS itself crashed on every start with and "unspecific error". So I went on uninstalling them again, and found this article in response to a similar question: [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa#answer-142808](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa#answer-142808) .

I tried out every single command line given, nothing lead to success. Note that the only ppa repositories that were listed in "Software & Updates" were the ffmpeg and OBS ones I just added before and therefore needed for the install.
I've ran out of answers, the only other thing that I've heard is that it may not be possible to install OBS on a 64bit Lubuntu install, although I didn't find any solutions for that either.

As suggested in the article, here are the outputs for cat /etc/apt/sources.list and cat /etc/apt/sources.list.d/*
```

exy@ThinkPad:~$ cat /etc/apt/sources.list
# deb cdrom:[Lubuntu 14.04.3 LTS _Trusty Tahr_ - Beta amd64 (20150805)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty universe
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main


```
```

exy@ThinkPad:~$ cat /etc/apt/sources.list.d/*
deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
deb http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu trusty main
deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
deb http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
# deb-src http://ppa.launchpad.net/obsproject/obs-studio/ubuntu trusty main
exy@ThinkPad:~$ 

```

After I switched from Windows to Xubuntu on my desktop PC, OBS install over there was no problem. I chose Lubuntu for my potato notebook, as it's said to be faster. If this problem is not solvable and Lubuntu-specific, I have still the possibility to switch over to xubuntu quickly aswell, so tell me if that's the better option.

Thank you in advance,

Exacom

---

