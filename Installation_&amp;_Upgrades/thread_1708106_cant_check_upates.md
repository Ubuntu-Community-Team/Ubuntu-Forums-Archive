---
title: "cant check upates"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2011-03-16
I upgraded to the 10.10 and now I get a red triangle with a explanation point in the middle on the upper right hand of my screen next to the time and date.  It apparently has to do with the update manager because when I click on it, it opens up the update manager.  But when I try to install the updates I get the following message:

[PHP]Failed to lock the package manager

Check if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.[/PHP]

---

### Post by zvacet on 2011-03-16
As another way to update close update manager and type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Dutch70 on 2011-03-16
That usually happens when you have more than one of these three opened.

Synaptic Package Manager
Software Center
or the Terminal

---

### Post by louis.roux on 2011-03-16
@ zvacet: I did that but the following comes up in the terminal

```
owner@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for owner: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
owner@ubuntu:~$ 
```

@ Dutch70: I do not have more then one of those open.  In fact I have rebooted my computer several times to see if I could get it to work.

---

### Post by Dutch70 on 2011-03-16
> **louis.roux said:**
> @ zvacet: I did that but the following comes up in the terminal

```
owner@ubuntu:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for owner: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
owner@ubuntu:~$ 
```

@ Dutch70: I do not have more then one of those open.  In fact I have rebooted my computer several times to see if I could get it to work.

11: Resource temporarily unavailable

That probably means that the mirror you're getting your updates from is currently down. Either wait a while or choose a different mirror.

---

### Post by louis.roux on 2011-03-16
What is a mirror and how do I choose another mirror?

---

### Post by Frogs Hair on 2011-03-16
The mirror is the location your download is coming from. To change it try Update manager settings > Ubuntu software tab and under download location choose other and a dialog box will open . Select use best server and Ubuntu will run tests to  locate the best server  . If you already have the best server try again later.

---

### Post by louis.roux on 2011-03-17
now I know I have a problem because when I run the test it says no suitable mirror found and tells me to check my internet connection.  But my internet connection is just fine.

---

### Post by plucky on 2011-03-17
> **louis.roux said:**
> now I know I have a problem because when I run the test it says no suitable mirror found and tells me to check my internet connection.  But my internet connection is just fine.

Please post your sources.list

from a terminal ```
cat /etc/apt/sources.list
``` and ```
ls -l /etc/apt/sources.list.d/
``` and post to the forum

---

### Post by louis.roux on 2011-03-17
> **plucky said:**
> Please post your sources.list

from a terminal ```
cat /etc/apt/sources.list
``` and ```
ls -l /etc/apt/sources.list.d/
``` and post to the forum

```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://ppa.launchpad.net/claydoh/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/claydoh/ppa/ubuntu lucid main # disabled on upgrade to lucid
# deb http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu jaunty main # disabled on upgrade to lucid
# deb-src http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu jaunty main # disabled on upgrade to lucid

deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository

```

```
owner@ubuntu:~$ ls -l /etc/apt/sources.list.d/
total 24
-rw-r--r-- 1 root root  98 2011-03-05 17:09 gwibber-daily-ppa-karmic.list
-rw-r--r-- 1 root root  98 2011-03-05 17:09 gwibber-daily-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  66 2010-02-15 09:47 gwibber-daily-ppa-karmic.list.save
-rw-r--r-- 1 root root 176 2011-03-05 17:09 karmic-partner.list
-rw-r--r-- 1 root root 173 2011-03-05 17:09 karmic-partner.list.distUpgrade
-rw-r--r-- 1 root root  81 2010-02-15 09:47 karmic-partner.list.save
owner@ubuntu:~$ 

```

---

### Post by plucky on 2011-03-17
You need to disable the Cdrom as a source ```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
``` in sources.list and un-tick all the non-maverick sources in **Software Sources**.

It might even be worth deleting them.

Then run ```
sudo apt-get update
``` and post the result.

Good Luck

---

### Post by louis.roux on 2011-03-17
> **plucky said:**
> You need to disable the Cdrom as a source ```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
``` in sources.list and un-tick all the non-maverick sources in **Software Sources**.

It might even be worth deleting them.

Then run ```
sudo apt-get update
``` and post the result.

Good Luck

Still getting the following in terminal 

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
owner@ubuntu:~$ 
```

and the following when I try to install through the update manager
Failed to lock the package manager

C```
heck if you are currently running another software management tool, e.g. Synaptic or aptitude. Only one tool is allowed to make changes at a time.

The package indexes are currently changed by apt-get.

```

---

### Post by kagerato on 2011-03-18
There's a discretionary lock on some of apt's key files.  That means that more than one program is trying to access those files simultaneously.  The second (third, etc.) programs will not proceed as long as they're designed to obey the discretionary lock, because doing so could cause substantial data corruption.

Essentially, you just need to close whatever application is holding the lock.  It might be the software center, or the background updater, or Synaptic, or another apt-get process in a terminal somewhere.  Check around.

---

### Post by Dutch70 on 2011-03-18
You can check in system monitor. I'm not sure exactly what to tell you to look for though.

---

### Post by plucky on 2011-03-18
If you cannot find anything in system-monitor,try deleting the lock file.
Use ```
cd /var/lib/apt/lists/
sudo rm lock
```

Then run the "sudo apt-get update" command and it will be re-created.

Good Luck

---

### Post by louis.roux on 2011-03-19
Plucky that was the answer.  thank you

---

