---
title: "can't upgrade from 12.4 to 14.4"
date: 2014-10-16
forum: Installation &amp; Upgrades
---

### Post by casper8 on 2014-10-16
Hi all,

I have been at this for days now... and I have realised i need some help on this!

When i login i get this screen:

> Your current Hardware Enablement Stack (HWE) is no longer supportedsince 2014-08-07.  Security updates for critical parts (kernel
and graphics stack) of your system are no longer available.


For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)


To upgrade to a supported (or longer supported) configuration:


* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade


OR


* Install a newer HWE version by running:
sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty


and reboot your system.


*** System restart required ***
Last login: Thu Oct 16 08:04:32 2014
dingit@mail01:~$




when i try to run either the 

> sudo do-release-upgrade -d

or

> sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty

I get a ton of error about not being able to download the updates or even connect to the different servers for updates.. 

some of the failed errors i get is this, don't know if it says much..

> === Command terminated with exit status 1 (Thu Oct 16 08:30:41 2014) ===

I also see a ton of > Failed to fetch followed by different repositorie urls.. 

here is my souce.list file info:

> 
 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
 deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty multiverse
#deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty multiverse
#deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
#deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
#deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main


# deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib # disabled on upgrade to trusty
# deb [http://webmin.mirror.somersettechsolutions.co.uk/repository](http://webmin.mirror.somersettechsolutions.co.uk/repository) sarge contrib # disabled on upgrade to trusty





I have no idea how to proceed from here.. reinstalling the server is not an option. I did do a snapshot before update so i can rolle back to it but this is a mail server which means mails will be lost.. in other words rolling back is my absolute last option.. 

help me obi wan kenobi, you are my only hope!

---

### Post by ibjsb4 on 2014-10-16
Your sources list say you are running trusty. 'do-release-upgrade -d' will send you to 14.10; do you really want to do that? 
> deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/main/binary-i386/
deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ dists/precise/restricted/binary-i386/
deb cdrom:[Ubuntu-Server 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.2)]/ precise main restricted
You Need to comment (#) the above out.

Also you have trusty-security updates disabled in the sources list.  Why??

After you get this figured out, do:
```
sudo apt-get update && sudo apt-get dist-upgrade
```
You should now be on the latest kernel.

---

### Post by casper8 on 2014-10-16
Hi Ibjsb4,

Thanks for answering... 

I want to be running LTS... i just assumed it would bring to the newst version of ubuntu server LTS?

---

### Post by grahammechanical on 2014-10-16
This command

> [COLOR=#000000]*sudo apt-get install linux-generic-lts-trusty linux-image-generic-lts-trusty*[/COLOR]

would have kept you on 12.04 LTS but with the Linux kernel and firmware that is now in 14.04 (trusty). Which command did you run first? If it was do-release-upgrade or a variant of it, then the second command was not necessary. This link will (hopefully) explain what that original message about the your hardware enablement stack no longer being support was all about.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

To put it simply from the release of 12.04 there have been 5 upgrades to the Linux kernel and firmware in what are called point releases. But only the kernels in 12.04.0; 12.04.1 and 12.04.5 will be supported until 2017.

These us us who moved from 12.04.1 to 12.04.2 or 12.04.3 or 12.04.4 but did not move on to 12.04.5 would be on kernels and firmware that would not be supported beyond 7th August 2014.

The usual update/upgrade process normally moves us through the point releases often without us knowing it. The important question now is, can you still update and if not what are the error messages?

Regards.

---

### Post by casper8 on 2014-10-16
Hi,

I did do the do-release-upgrade which didn't help me much.. than i tried the linux-generic thing.. failed too.. than i did do-release-upgrade -d no joy... 

do you know where i can find the error messagenes if i can't than i need to point to my original post and the error messanges i have posted there..

---

