---
title: "no updates"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by paradoxni on 2008-04-24
I came home from work today hoping to do the final update from RC. The problem is no updates are listed..tells me im up to date, yet this is the first my PC has been on today.

I tried changing from main to UK to german servers but still no new updates?!

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Beta amd64 (20080319)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse

```

```
alun@alun-desktop:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com hardy Release.gpg       
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy-security Release.gpg
Ign http://gb.archive.ubuntu.com hardy-security/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release
Hit http://gb.archive.ubuntu.com hardy-updates Release
Hit http://gb.archive.ubuntu.com hardy-security Release
Hit http://gb.archive.ubuntu.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-security/main Packages
Hit http://gb.archive.ubuntu.com hardy-security/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-security/universe Packages
Hit http://gb.archive.ubuntu.com hardy-security/multiverse Packages
Reading package lists... Done

alun@alun-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

alun@alun-desktop:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by Ninjanoh on 2008-04-24
Double post.

---

### Post by Ninjanoh on 2008-04-24
I am having the same problem with the US servers.
I tried to access the files through a browser, and i get 404 errors.

I would say the problem was just that the servers are overloaded, but i have been having this problem for the past week when trying to download software for a new server.

Ok update. 
I opened up synaptic package manager, and hit reload. That fixed the problem.

---

### Post by GeneW on 2008-04-25
I've tried four or five different servers and I still keep getting 404 errors when I try to "reload" in Synaptic.  Did Ubuntu change the way that it organizes it's web repositories recently?  From the errors, I see that synaptic is looking for:

```
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/main/source/Sources.gz: 404 Not Found
http://ubuntu.mirrors.tds.net/pub/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found
```

but when I look at that repository, I see that it has paths like this:

```
http://ubuntu.mirrors.tds.net/ubuntu/dists/gutsy/main/
```

How do I tell synaptic to look for  in the right places?

---

