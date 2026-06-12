---
title: "Could not download the upgrades on the last file"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by geovino on 2007-10-18
After 10 hours of downloading, on the 1353 of 1353 files I get this message

Could not download the Upgrades

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5_all.deb) Connection timed out [IP: 91.189.88.43 80]

Why after all that time? Was the whole download wasted?

I'll never do an upgrade in the first week of a new release again. I'll wait.

---

### Post by linuxwizard on 2007-10-18
Try removing or disable extra repos you have added to your source list.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by geovino on 2007-10-18
I have never touched the repos since I upgraded to Feisty last April. I checked the source.lst and there is a repos to automatix. would that do it? Automatix was uninstalled months ago.
Would that be the problem?

Here's the list: sources.list distroUpgrade

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
#AUTOMATIX REPOS END

I clicked on sources.list and it took me to Software Sources where I unchecked automatix in Third party Software.

Could this have caused the problem? Why didn't the installer catch that before the download?

---

### Post by geovino on 2007-10-18
Another question: I have a copy of the Ubuntu 7.10 RC1. Someone said that you can upgrade to Gutsy using it by running it in Synaptic. Is this true?

---

### Post by linuxwizard on 2007-10-18
If you have used EasyUbuntu or Automatix (neither of which is recommended nor supported), you may have problems upgrading to a newer version that requires a fresh install.

---

### Post by geovino on 2007-10-18
I just went into the sources.list.distUpgrade file and remmed out the automatix repo. would that help?

Should I try the upgrade through the 7.10 RC1 CD? 

I can't see why I didn't get a error message about automatix before the upgrade started. :confused:

---

### Post by linuxwizard on 2007-10-18
Not sure what to tell you about upgrading through the 7.10 RC1 CD. 
Your first post problem
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...buntu5_all.deb](http://us.archive.ubuntu.com/ubuntu/...buntu5_all.deb) Connection timed out [IP: 91.189.88.43 80] has to do with openoffice all debs which was added some how or automatix.

---

### Post by geovino on 2007-10-19
I Remmed out the repo to automatix on the sources.list.distUpgrade file and the sources.list.save file. But when I try to start the upgrade to 7.10 it seems like it doesn't want to start the process to upgrade. is it that the network is so busy that I can't upgrade for a couple more days?

---

### Post by linuxwizard on 2007-10-19
It could be that the network servers are busy or you still have another issue. Try again later see what happens.

---

### Post by geovino on 2007-10-19
OK, but shouldn't the update manager tell you about what errors to correct in the sources.list before trying to download?

---

