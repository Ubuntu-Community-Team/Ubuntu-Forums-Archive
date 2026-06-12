---
title: "No release found performing upgrade of hardy to lucid"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by victorforde on 2012-08-20
Hi,
 
I am attempting the upgrade of 8.0 LTS to 10.04 LTS. I have seen the steps identified in the server section that this can be done directly from 8.04 to 10.04 [https://help.ubuntu.com/community/LucidUpgrades/](https://help.ubuntu.com/community/LucidUpgrades/) 
 
I have done the following steps
 
1.) apt-get update (updated)
2.) apt-get upgrade (nothing to upgrade)
3.) apt-get install update-manager-core (installed 5 additonal packges as well) 
4.) do-release-upgrade
 
it reported "No new release found" 
 
then I performed 
 
5.) apt-get distrib-upgrade ( This brought it from kernel revision 2.6.24-24 to 2.6.24-32)
 
Re-ran the first 4 steps ending up with the same result of "No new release found"
 
rebooted and reran steps 1-4 with the same result. Can anyone assist?
 
I am downloading the alternate-cd media for 32-bt lucid LTS 10.04 in the mean time as I will probably follow those steps for upgrading with the offline media.
 
System info below;
 
uname -a output
 
Linux opsview-appliance 2.6.24-32-virtual #1 SMP Thu Jul 12 15:58:13 UTC 2012 i686 GNU/Linux
 
/etc/lsb-release output
 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.4 LTS"
 
Below is my repository entries;
 
/etc/apt/sources.list.d/ubuntu.list output
 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
 
/etc/apt/sources.list.d/ubuntu-universe.list output
 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe multiverse
 
This is probably a basic set-up issue so will most likely be marked in the newbie section.
 
Thanks in Advance,
 
Victor

---

### Post by black veils on 2012-08-20
i cannot help you with your actual queries, but..

cant you just use installation media to install the version you want? 10.04 end of life is april 2013.

if you are trying to keep a light system, or something familiar like gnome 2, then you can install Xubuntu/Linux Mint xfce (light), or Lubuntu (lighter with less features).

---

### Post by darkod on 2012-08-20
8.04 LTS is EOL (End Of Life). The repositories are closed.

In this link there are steps how to change the sources.list to the archived repositories:
[https://help.ubuntu.com/community/EOLUpgrades/](https://help.ubuntu.com/community/EOLUpgrades/)

If you can, I guess a clean install of 10.04 LTS or even 12.04 LTS would be much better option. Even if you upgrade from 8.04 to 10.04 without any problems, 10.04 is supported only 8 months more. So, soon it will be EOL too and you will have to do another upgrade.

Doing many upgrades in a row makes it more probable things to go wrong.

---

### Post by victorforde on 2012-08-20
Ok thanks for that. I have done the upgrade to 10.04 from the download media as opposed to repository but as you said long term it would makes sense to go to the 12.04 **L**ong **T**erm **S**upport release.
 
Thanks for the reponses

---

