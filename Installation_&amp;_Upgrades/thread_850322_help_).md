---
title: "help :)"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by v_eye on 2008-07-05
hay guys im a very new user to Ubuntu or any other products of Linux,

i was trying to get wine to run but I've some how screwed it up and it now coming up with a error saying:

could not mark all packages for installations or upgrades 

the following packages have unresolvable dependencies. make sure that all required repositories are add and enabled in the preferences.
    
wine:
 Depends: libldap2 (>=2.1.17-1) but it is not installable

can any one help or give a little advise for me :D thank you :)

---

### Post by PmDematagoda on 2008-07-05
Can you post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by v_eye on 2008-07-05
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


think thats it :)

---

### Post by PmDematagoda on 2008-07-05
How are you trying to install Wine?

---

### Post by v_eye on 2008-07-05
installing trough synatic package manager but i also went through wine hq and followed the steps fo the instalation and that was through console, 

followed this

Adding the WineHQ APT Repository:

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then update APT's package information by running 'sudo apt-get update'.

Now you can install Wine by clicking this link. Alternatively, you can install by going to Applications->Add/Remove and searching for Wine.
Upgrading to a new version of Ubuntu

If you are upgrading the entire system, such as going from Ubuntu 7.10 to 8.04, you will need to come back to this page and enter the command for the new version above. The built in update manager will not switch the Wine repository automatically.
Older .deb packages

Since the APT repository can only hold the latest packages, older versions of the packages are available at the WineHQ .deb packages archive.

You can install the packages by double-clicking on them.

Very fast and reliable webhosting for the APT repository is graciously provided by budgetdedicated.com.

---

### Post by justin whitaker on 2008-07-05
> **v_eye said:**
> installing trough synatic package manager but i also went through wine hq and followed the steps fo the instalation and that was through console, 

followed this

Adding the WineHQ APT Repository:

First, open a terminal window (Applications->Accessories->Terminal). Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

Next, add the repository to your system's list of APT sources:

For Ubuntu Hardy (8.04):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list](http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/winehq.list

For Debian Etch (4.0):
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/etch.list](http://wine.budgetdedicated.com/apt/sources.list.d/etch.list) -O /etc/apt/sources.list.d/winehq.list

Then update APT's package information by running 'sudo apt-get update'.

Now you can install Wine by clicking this link. Alternatively, you can install by going to Applications->Add/Remove and searching for Wine.
Upgrading to a new version of Ubuntu

If you are upgrading the entire system, such as going from Ubuntu 7.10 to 8.04, you will need to come back to this page and enter the command for the new version above. The built in update manager will not switch the Wine repository automatically.
Older .deb packages

Since the APT repository can only hold the latest packages, older versions of the packages are available at the WineHQ .deb packages archive.

You can install the packages by double-clicking on them.

Very fast and reliable webhosting for the APT repository is graciously provided by budgetdedicated.com.

The budgetdedicated repo is not showing in your sources list. Readd the key, and try adding the repo again. 

You can also download WINE off that site by going to the distro specific page, and going to the archives link. You can then use gdebi to install it.

---

### Post by v_eye on 2008-07-05
nice one just got it running :) thanks guys

---

