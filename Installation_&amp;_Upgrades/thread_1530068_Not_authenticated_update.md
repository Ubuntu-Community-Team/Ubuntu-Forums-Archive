---
title: "Not authenticated update"
date: 2010-07-13
forum: Installation &amp; Upgrades
---

### Post by noninyo on 2010-07-13
Hi all,

I try to update using update manager.

I got the massage: 
```
Warring
You are about to install software that can't be authenticated!
Doing this could allow a nalicious individual to damage or
take control of your system
```I try to write in the terminal:
```
sudo apt-get update
```but I get: 
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
```

Someone have idea what can I do?????

---

### Post by tommcd on 2010-07-13
> **noninyo said:**
> 
I try to update using update manager.
I got the massage: 

Warring
You are about to install software that can't be authenticated!
Doing this could allow a nalicious individual to damage or take control of your system.
Did you copy and paste that error message? Or did you type it by hand? There are some obvious typos there. I am just wondering if that was the exact error message you received. 

Have you added any 3rd party repos to your system? This includes the ppa repos. If so then you will need to add the GPG key for that repo. Post your */etc/apt/sources.list* file if you are not sure .
> 
```
sudo apt-get update
```but I get: 
```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
```
Do you have the update manager, the synaptic package manager, the software center, or any other package management utility open when you run: *sudo apt-get update*? If so, then you will need to close them. Then run *sudo apt-get update*.
What version of Ubuntu are you using?
Write back if you need more help.

---

### Post by noninyo on 2010-07-14
> **tommcd said:**
> Did you copy and paste that error message? Or did you type it by hand? There are some obvious typos there. I am just wondering if that was the exact error message you received. 

Have you added any 3rd party repos to your system? This includes the ppa repos. If so then you will need to add the GPG key for that repo. Post your */etc/apt/sources.list* file if you are not sure .

Do you have the update manager, the synaptic package manager, the software center, or any other package management utility open when you run: *sudo apt-get update*? If so, then you will need to close them. Then run *sudo apt-get update*.
What version of Ubuntu are you using?
Write back if you need more help.

I type the message bye hand. I attach photo of the massege [ATTACH]163359[/ATTACH]

I don't think I add 3rd party repos... just in case here is my sources.list
```
 # deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://za.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid universe
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```I close the  update manager and run *sudo apt-get update. *it didn't help I still get the same message.

thanks for the help!!!!

---

### Post by noninyo on 2010-07-14
ok I fix it...
I don't know how...
Thanks anyway!!!

---

### Post by tommcd on 2010-07-14
Well, your sources.list only has the official Ubuntu repos. I have never seen a message like that from using only the official repos.

By the way, you can add the **backports** repo, and the **Ubuntu partner** repo to your system if you wish. The backports repo sometimes has updates for programs that have been "backported" to the repos. These updates are generally not officially supported by Ubuntu though. The Partner repo has some proprietary stuff like the official java and some other stuff.
 You can also add the **medibuntu** repo to get the Windows codecs and libdvdcss. See these links about adding extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
These repos are optional though. You do not need them.
The first link there has a screenshot of the error you posted. If you would have clicked the plus sign "+" next to the words "NOT AUTHENTICATED" it would have presumably told what was not authenticated.
 You usually only see that when you are trying to add a 3rd party repo to your sources.list.
Write back if you need more help.

---

