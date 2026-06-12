---
title: "Help/Suggestions on how to recreate my current installation after upgrade breakage"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by twgray on 2015-03-30
After my recent upgrade to the latest LTS Xubuntu 14.04 I have several glitches and problems.  I would like to perform a new install from DVD, but I want to reinstall all my current PPAs w/keys, and all my current packages.  I have found this guide for reinstalling my existing packages:

[https://help.ubuntu.com/community/ReinstallingSamePackages?action=fullsearch&value=linkto%3A%22ReinstallingSamePackages%22&context=180](https://help.ubuntu.com/community/ReinstallingSamePackages?action=fullsearch&value=linkto%3A%22ReinstallingSamePackages%22&context=180)

but there is no mention of how to handle all the PPAs that I have installed.  I could just copy my /etc/apt directory to the new installation but I am not sure if this will also copy all the PPA keys.  

Does anyone have any suggestions before I proceed?

---

### Post by grahammechanical on 2015-03-30
The upgrade process should disable any Personal Package Archives (PPA) and there is a reason for this. The developer of the software may not have created an archive for 14.04. So, I would first advise checking the PPAs to see if there is actually a trusty PPA for that software. Otherwise enabling the PPA will cause Update Manager to throw out errors.

One of the reasons why some of us recommend doing a fresh install instead of an upgrade is that the upgrade scripts cannot take into account all the modifications we users make to our systems. I would include software installed through a PPA. If you succeed in what you want to do you may find that the new install also has problems.

---

### Post by twgray on 2015-03-30
That is all true, but I am talking about PPA's that I have added and that ARE WORKING...all packages I have added after the botched upgrade attempt...packages that have been released for 14.04.  

So, to clarify, I need to install all the packages currently on my system, including all the packages from PPAs.  Will copying the contents from the /etc/apt folder also copy all the keys from the various PPA's that I have added?

---

### Post by Vladlenin5000 on 2015-03-30
Perhaps you should consider Y-PPA Manager: [https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager) (and yes, with that one more PPA for the list)

---

