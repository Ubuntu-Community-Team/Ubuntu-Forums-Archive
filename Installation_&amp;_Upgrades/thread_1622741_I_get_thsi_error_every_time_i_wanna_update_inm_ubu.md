---
title: "I get thsi error every time i wanna update inm ubuntu 10.04"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by Edgar117 on 2010-11-15
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

Then i went to the terminal and put this command
cat /etc/apt/sources.list

I got this
deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://sv.archive.ubuntu.com/ubuntu/](http://sv.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

Any solutions ubuntu PROS :popcorn:

---

### Post by drs305 on 2010-11-15
Comment out this line:
> 
**deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted**
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

If you don't have that CD inserted (the install CD) you will get that message every time.

To edit the file:
```
gksu gedit /etc/apt/sources.list
```
Save the file, then update the sources list:
```
sudo apt-get update
```

---

### Post by Edgar117 on 2010-11-15
> **drs305 said:**
> Comment out this line:


If you don't have that CD inserted (the install CD) you will get that message every time.

To edit the file:
```
gksu gedit /etc/apt/sources.list
```Save the file, then update the sources list:
```
sudo apt-get update
```


Where o what do i edit

And yes i have the CD inserted what can i do from here .?:guitar:

---

### Post by Edgar117 on 2010-11-15
> **Edgar117 said:**
> Where o what do i edit

And yes i have the CD inserted what can i do from here .?:guitar:
Oooooooooooooooooohhhhh now i get it

thank you soo very much !!:P

---

### Post by drs305 on 2010-11-15
> **Edgar117 said:**
> Where o what do i edit

And yes i have the CD inserted what can i do from here .?:guitar:

Sorry I wasn't clearer. By "comment out" we mean to insert a **#** symbol at the start of the line. That tells the script to disregard what follows. The convention is often used by programmers to include comments about what the following commands will do.

> **[COLOR="DarkRed"]#[/COLOR]** deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted

You can also disable it by opening Synaptic, Software Sources or Software Center. In Synaptic/Software Sources: Settings, Repositories, Ubuntu Software tab: Untick the CD in the bottom panel. Other CDs would be listed in the Other Software tab.

Note: The CD in the sources.list is the original install CD. Even if you upgrade, the original CD will most likely still be listed.

---

