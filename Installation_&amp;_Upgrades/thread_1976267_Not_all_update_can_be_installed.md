---
title: "Not all update can be installed"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by brydong on 2012-05-08
Since upgrading to 12.04, update manager no longer runs fully. It stops with the following message:

"Not all updates can be installed

This cab be caused by...."

The options are "Partial Upgrade" or "Close"\

Running "Partial Upgrade" fails with "Cannot upgrade

An upgrade from 'precise' to 'oneiric' is not supported with this tool."

Any tips on how to diagnose and get past this??

---

### Post by Cavsfan on 2012-05-08
> **brydong said:**
> Since upgrading to 12.04, update manager no longer runs fully. It stops with the following message:

"Not all updates can be installed

This cab be caused by...."

The options are "Partial Upgrade" or "Close"\

Running "Partial Upgrade" fails with "Cannot upgrade

An upgrade from 'precise' to 'oneiric' is not supported with this tool."

Any tips on how to diagnose and get past this??

I would just use this method of getting my updates if I were you:

```
sudo apt-get update 
sudo apt-get upgrade
```That will show you if there is anything held back.
If there is a kernel or something held back enter this to get it:

```
sudo apt-get dist-upgrade
```

---

### Post by Cavsfan on 2012-05-08
Also, you probably need to edit your sources file

```
gksudo gedit /etc/apt/sources.list
```

Change any occurrence of **precise** to **oneiric**.

---

### Post by brydong on 2012-05-08
I'm on 12.04. What I can't figure out is what's trying to move backwards?

My sources.list appears to be all "precise"...

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by Cavsfan on 2012-05-08
Just edit sources - **gksudo gedit /etc/apt/sources.list** and click "search" and then "replace"
Enter **precise** in Search for and **oneiric** in Replace with.
Save it and then do the update commands I mentioned.

I always do a clean install myself.

You never want to do a Partial upgrade and the CLI commands will never let you down.

---

### Post by brydong on 2012-05-09
Sorry I'm a bit confused. I want to be on 12.04, and I am. You're suggesting I move everything back to oneiric and then? Run an install of 12.04?

---

### Post by Cavsfan on 2012-05-10
> **brydong said:**
> Sorry I'm a bit confused. I want to be on 12.04, and I am. You're suggesting I move everything back to oneiric and then? Run an install of 12.04?

My mistake, I had the versions backwards. I see everything is set to precise with few still set to natty, but those are commented out.

What is the output of these commands run in terninal?
```
sudo apt-get update
sudo apt-get upgrade
```Highlight the results and click the # button on the top right to put CODE around it.

---

### Post by brydong on 2012-05-10
I marked it closed as I believe I managed to get through this. My hunch is the upgrade simply didn't complete correctly which explains other issues I was seeing like HUD not working well. I finally make it through a dist-upgrade and I think I'm good now.

thanks for your help!

---

### Post by judedawson on 2013-02-22
Hi there,

My wife's laptop running 12.04LTS also had the same problem recently. 

Following the suggestions in step#2 solved it.

Thanks very much :)

From,
Jude

---

### Post by Cavsfan on 2013-02-23
> **judedawson said:**
> Hi there,

My wife's laptop running 12.04LTS also had the same problem recently. 

Following the suggestions in step#2 solved it.

Thanks very much :)

From,
Jude

You are welcome Jude! :)

I would suggest using the terminal method for all your updates and to make it easier do the following.
Someone on this forum told how me to do this and it was good advice.

**gksudo gedit ~/.bashrc**

Find the other lines and enter the 3 bold lines after them:

```
# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

[B]# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'[/B]
```

Then save the file.

Just logoff and backon and then in terminal enter **ud** and it will ask for your password and see if there are any updates available.

If there is anything held back, like a new kernel etc. enter **ud2** and whatever is held back will be installed.

---

