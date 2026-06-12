---
title: "unpluged network during install, can't update now"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by Sarmu on 2007-11-06
Hi

I've re-installed Gutsy today, the problem is during install the part with that "configureing apt : scanning for mirror" got stuck, therefore I unpluged the network cable to force it to skip this part and soon after I unpluged the cable it says something about security is not configured, and have to configure it later.

Now the problem is when I bootup gutsy, it seems i'm not able to connect to any server, Update Manager didn't find any new update, when trying to install NVIDIA restricted driver it doesn't automatic download the driver from server, instead it says "the software package nvidia-glx-new is not enabled". apt-get install always says "E: Package xxxxx has no installation candidate".

I know all these work if "configureing apt" succeeded during install, so I'm wondering how can I configure it now?

I know internet works and I can browse

---

### Post by alpage2 on 2007-11-06
The fact that the mirrors seemed not to be found during the installation could point to a networking problem. Earlier in the install, did it clearly confirm that the network was detected? Has your network adapter worked correctly in a previous version of ubuntu?

However, assuming for a moment that your network is up, you need to have a correct set of mirrors listed in /etc/apt/sources.list  - If not,  you will need to edit this file with root permissions. Look at your own copy first - it may contain references to your own install CD in the first few lines - keep those intact, since the equivalent references in my sources.list file, pasted below, will probably be different. If you don't know what should go there, just comment out all references to the install CD, and it should be able to fetch any package it needs from the mirrors.

 I am in the uk (hence the mirror addresses start with gb) and, if you are not in the uk, you should substitutute the 'gb' with the country code for the mirror that is closest to you - but that will keep until you get it working.

Post again if this does not fix it.

Regards
Alan
full contents of /etc/apt/sources.list follows:


#
# deb cdrom:[Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016)]/ gutsy main restricted

deb cdrom:[Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-2 (20071016)]/ gutsy main restricted
deb cdrom:[Edubuntu 7.10 _Gutsy Gibbon_ - Release i386 Binary-1 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by timcredible on 2007-11-06
if the installer doesn't see the repos, it disables all the repos, so just go into synaptic under the Settings-> Repositories tab and checkmark all the repos and then hit reload

---

### Post by Sarmu on 2007-11-06
> **alpage2 said:**
> The fact that the mirrors seemed not to be found during the installation could point to a networking problem. Earlier in the install, did it clearly confirm that the network was detected? Has your network adapter worked correctly in a previous version of ubuntu?

However, assuming for a moment that your network is up, you need to have a correct set of mirrors listed in /etc/apt/sources.list  - If not,  you will need to edit this file with root permissions. Look at your own copy first - it may contain references to your own install CD in the first few lines - keep those intact, since the equivalent references in my sources.list file, pasted below, will probably be different. If you don't know what should go there, just comment out all references to the install CD, and it should be able to fetch any package it needs from the mirrors.

 I am in the uk (hence the mirror addresses start with gb) and, if you are not in the uk, you should substitutute the 'gb' with the country code for the mirror that is closest to you - but that will keep until you get it working.

Post again if this does not fix it.

Regards
Alan

Thanks Alan, I'll give this a go later.

I know the network works during install, I can browse the net, and I've successfully connected to the mirror before. But I had to format few time due to extended partition issue with some other OS installation.

What I acctually wondered was where is the mirror connecting to (if all copy of install connects to a central server, or it connect to the nearest server from the location you specified) and if the server I'm connecting to is down or not.

Also if the only way to fix this is by editing /etc/apt/sources.list, then I would assume it will be a nightmare for those who installed ubuntu without network connection, and then pluged in the network cable after installation.

---

### Post by alpage2 on 2007-11-08
> **Sarmu said:**
> 

What I acctually wondered was where is the mirror connecting to (if all copy of install connects to a central server, or it connect to the nearest server from the location you specified) and if the server I'm connecting to is down or not.



I have not tried it, but I imagine, in the absence of an internet connection, that sources.list will contain some default mirror settings. (Have a look at yours, and that should answer your questi0on.) At worst, as indicated by timcredible, if those settings are disabled, that would explain why you are getting nowhere. But they can be enabled in a user friendly GUI way - thanks to timcredible for the reminder ;-)

So, to improve my previous method, for the benefit of those less familiar with the command line, just do this:

start the Synaptic Package Manager
Select 'Settings' from the menu bar
Choose 'Repositories'
Check the boxes for the repositories that you want to use, with 'Canonical maintained Open Source software: main' as an absolute minimum. Add more for a wider range of software.
In the drop-down list labelled 'Download from:' select your nearest mirror.
Finally hit the 'Close' button.

The /etc/apt/sources.list should now have been automatically modified accordingly.

This should get things configured correctly if there was no internet for external reasons, such as modem turned off or ISP down. On the other hand, if it was due to a hardware problem, like the network adapter not being configured correctly, then that would need to be fixed first, before worrying about the sources.

Regards
Alan

---

