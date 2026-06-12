---
title: "Fresh install or upgrade?"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by lordfkiller on 2007-10-20
Hello.

I have some softwares installed from source code (SVN). Also my GPU driver is installed manually (downloaded from nVidia website). But all other softwares are installed from repos. Is my system a good candidate for upgrade or I am better install a fresh Gusty?

Also, when I click reload in Synaptic, I get an error because of wrong PGP or something like that. Is it because Gusty is released and Feisty is no more supported?

Thanks for any help.

---

### Post by lordfkiller on 2007-10-21
Any idea?

---

### Post by Sef on 2007-10-21
> Also, when I click reload in Synaptic, I get an error because of wrong PGP or something like that. Is it because Gusty is released and Feisty is no more supported?

Neither.  Sounds more like you there is a bad repository in your sources list.  Most likely from installing something.

1) Could you copy and paste, or post the error in detail.

2) Could you copy and paste your sources list.

Applications > Accessories > Terminal

then type or copy and paste this command:

gksudo gedit /etc/apt/sources.list

---

### Post by lordfkiller on 2007-10-21
I just tried again and didn't get an error this time. Perhaps it has been a temporary problem with a server.

But when I view details for package updating process, many repositories fail(though no error occures). Following is my sources.list . In the meantime, would you mind commenting on my other(main) question which is about upgrading to Gusty?

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

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
# deb [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://ir.archive.ubuntu.com/ubuntu/](http://ir.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib
# deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

---

### Post by lordfkiller on 2007-10-24
Should I install gusty from the scratch or upgrade? If upgrade, then using package manager or...? Please help.

---

### Post by lordfkiller on 2007-10-27
?

---

### Post by lordfkiller on 2007-11-01
I have not upgraded yet! No one can help me there?!!

---

### Post by coldswede on 2007-11-01
If it was me I'd just do a fresh install, I tried upgrading and had problems.  The fresh install went perfectly

---

