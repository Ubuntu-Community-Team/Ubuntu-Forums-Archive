---
title: "Problem with Ubuntu 10.04 VPS Java"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Niksutin on 2011-04-28
Hi, I have problems with my Ubuntu 10.04 VPS.
I'm trying to install java to it, and when i type  
sudo apt-get install sun-java6-jre sun-java-jdk sun-java6-plugin sun-java6-fonts,
it just says 

virtual@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java-jdk sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
virtual@ubuntu:~$

I'm newbie with VPS's so could you tell me exactly what I need to type and what order? Thanks in advance (:

---

### Post by paulm23 on 2011-04-28
You'll need to enable the 'partner' repository. Use nano to edit sources.list, so...

nano /etc/apt/sources.list

Find the line that starts:
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
Delete the "#"

Ctrl+O (to save)
Ctrl+X (to exit)

sudo apt-get update

Then sudo your java install as before.

Paul.

---

### Post by Niksutin on 2011-04-28
All I see is 

# deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted

#deb cdrom:[Ubuntu-Server 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse

What to do?

---

### Post by Niksutin on 2011-04-28
I mean how i delete that line?

---

### Post by Niksutin on 2011-04-28
I did what u said and deleted "#" and when I saved it said
"[ Error writing /etc/apt/sources.list: Permission denied ]"
What to do?

---

### Post by paulm23 on 2011-04-28
Sorry that should of been
sudo nano /etc/apt/sources.list

Don't delete the line because that is what tells the system where to get the java files!

Paul.

---

### Post by Niksutin on 2011-04-28
But what I do then if I can't delete line?

---

### Post by paulm23 on 2011-04-28
Just delete the # at the start of the line and then save it Ctrl+O (to save) (press enter to confirm file name)
Ctrl+X (to exit)
Then sudo apt-get update

---

### Post by kiddieland on 2011-04-28
[COLOR=Silver]Hi, this sounds very noob-like but i really need your help. 

When the distributor license pops up and there is an ok at the bottom, how do you press it??? [/COLOR][COLOR=Silver]:confused:

[/COLOR]
found out, u press an arrow key

---

### Post by Niksutin on 2011-04-29
I got new problem, i'm setting up botclient to VPS and I need to change permission of "run-linux.sh", but when i try do "chmod +x run-linux.sh" it says "chmod: changing permissions of "run-linux.sh": Operation not permitted"

So what to do?

---

