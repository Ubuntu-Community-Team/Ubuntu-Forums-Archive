---
title: "Packet manager problems after upgrade"
date: 2019-12-01
forum: Installation &amp; Upgrades
---

### Post by name7891 on 2019-12-01
Hello Community,

I would like to install "qt5-default" on Ubuntu 19.04

starting with 


```
    sudo apt-get install qt5-default

```

I get "qt5-default : Depends: qtbase5-dev but it is not going to be installed"


on


```
    sudo apt-get install qtbase5-dev

```

I get "qtbase5-dev : Depends: libvulkan-dev but it is not going to be installed"


on


```
    sudo apt-get install libvulkan-dev

```

I get "libvulkan-dev : Depends: libvulkan1 (= 1.1.101.0-2) but 1.1.114.0-1~gpu18.04.1 is to be installed"


here I am not sure what to do now


This PC is running with a gtx1080ti for which I installed CUDA so I am not sure how exactly to libvulkan1 (= 1.1.101.0-2) to 1.1.114.0-1~gpu18.04.1 and when I do so if I would break anything. Also I am not sure whether my attempt to solve the problem is correct or not. I am not an experienced Ubuntu user.


/etc/apt/sources.list :


```
    # deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted
    
    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
    # newer versions of the distribution.
    deb http://us.archive.ubuntu.com/ubuntu/ disco main restricted
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic main restricted
    
    ## Major bug fix updates produced after the final release of the
    ## distribution.
    deb http://us.archive.ubuntu.com/ubuntu/ disco-updates main restricted
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    
    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    ## team. Also, please note that software in universe WILL NOT receive any
    ## review or updates from the Ubuntu security team.
    deb http://us.archive.ubuntu.com/ubuntu/ disco universe
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic universe
    deb http://us.archive.ubuntu.com/ubuntu/ disco-updates universe
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates universe
    
    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    ## team, and may not be under a free licence. Please satisfy yourself as to 
    ## your rights to use the software. Also, please note that software in 
    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    ## security team.
    deb http://us.archive.ubuntu.com/ubuntu/ disco multiverse
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic multiverse
    deb http://us.archive.ubuntu.com/ubuntu/ disco-updates multiverse
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    
    ## N.B. software from this repository may not have been tested as
    ## extensively as that contained in the main release, although it includes
    ## newer versions of some applications which may provide useful features.
    ## Also, please note that software in backports WILL NOT receive any review
    ## or updates from the Ubuntu security team.
    deb http://us.archive.ubuntu.com/ubuntu/ disco-backports main restricted universe multiverse
    # deb-src http://de.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    
    ## Uncomment the following two lines to add software from Canonical's
    ## 'partner' repository.
    ## This software is not part of Ubuntu, but is offered by Canonical and the
    ## respective vendors as a service to Ubuntu users.
    deb http://archive.canonical.com/ubuntu disco partner
    # deb-src http://archive.canonical.com/ubuntu bionic partner
    
    deb http://us.archive.ubuntu.com/ubuntu/ disco-security main restricted
    # deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
    deb http://us.archive.ubuntu.com/ubuntu/ disco-security universe
    # deb-src http://security.ubuntu.com/ubuntu bionic-security universe
    deb http://us.archive.ubuntu.com/ubuntu/ disco-security multiverse
    # deb http://linux.dropbox.com/ubuntu disco main # disabled on upgrade to disco
    # deb-src http://linux.dropbox.com/ubuntu bionic main
    # deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
    # deb http://dl.openfoam.org/ubuntu bionic dev main
    # deb-src http://dl.openfoam.org/ubuntu bionic dev
    # deb-src http://dl.openfoam.org/ubuntu bionic main

```

/etc/apt/sources.list.d are still bionic files :
```
    daniel_pavel-ubuntu-solaar-bionic.list
    daniel_pavel-ubuntu-solaar-bionic.list.distUpgrade
    daniel_pavel-ubuntu-solaar-bionic.list.save
    dropbox.list
    dropbox.list.distUpgrade
    dropbox.list.save
    google-chrome.list
    graphics-drivers-ubuntu-ppa-bionic.list
    graphics-drivers-ubuntu-ppa-bionic.list.distUpgrade
    graphics-drivers-ubuntu-ppa-bionic.list.save
    lutris-team-ubuntu-lutris-bionic.list
    lutris-team-ubuntu-lutris-bionic.list.distUpgrade
    lutris-team-ubuntu-lutris-bionic.list.save
    teamviewer.list

```

I also asked this question in askUbuntu and received an answer. My problem is that the answer is cryptic to me and I would like to ask for your help to really understand what to do. The answer is as follows:

[FONT=Arial][FONT=inherit]You got a higher version of libvulkan1 when on 18.04 from the ppa and didn't use ppa-purge before upgrading. So easiest is to add the ppa back for disco and update to the ppa's libvulkan1 package for 19.04 (& any other installed ppa packages) , then use ppa-purge to downgrade to disco packages. Then you should upgrade to 19.10 as 19.04 is EOL[/FONT]
[/FONT]
[FONT=inherit][COLOR=#C0C0C0][FONT=Arial][/FONT][/COLOR]
[/FONT]

What ppa should I add back for disco and how exactly do I update to the ppa's libvulkan1 package? How do I find other packages for which this will be necessary? (I think how to ppa-purge I will easily find on the internet).

Thank you very much in advance for your help.

Greetings,
name7891

---

### Post by Impavidus on 2019-12-01
You could try and get libvulkan-dev from a PPA so that it can handle libvulkan1 version 1.1.114.0-1~gpu18.04.1, but that may lead to dependency hell. And I don't know what's in that PPA. If you don't really need libvulkan1 version 1.1.114, but version 1.1.101 is also acceptable, I suggest you downgrade libvulkan1 to the version from the official repositories. Use whatever is your favourite interface to package management and force the version from the official repos. Disable the PPA.
> **name7891 said:**
> [FONT=Arial][FONT=inherit]Then you should upgrade to 19.10 as 19.04 is EOL[/FONT][/FONT]

That isn't true. 19.04 will be supported until some day in January.

---

### Post by mörgæs on 2019-12-01
I suggest a clean install of 19.10 without PPA's or other additions. It will give you 1.1.114 and guarantee that all packages are in sync.

---

