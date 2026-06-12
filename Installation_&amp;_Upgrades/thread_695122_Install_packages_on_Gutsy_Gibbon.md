---
title: "Install packages on Gutsy Gibbon?"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by jano_rajmond on 2008-02-12
Hy... i have a (maybe stupid) question:

Take a look at this:

```
sudo apt-get install xmms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xmms
```

Except for a few packages (like g++ for example), any other package I try to install it says it cannot find them...

I mean if I take any package from [http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/) and then type ```
apt-get install <package> 
```  shouldn't it install it?? 

Also Pidgen does not connect (it says "Connecting..." but never does).

Firefox and Internet work fine!!!

Might this be a network config problem or what? Cause I just give up!

Thanks!

---

### Post by jano_rajmond on 2008-02-12
PS: I upgraded fro Feisty to Gutsy and with the same settings everything way OK @ Feisty. (By upgade I mean format and clean install(

---

### Post by taurus on 2008-02-12
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

p.s.  If you did a clean install of Gutsy, then it's not an upgrade!  It's a clean install.

---

### Post by jano_rajmond on 2008-02-12
```
cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by taurus on 2008-02-12
Do you see the # in front of all the repos?  That is why you can't install anything except whatever it's on the CD because you don't have those extra repos enable.  So, edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and put a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close gedit window.

Then run

```
sudo apt-get update
```
Now, see if you can install whatever else you plan to install before.

---

### Post by jano_rajmond on 2008-02-12
This did the trick. THANK YOU very much.

And also... I have two sound cards installed. The default one (set by the system after instalation) is the one on ny mother board. However when I switch to the one on the PCI sound does not work until restart. Any ideas?

---

### Post by taurus on 2008-02-12
If you plan to use the add-on soundcard as your default card, I would recommend you go into the BIOS and turn off the onboard soundcard.

---

### Post by jano_rajmond on 2008-02-13
I'll try to do that next time I reboot! Thank very mush for your help!

---

