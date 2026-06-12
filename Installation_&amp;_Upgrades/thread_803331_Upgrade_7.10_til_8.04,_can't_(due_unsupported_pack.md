---
title: "Upgrade 7.10 til 8.04, can't (due unsupported package?)"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Darkmoor on 2008-05-22
Hi,

I'm trying to upgrade my ubuntu 7.10 to 8.04 but are getting this message

Could not calculate the upgrade 

A unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

(I'm running the upgrade from at terminal since the upgrade does not appear in "update manager)"

running  "lsb_release -a" gives
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

So I think that the problem is with the "Unofficial..." But how can I be sure about that? And how can I easily remove those if that is the problem?

---

### Post by Partyboi2 on 2008-05-22
Open up "Software Sources" (System>Admin>Software Sources) on the 2nd tab untick all 3rd party repo's then close and try the upgrade again.

---

### Post by Darkmoor on 2008-05-22
None of 3rd party was ticked.

---

### Post by Tommy on 2008-05-22
> **Darkmoor said:**
> None of 3rd party was ticked.

Paste the contents of /etc/apt/sources.list here

---

### Post by Darkmoor on 2008-05-22
emile@hal9001:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by zvacet on 2008-05-22
```
sudo apt-get update && sudo apt-get upgrade
```

Then try to upgrade again.

---

### Post by Tommy on 2008-05-22
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```Then try to upgrade again.

Especially if you see any errors with the apt-get upgrade, I would ALSO recommend 

```
 sudo apt-get dist-upgrade 
```

before trying the Hardy upgrade again. That way if there are some existing unresolved package dependencies they can get sorted out first.

I looked over your sources.list and nothing seemed wrong, though I suppose there could possibly be some sort of error on the dk.archive.ubuntu.com server (it seems unlikely). When you do your apt-get upgrade it should report server errors, and apt-get dist-upgrade will report any package errors. If you narrow down the problem to a specific package, you can uninstall it, do the upgrade, and install it in your upgraded system.

---

### Post by Darkmoor on 2008-05-23
Running update, upgrade and dist-upgrade gives no errors. The message I get is:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Tommy on 2008-05-23
> **Darkmoor said:**
> Running update, upgrade and dist-upgrade gives no errors. The message I get is:

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

My Ubuntu 7.10 system has been showing an upgrade button since shortly after the official release of 8.04. Since yours is not and there are no pending upgrades, I wonder if maybe the upgrade tool cannot "see" the hardy repository in the archive for some reason.

You know, another way to do the upgrade is to download the iso and either mount it or burn a disk and mount that... it should recognize the archives on the disk and offer to do an upgrade then.  

Of course, after all this you might decide it's less hassle to back up all your data and start with a clean install... it's usually MUCH faster than an upgrade!

---

