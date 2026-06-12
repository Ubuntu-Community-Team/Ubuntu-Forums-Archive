---
title: "Can't install wine"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by aidy_99 on 2008-11-21
Hi I'm trying to install wine and keep getting the error message  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
E: Broken packages
Has anyone had this before? Any help would be great.:confused:

---

### Post by taurus on 2008-11-21
Which release are you running and can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by aidy_99 on 2008-11-21
Source list is

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

## deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# deb [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) gutsy main
# deb-src [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu) gutsy main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"


I'm trying to install wine 1.0.1, hope this helps.:confused:

---

### Post by taurus on 2008-11-21
Is that the whole /etc/apt/sources.list or is that just only the last part/half?

---

### Post by aidy_99 on 2008-11-21
That's the lot!

---

### Post by taurus on 2008-11-21
Maybe you want to add a few more.

Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and add the following lines to the end of it.

```

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse

deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted

deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

---

### Post by aidy_99 on 2008-11-21
Many many many thanks!! All sorted!:):):):)

---

