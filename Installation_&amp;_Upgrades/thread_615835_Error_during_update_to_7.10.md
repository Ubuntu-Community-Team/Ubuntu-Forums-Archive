---
title: "Error during update to 7.10"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by flash19 on 2007-11-17
When I try to upgrade from feisty to gusty, I get this error message:


"Error during update"

"A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/di...6/Packages.bz2](http://security.ubuntu.com/ubuntu/di...6/Packages.bz2) Sub-process bzip2 returned an error code (2)"
 
I am able to install updates for feisty, but can't upgrade.
On another post I saw that some one said to go to System - administration - software sources and disable all the third party repos.  but there is nothing in the third party folder

Here is the contents of the /etc/apt/sources.list if that helps:

http://help.ubuntu.com/community/UpgradeNotes[/url] for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multive

One thing that stands out to me is that a lot say restricted. Why? 
Any help appreciated!

---

### Post by nicko7i on 2007-11-18
"Restricted" basically indicates that the software isn't fully open-source.  Not something that affects what we're doing here.

Your /etc/apt/sources.list shows that you're still at the Feisty 7.04 level.  You need to bring your 7.04 fully up to date before you can upgrade the distribution to 7.10.

Try running the update manager to get all the latest stuff for Feisty.  When that succeeds, you'll see a button for "dist-upgrade" to 7.10.

When using the update manager, sometimes the update doesn't fully succeed.  That might have happened to you .  Just try again.

One more thing... make sure you have space left on your disk, at least several hundred megabytes.  

Hope this helps

n

---

### Post by flash19 on 2007-11-29
I have run the update manager and I am fully up to date. one in a while though I get another update.  I have tried updateing to 7.10 I don't know how many times (10 +?) and it always has the same thing.  I will have to check how much room is left on the hard drive as it is only an 8 GB. Ubuntu is the only thing on it though.

---

### Post by Pumalite on 2007-11-29
Try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by PmDematagoda on 2007-11-29
I think it is something with the server itself, change the location of the server in Software Sources and try upgrading the system again.

---

