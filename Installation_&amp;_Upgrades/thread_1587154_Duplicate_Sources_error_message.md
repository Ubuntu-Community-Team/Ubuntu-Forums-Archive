---
title: "Duplicate Sources error message"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by PCTinker on 2010-10-03
What do I do about this? It appears every time I use the Synaptic Package Manager. The only difference I can see is *_main_* and *_restricted_* towards the end of each line of text.

W: Duplicate sources.list entry cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/main Packages (/var/lib/apt/lists/Ubuntu%2010.04.1%20LTS%20%5fLucid%20Lynx%5f%20-%20Release%20i386%20(20100816.1)_dists_lucid**_main_**binary-i386_Packages)

W: Duplicate sources.list entry cdrom://Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)/ lucid/restricted Packages (/var/lib/apt/lists/Ubuntu%2010.04.1%20LTS%20%5fLucid%20Lynx%5f%20-%20Release%20i386%20(20100816.1)_dists_lucid**_restricted_**binary-i386_Packages)

---

### Post by sikander3786 on 2010-10-03
Post the output of

```

cat /etc/apt/sources.list

```

---

### Post by PCTinker on 2010-10-03
deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted

deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-security main restricted universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-security multiverse

---

### Post by sikander3786 on 2010-10-03
The first 2 lines are giving the duplicate entry error.

Do you use Ubuntu 10.04.1 CD-ROM as a repository. I'll recommend to disable them, both of them, they can cause some problems with apt-get.

Go to System > Administration > Software Sources and untick Ubuntu CD-ROM or something like that on the first page.

Alternatively comment out the first 2 lines with # in /etc/apt/sources.list

```
gksu gedit /etc/apt/sources.list
```

Save, close and

```
sudo apt-get update
```

---

### Post by PCTinker on 2010-10-03
Done as you suggested. Problem solved!

Thank you. Have another bowl of popcorn :popcorn:

---

### Post by PCTinker on 2010-10-03
FYI this solved another problem where Computer Janitor listed a number of redundant files, yet when it tried to clean them up they couldn't be found.

---

