---
title: "Depends: libg2c0-dev but it is not going to be installed"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by roboa1983 on 2008-09-23
I believe this is related to a repository problem because a few months back my computer thought I should upgrade to the alpha version of Intrepid (8.10), so although I've changed /etc/apt/sources.list back to hardy, there are some unresolved issues.
By the way, when I changed sources.list, synaptic said that there were some repeated addresses, but I could not confirm it manually.
Namely, I have been trying to install g77 through synaptic and the following error shows up:

```

g77:
 Depends: g77-3.4 but it is not going to be installed

```

Similarly, when I try to get g77-3.4:

```
g77-3.4:
  Depends: gcc-3.4 (=3.4.6-6ubuntu5) but 3.4.6-8ubuntu1 is to be installed
  Depends: gcc-3.4-base (=3.4.6-6ubuntu5) but 3.4.6-8ubuntu1 is to be installed
 Depends: libg2c0-dev but it is not going to be installed
```

Finally, trying to install libg2c0-dev leads to the following answer:

```

libg2c0-dev:
  Depends: gcc-3.4-base (=3.4.6-6ubuntu5) but 3.4.6-8ubuntu1 is to be installed
 Depends: libg2c0 but it is not going to be installed

```

I'm tempted to install gcc-g77 manually, but that would not ultimately solve my synaptic problem. 
I appreciate the help.

---

### Post by oldos2er on 2008-09-23
Can you post the output of "cat /etc/apt/sources.list"?

---

### Post by roboa1983 on 2008-09-23
Hi
Here's /etc/apt/sources.list

```


deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hardy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
# deb http://debs.astraw.com edgy/
# deb http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
# deb-src http://wxpython.wxcommunity.com/apt/ubuntu/dapper /
# deb http://janvitus.interfree.it/ubuntu/ edgy-janvitus main-amd64deb http://3v1n0.tuxfamily.org dapper 3v1n0


#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu hardy partner

deb http://archive.ubuntu.com/ubuntu hardy-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu hardy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu hardy multiverse
#AUTOMATIX REPOS END
deb http://www.toastfreeware.priv.at/debian unstable/
deb-src http://www.toastfreeware.priv.at/debian unstable/
deb http://us.archive.ubuntu.com/ubuntu/ hardy main universe
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe main
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main restricted
deb http://archive.ubuntu.com/ubuntu/ hardy main universe multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse
deb http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main universe restricted multiverse #Added by software-properties



```
I accidentally posted one from another computer. My apologies. Now it's been corrected.

---

### Post by oldos2er on 2008-09-23
You've got Debian repositories mixed in with Ubuntu ones...not good. And mixing Intrepid and Heron repos isn't a great idea either. I'll post my Hardy Heron sources.list, which you can copy over yours if you like.

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted main multiverse universe 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe 
# deb [http://ubuntusatanic.org/hell](http://ubuntusatanic.org/hell) hardy main

# Eternity Screensaver
# deb [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main
# deb-src [http://parker1.co.uk/apt](http://parker1.co.uk/apt) hardy main

---

### Post by roboa1983 on 2008-09-23
Hi 
I know it's no good to have intrepid and heron. I wish I could have avoided it :)
I am now using your sources.list file, but the problem persists. Could it be because of this hardy/intrepid mess has the terminations (see below) messed up?

```

libg2c0-dev:
  Depends: gcc-3.4-base (=3.4.6-6ubuntu5) but 3.4.6-8ubuntu1 is to be installed
 Depends: libg2c0 but it is not going to be installed

```

---

### Post by oldos2er on 2008-09-23
> **roboa1983 said:**
> Hi 
I know it's no good to have intrepid and heron. I wish I could have avoided it :)
I am now using your sources.list file, but the problem persists. Could it be because of this hardy/intrepid mess has the terminations (see below) messed up?

```

libg2c0-dev:
  Depends: gcc-3.4-base (=3.4.6-6ubuntu5) but 3.4.6-8ubuntu1 is to be installed
 Depends: libg2c0 but it is not going to be installed

```

 Yes, it could be because of that. Did you run "sudo apt-get update"?

---

### Post by roboa1983 on 2008-09-29
Hi again
I tried it also with 
```

sudo apt-get update

```

I'm still guessing this has to do with the update to Intrepid that messed things up. It seems there's no way to revert. Do you have an idea what
"3.4.6-8ubuntu1" and "3.4.6-6ubuntu5" mean?

---

