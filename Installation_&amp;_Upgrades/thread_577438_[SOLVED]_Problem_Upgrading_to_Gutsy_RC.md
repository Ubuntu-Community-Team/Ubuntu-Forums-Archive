---
title: "[SOLVED] Problem Upgrading to Gutsy RC"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by StanBlast on 2007-10-16
Hi All,

I was trying to upgrade from Feisty to Gutsy using the update manager and I got the error message below:

Failed to fetch [http://repository.debuntu.org/dists/gutsy/Release](http://repository.debuntu.org/dists/gutsy/Release) Unable to find expected entry  deb-src/binary-i386/Packages in Meta-index file (malformed Release file?)

Any idea how to fix this? Thanks!

Stan

---

### Post by PmDematagoda on 2007-10-16
Could you please post your sources.list file using:-

```
sudo gedit /etc/apt/sources.list
```

---

### Post by StanBlast on 2007-10-16
Hi PM, thanks for the prompt response :) Below is my source list :


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

#AUTOMATIX REPOS START

# deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
#AUTOMATIX REPOS END
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse Ubuntu Feisty Fawn deb [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) feisty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe

---

### Post by PmDematagoda on 2007-10-16
Organise the last 3 lines by doing this:-
```

deb http://repository.debuntu.org/ gutsy multiverse 
deb-src http://repository.debuntu.org/ gutsy multiverse
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe 
```

And see if that solves your problem.

---

### Post by StanBlast on 2007-10-17
Hi PM, thanks for the solution. I managed to get the upgrade done. :)
But I've got other issues, but that's for another thread. 
Thanks again!

:) :)

---

### Post by PmDematagoda on 2007-10-17
Glad to hear the problem was solved, I wish you good luck with the other issues you have and if possible will try and help you to solve them:).

---

