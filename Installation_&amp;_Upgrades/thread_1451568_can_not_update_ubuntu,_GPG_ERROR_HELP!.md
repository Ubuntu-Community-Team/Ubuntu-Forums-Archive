---
title: "can not update ubuntu, GPG ERROR HELP!"
date: 2010-04-10
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2010-04-10
hey everyone, i have already had this problem and fixed it, i followed the steps taken last time, yet i have had no luck. my sources list is as follows

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic main restricted 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic main restricted 

###### Ubuntu Update Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic-security main restricted 
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic-updates main restricted 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic-security main restricted 
deb-src [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) karmic-updates main restricted 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Banshee - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main 

#### GetDeb - [http://www.getdeb.net](http://www.getdeb.net)
## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

#### MediaInfo - [http://mediainfo.sourceforge.net](http://mediainfo.sourceforge.net)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) karmic main

#### Medibuntu - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free 

#### Pidgin - [http://pidgin.im](http://pidgin.im)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8   
deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

#### Themes for GNOME and Ubuntu - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main 

#### VLC Media Player  - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) karmic main 


####### 3rd Party Source Repos

#### Banshee (Source) - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) karmic main  

#### MediaInfo (Source) - [http://mediainfo.sourceforge.net](http://mediainfo.sourceforge.net)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9D8BC54
deb-src [http://ppa.launchpad.net/shiki/mediainfo/ubuntu](http://ppa.launchpad.net/shiki/mediainfo/ubuntu) karmic main

#### Medibuntu (Source) - [http://www.medibuntu.org/](http://www.medibuntu.org/) 
## Run this command: sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update 
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free 

#### Pidgin (Source) - [http://pidgin.im](http://pidgin.im)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A1F196A8   
deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) karmic main

#### Themes for GNOME and Ubuntu (Source) - [https://edge.launchpad.net/~bisigi/+archive/ppa](https://edge.launchpad.net/~bisigi/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 881574DE
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main

#### VLC Media Player  (Source) - [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40130828
deb-src [http://ppa.launchpad.net/c-korn/ppa/ubuntu](http://ppa.launchpad.net/c-korn/ppa/ubuntu) karmic main

-------------------------------------------------------------------------------

I do not know what to do, i have tried everything i know ? please help D:

---

### Post by emanuel.b on 2010-04-10
You could try deactivating the third party repos.

---

### Post by slashwannabe94 on 2010-04-10
> **emanuel.b said:**
> You could try deactivating the third party repos.
how do i do that

---

### Post by emanuel.b on 2010-04-10
Ok, it's simple. First go to "System -> Administration -> Software Sources" from the main menu.

Then click on the "Other Software" tab, and un-check all the items listed.

I included some screen-shots to help.

---

### Post by slashwannabe94 on 2010-04-10
im having too much trouble, dude can you help me like completley do it from scratch

---

### Post by emanuel.b on 2010-04-10
Ok, what are you trying to do in the first place? Do you need help Updating, or Upgrading to 10.04?

---

### Post by slashwannabe94 on 2010-04-10
i want to update my system NOT upgrade. what has been done to my sources list or whatever i do not know, but what i do know is the error i receive when i try to update

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

---

### Post by emanuel.b on 2010-04-10
> **slashwannabe94 said:**
> i want to update my system NOT upgrade. what has been done to my sources list or whatever i do not know, but what i do know is the error i receive when i try to update

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://uk.archive.ubuntu.com](http://uk.archive.ubuntu.com) karmic-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

Ok then, here's  how to fix those problems.

First open a terminal, then copy (ctrl + c) and paste (ctrl + shift + p) this:

```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
```

After, you'll want to go back to the software sources, and activate the main server. I attached a screenshot to help.

That's it! That should work! :)

---

### Post by slashwannabe94 on 2010-04-10
It worked!!!!!! Thanks man you saved my hide :d :d :d

---

### Post by emanuel.b on 2010-04-10
You're very welcome, always glad to help. ;)

---

