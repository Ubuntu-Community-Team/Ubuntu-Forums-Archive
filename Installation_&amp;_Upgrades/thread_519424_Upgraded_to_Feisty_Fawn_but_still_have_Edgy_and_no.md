---
title: "Upgraded to Feisty Fawn but still have Edgy and now need 844 updates?"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by teknosexual on 2007-08-07
First of all, I checked to make sure my Edgy installation was up-to-date and I was running the correct version of update manager. 

I started the upgrade process and everything went smoothly, then I rebooted my system. Upon reboot, I received a black screen informing me that fsck failed and needed to be done manually, so I typed fsck into the command line. The system ran through various nodes that needed fixing, and quite frankly I have no idea what was going on, but I said yes to all the fixes.

After all the fixes, I rebooted my system and found my **Edgy Eft** installation still intact, except now update manager says I have **844 updates** I need to install! All of my data and settings seem to be intact, and update manager still prompts me to do a distro upgrade to...**Edgy Eft**!

I'm very confused. I'm kind of new to Ubuntu (using since April), so I don't know what to do or where to go from here. :confused: I also have a Windows XP partition on my hard drive (which seems to be intact). 

Any help is appreciated! Thanks in advance!!

---

### Post by Sam Liu on 2007-08-07
Hi tekno, could you post your sources.list?

---

### Post by teknosexual on 2007-08-07
> **Sam Liu said:**
> Hi tekno, could you post your sources.list?

Here it is:

> 
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

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
#AUTOMATIX REPOS END


I don't know if it matters, but I do not have Automatix installed anymore.

---

### Post by stchman on 2007-08-07
> **teknosexual said:**
> First of all, I checked to make sure my Edgy installation was up-to-date and I was running the correct version of update manager. 

I started the upgrade process and everything went smoothly, then I rebooted my system. Upon reboot, I received a black screen informing me that fsck failed and needed to be done manually, so I typed fsck into the command line. The system ran through various nodes that needed fixing, and quite frankly I have no idea what was going on, but I said yes to all the fixes.

After all the fixes, I rebooted my system and found my **Edgy Eft** installation still intact, except now update manager says I have **844 updates** I need to install! All of my data and settings seem to be intact, and update manager still prompts me to do a distro upgrade to...**Edgy Eft**!

I'm very confused. I'm kind of new to Ubuntu (using since April), so I don't know what to do or where to go from here. :confused: I also have a Windows XP partition on my hard drive (which seems to be intact). 

Any help is appreciated! Thanks in advance!!

I recommend a clean install of Feisty.

---

### Post by teknosexual on 2007-08-07
Well, I finally managed to actually get Feisty installed. I did a manual upgrade. After rebooting, I do have Feisty installed. So far everything seems okay. Maybe it was just a fluke with the GUI upgrade? If I come across any more details, I'll post back here.

---

### Post by zvacet on 2007-08-07
You have mixed source list and that can make problems to you.replace all edgy t ofeisty or try this source list

[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

