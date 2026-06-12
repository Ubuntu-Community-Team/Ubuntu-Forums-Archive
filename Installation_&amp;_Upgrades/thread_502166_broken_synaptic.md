---
title: "broken synaptic"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by chrisbain88 on 2007-07-16
Hi,
I have tried to install NeroLinux v2.1.0.2 and i have had trouble.  When i try to open synaptic i get a msg about nerolinux needing to be reinstalled and archive can not be found.  When i try to reinstall the deb i get this might be corrupt and your are unable to open this file.  I have tried the apt-get install -remove commands in the terminal.  I have run out of ideas and do not wish to re install ubuntu to resolve the problem.
Any help would be appreciated.
Cheers
Chris

---

### Post by aysiu on 2007-07-16
Is it possible the .deb actually is corrupt? And have you considered using another burning program? K3B is excellent.

---

### Post by Soybean on 2007-07-16
This should certainly be fixable without any drastic measures. :)
> **chrisbain88 said:**
> I have tried the apt-get install -remove commands in the terminal.
Hmm... something along those lines should work. 

If you know the package name, "sudo aptitude remove *packagename*" ought to solve your problem. If it doesn't, could you copy-paste the exact error output into a forum post?

Oh, also, I don't see NeroLinux in the default repositories. So you must have had to add a custom repository to try to install it? A simple typo at that step could also be causing error messages every time you open Synaptic. If the "aptitude remove" idea doesn't work, posting your "/etc/apt/sources.list" file might also help.

---

### Post by chrisbain88 on 2007-07-16
the results for the "sudo aptitude remove nerolinux" is
chris@chris-laptop:~$ sudo aptitude remove nerolinux
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  nerolinux 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing nerolinux (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 nerolinux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

And the contents of the sources.list file are
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070418)]/ feisty main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

deb [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./
deb-src [http://orniere-du-globe.net/debian](http://orniere-du-globe.net/debian) ./

Cheers
Chris

---

### Post by chrisbain88 on 2007-07-16
> **aysiu said:**
> Is it possible the .deb actually is corrupt? And have you considered using another burning program? K3B is excellent.

A mate gave the .deb file to me so i thought i would try it, i have used K3B before and i am quiet happy with it.

The problem i have at the moment is that with the corrupt i can not use synaptic, add remove, the update manager or install other .deb files

---

