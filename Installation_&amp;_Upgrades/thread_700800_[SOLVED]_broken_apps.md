---
title: "[SOLVED] broken apps"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by mugatea on 2008-02-18
I got Linux yesterday and am very new to all this.  I got it on DVD with a Ubuntu manual.

I cant install gimp from the synamptic manager cause when i try this message appears:
[I]
E: /var/cache/apt/archives/gimp_2.4.2-0ubuntu0.7.10.1_i386.deb: corrupted filesystem tarfile - corrupted package archive[/I]

and when I try to install a firefox update another similar message appears.

Is there something wrong with my DVD?

Jamie

---

### Post by xeth_delta on 2008-02-18
Welcome to the forums! It is possible there's something wrong with your DVD. You can install programs from the repositories via the internet.

Are the repositories (besides the DVD) enabled?

---

### Post by froy02 on 2008-02-18
Open your Synaptics Package Manager then go to Settings ->Repositories.  When the Software Sources window comes up go to Installable from CD-ROM/DVD and uncheck both Cdrom with Ubuntu 7.10 'Gutsy Gibbon'.
This would force Synaptics to go to the internet for the applications you are trying to install.

If this helps you please mark it Solved.

---

### Post by mugatea on 2008-02-18
no its not worked.  I've found out the drive E: is my hard drive, it's partioned with xp on the other half.


Jamie

---

### Post by xeth_delta on 2008-02-18
> **mugatea said:**
> no its not worked.  I've found out the drive E: is my hard drive, it's partioned with xp on the other half.


Jamie

I am sorry, but I don't understand what you mean by the last post and how it relates to the original problem. Can you be a little more specific?

Please open a terminal / console and type the following:
```
gedit /etc/apt/sources.list
```
Copy the contents of the file and post it in the thread.

---

### Post by mugatea on 2008-02-18
thanks fo your help, its all getting me a bit down tbh.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse

---

### Post by xeth_delta on 2008-02-18
Please don't be discouraged, it might seem a little overwhelming at the beginning, but you'll see it os actually not that difficult.

Open a terminal and type:
```
gksudo gedit /etc/apt/sources.list
```

place a # in front of the line
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
```
so that it looks like:
```
#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
```
Once that is done, save the file.
Go back to the terminal and type:
```
sudo apt-get clean
```
```
sudo apt-get update
```
Open synaptic and install your favourite software. Good luck!

---

### Post by mugatea on 2008-02-18
wow, it worked thanks.  I have no idea what you did, but it worked.  Thanks.

Jamie

---

### Post by xeth_delta on 2008-02-18
> **mugatea said:**
> wow, it worked thanks.  I have no idea what you did, but it worked.  Thanks.

Jamie

You are most welcome! What we did was tell the package managements system to get the software from the repositories over the internet instead of getting them from the CD. Then we cleaned the cache (in case there were any corrupted packages) and finally updated the package database.

Good luck and enjoy your Ubuntu Linux system!

---

