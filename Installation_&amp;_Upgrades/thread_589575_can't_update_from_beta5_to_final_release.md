---
title: "can't update from beta5 to final release"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Neo4 on 2007-10-24
My laptop has been in warranty and came yesterday, it had installed the beta5 release and now that they came I can't update to final release...

i go to the update manager click on search for updates and it can't find the repo's it said permission denied the only repo that works is the relase but nothing appear to update!

help me please!

---

### Post by ThrobbingBrain66 on 2007-10-24
Can you post the contents of your sources.list please?
```
cat /etc/apt/sources.list
```

---

### Post by Neo4 on 2007-10-24
for shure: 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

### Post by Neo4 on 2007-10-24
now the updates are showed but if i try to upload occurs the following error:

W: Falha ao obter [http://pt.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.0ubuntu5_i386.deb](http://pt.archive.ubuntu.com/ubuntu/pool/main/b/base-files/base-files_4.0.0ubuntu5_i386.deb)
  403 Forbidden
(...)
for all packages

---

### Post by ThrobbingBrain66 on 2007-10-24
Go to System > Adminstratoin > Software Sources and change the 'download from' mirror.  Looks like you are downloading some from your local mirror (pt) and some from the main server.  Changing them all to one server should fix your problem (I'd try the main server for the time being).

When you close the window it'll reload your sources.list and you should be able to update.

---

### Post by Neo4 on 2007-10-24
the problem was on the sinaptic it had proxy setings on..

sorry =/ i've forgot to check that before post

---

### Post by ThrobbingBrain66 on 2007-10-24
> **Neo4 said:**
> the problem was on the sinaptic it had proxy setings on..

sorry =/ i've forgot to check that before post

Not a problem....I'm glad you got your problem sorted out. :)

---

