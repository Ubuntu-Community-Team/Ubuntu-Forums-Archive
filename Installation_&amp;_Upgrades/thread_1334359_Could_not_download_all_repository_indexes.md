---
title: "Could not download all repository indexes"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by OwNeD on 2009-11-22
update manager cant download all the repository indexes... 

Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  maindeb/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/maindeb/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/maindeb/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/http://ppa.launchpad.net/tualatrix/ppa/ubuntu/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/http://ppa.launchpad.net/tualatrix/ppa/ubuntu/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/karmic/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/karmic/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead. 

------------------------------------------------------------------------------------------------------
My Source.list >   # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic multiverse
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security multiverse
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) gutsy maindeb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic maindeb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock


Please help me! Thanks.

---

### Post by wojox on 2009-11-22
Before:
```

deb http://ftp.uninett.no/ubuntu/ karmic-security main restricted
deb-src http://ftp.uninett.no/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://ftp.uninett.no/ubuntu/ karmic-security universe
deb http://ftp.uninett.no/ubuntu/ karmic-security multiverse
deb-src http://ppa.launchpad.net/tualatrix/ubuntu gutsy maindeb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic maindeb http://repository.cairo-dock.org/ubuntu karmic cairo-dock

```

After:
```

deb http://ftp.uninett.no/ubuntu/ karmic-security main restricted
deb-src http://ftp.uninett.no/ubuntu/ karmic-security restricted main multiverse universe
deb http://ftp.uninett.no/ubuntu/ karmic-security universe
deb http://ftp.uninett.no/ubuntu/ karmic-security multiverse
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic maindeb 
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock

```

---

### Post by OwNeD on 2009-11-22
ok i deleted the whole source.list and typed in this code : 
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security restricted main multiverse universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic maindeb 
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock


But the update manager still says this : Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  maindeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

 i can get some updates now but i would like to fix that too.

---

### Post by OwNeD on 2009-11-23
Anyone?

---

### Post by rainingheavy on 2009-11-23
Hello,

I believe I am having a similar problem, I'm new to Linux and at university, but it doesn't seem to download any packets. I thought this was to do with proxy settings, and after applying them as instructed by the university website, it tried again (to download WINE), it got 4 of 18 packets and stopped saying it could not connect to various websites.

I am running Ubuntu Jaunty 9.4, and the Internet is supplied by the university through a network system. it is wired if that makes any difference.

I would appreciate any suggestions, I am off to see if I can find some IT support people that can help.

MP

---

### Post by wojox on 2009-11-23
```

deb http://ftp.uninett.no/ubuntu/ karmic main restricted
deb-src http://ftp.uninett.no/ubuntu/ karmic multiverse universe
deb http://ftp.uninett.no/ubuntu/ karmic universe
deb http://ftp.uninett.no/ubuntu/ karmic-updates universe
deb http://ftp.uninett.no/ubuntu/ karmic multiverse
deb http://ftp.uninett.no/ubuntu/ karmic-updates multiverse
deb http://ftp.uninett.no/ubuntu/ karmic-updates main restricted
deb-src http://ftp.uninett.no/ubuntu/ karmic-updates restricted main multiverse universe
deb http://ftp.uninett.no/ubuntu/ karmic-security main restricted
deb-src http://ftp.uninett.no/ubuntu/ karmic-security restricted main multiverse universe
deb http://ftp.uninett.no/ubuntu/ karmic-security universe
deb http://ftp.uninett.no/ubuntu/ karmic-security multiverse
deb http://repository.cairo-dock.org/ubuntu karmic cairo-dock

```

Open System > Admin > Software Sources > Other Software
and add:

ppa:tualatrix/ppa

---

### Post by OwNeD on 2009-11-23
i did what you said wojox but  the update manager still says this : Failed to fetch [http://ppa.launchpad.net/tualatrix/p...karmic/Release]("http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/karmic/Release")  Unable to find expected entry  maindeb/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.


 then i deleted the whole source.list and added 

deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic multiverse universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic multiverse
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates multiverse
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-updates restricted main multiverse universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security main restricted
deb-src [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security restricted main multiverse universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security universe
deb [http://ftp.uninett.no/ubuntu/](http://ftp.uninett.no/ubuntu/) karmic-security multiverse
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) karmic cairo-dock

 now i dont have anymore problems with it so far.

Thanks for the help!

---

### Post by cybercookie72 on 2009-12-09
Greetings

9.10 only
(remember to back up first/this sources.list was found in this forum)
I had error that was like yours and I replaced sources.list with ::


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main universe multiverse restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main universe multiverse restricted

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main universe multiverse restricted


I used that for awhile but then found a website that generates from a form

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

I use the sources.list from the website now because it updates
pidgin and VLC ;)

hope this helps

---

