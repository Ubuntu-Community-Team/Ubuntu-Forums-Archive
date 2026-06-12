---
title: "synaptic/apt-get problem"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by cusri2004 on 2010-05-17
Hi there,

I was just tweaking the server settings to get rid of some gpg key  issues. They all of a sudden I see this error message in my synaptic

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.


sudo apt-get update says

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)

I don't know what is wrong with /etc/apt/sources.list file. I am just  posting the contents of the file here.

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/  hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for  how to upgrade to
# newer versions of the distribution.

deb New Zealand lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb New Zealand lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as  to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu  security
## team.
deb New Zealand lucid universe
deb New Zealand lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the  Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as  to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb New Zealand lucid multiverse
deb New Zealand lucid-updates multiverse

## Uncomment the following two lines to add software from the  'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it  includes
## newer versions of some applications which may provide useful  features.
## Also, please note that software in backports WILL NOT receive any  review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)  hardy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)  hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to  Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)  lucid partner

deb New Zealand lucid-security main restricted
deb New Zealand lucid-security universe
deb New Zealand lucid-security multiverse
# deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)  lucid main # disabled on upgrade to lucid


# deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable  non-free #Skype disabled on upgrade to lucid

---

### Post by portentum on 2010-05-17
I assume you made some changes to your sources.list yourself? 

Replace "New Zealand" in lines like ```
deb New Zealand lucid main restricted

```
with [http://ftp.citylink.co.nz/ubuntu/](http://ftp.citylink.co.nz/ubuntu/) so that they look more like
```
deb http://ftp.citylink.co.nz/ubuntu/ lucid main restricted
```
(this is an official Ubuntu mirror, as listed [here]("https://launchpad.net/ubuntu/+archivemirrors") unless I'm mistaken as to the purpose of that page)


**edit/update**: A cleaner fix for that would be [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) as shown here
```

deb http://nz.archive.ubuntu.com/ubuntu/ lucid main restricted

```

---

