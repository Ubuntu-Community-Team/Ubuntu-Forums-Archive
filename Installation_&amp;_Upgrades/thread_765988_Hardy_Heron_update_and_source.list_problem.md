---
title: "Hardy Heron update and source.list problem"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by linuxlsrjd on 2008-04-24
Hey everyone. I've been trying to update to Hardy Heron all day now and i keep getting errors. It would end up timing out and say there was a network problem and that it could not connect to the Ubuntu archives. When I use update manager I was also getting errors having to do with not being able to find certain repositories. I figured that was my problem with updating to Hardy Heron so I attacked that problem first. I also found forums about something being wrong with proxy also that could be why the update wasn't working. Anyway, I ended up screwing up my source.list. Update manager now says I can't download all repositories. I want to find a way to just get the source.list back to the norm but all the forums point to a website that is inactive which is: [http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic). Can anyone help me out here with the source.list our just updating strait to Hardy Heron. I'm using Ubuntu 7.10 by the way.

---

### Post by enoughsaid05 on 2008-04-24
How do you screw up your sources.list? By editing the file /etc/apt/sources.list?

I am by no means an expert. I am also trying to upgrade Gutsy but it seems that the server is overcrowded. I am waiting for the network traffic to ease.

During the upgrade I also found myself unable to use update manager. The only server it hooks up to is the main server and not the one that is closest. No matter how many times I tried, I can't change the settings.

If you have not done anything to your sources.list file, I guess it would be fine.

---

### Post by ptcbus on 2008-04-24
Regarding upgrading from 7.10 to 8.04, I would go for torrents. The servers are way too overcrowded now.  See [http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html]("http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html")

---

### Post by | MM | on 2008-04-24
> **linuxlsrjd said:**
> Hey everyone. ...

Seems like servers are taking a pounding, many of the links to K/X/Ubuntu (even torrrent links) seems to be down or strained at the moment.  So i wouldn't fret that you cant contact servers.  Give it a day or two i would say.

Here's my sources list for Hardy (US servers):

[B]Note:
See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to newer versions of the distribution.[/B]

[B]Note2:
I have a couple of links to New Zealand (NZ) servers... [/B]

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Alpha i386 (20080201.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy universe
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://nz.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

```

---

### Post by linuxlsrjd on 2008-04-28
Thanks guys. I tried using the alternate cd to install Hardy but I ended up getting similar errors that I got when I tried to install through Update Manager. I just ended up taking the easy/lazy route and doing a fresh install. Thanks though. I love Hardy so far. You should all give it a try if you haven't already.

---

