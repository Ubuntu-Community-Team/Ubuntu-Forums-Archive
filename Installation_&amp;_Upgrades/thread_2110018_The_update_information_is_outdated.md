---
title: "The update information is outdated"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by barezi6 on 2013-01-29
Hi everyone.

I cant install the updates to my computer.
It gives me a error saying "the update information is outdated...", i saw that many people have the same problem but i cant fix it in my computer, i changed the updates server to the main server, but its still not working, i only can get the updates by command line.

Can anyone give me some help with this problem?

where is my souce list

```
# deb cdrom:[Xubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.1)]/ quantal main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu quantal main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu quantal-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal universe
deb-src http://archive.ubuntu.com/ubuntu quantal universe
deb http://archive.ubuntu.com/ubuntu quantal-updates universe
deb-src http://archive.ubuntu.com/ubuntu quantal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu quantal multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal multiverse
deb http://archive.ubuntu.com/ubuntu quantal-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb-src http://archive.ubuntu.com/ubuntu quantal-security main restricted
deb http://archive.ubuntu.com/ubuntu quantal-security universe
deb-src http://archive.ubuntu.com/ubuntu quantal-security universe
deb http://archive.ubuntu.com/ubuntu quantal-security multiverse
deb-src http://archive.ubuntu.com/ubuntu quantal-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu quantal partner
# deb-src http://archive.canonical.com/ubuntu quantal partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu quantal main
deb-src http://extras.ubuntu.com/ubuntu quantal main
```

Thanks

---

### Post by ibjsb4 on 2013-01-29
Are you set for daily updates?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

---

### Post by barezi6 on 2013-01-29
> **ibjsb4 said:**
> Are you set for daily updates?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

Yes I am

---

### Post by ibjsb4 on 2013-01-29
Actually I posted in the wrong thread :)  woops

What happens if you do a ..

```
sudo apt-get update
```

---

### Post by barezi6 on 2013-01-29
> **ibjsb4 said:**
> Actually I posted in the wrong thread :)  woops

What happens if you do a ..

```
sudo apt-get update
```

Give me some errors but update some data, and the red icon disappear but some time later the icon back again.

---

### Post by plucky on 2013-01-29
> **barezi6 said:**
> Give me some errors but update some data, and the red icon disappear but some time later the icon back again.

Please post the full output of the command so we can attempt to give you a solution.

Good Luck

---

### Post by barezi6 on 2013-01-29
> **plucky said:**
> Please post the full output of the command so we can attempt to give you a solution.

Good Luck

Well, i write sudo apt-get update in command line, and they install a lot of things and in the final give me that:

Obtained 907 kB in 14s (60.7 kB / s)
W: Failed to fetch [http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/quantal/main/source/Sources) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/quantal/main/binary-i386/Packages) 404 Not Found

E: Failed to download some index files. Were ignored or older were used instead.

---

### Post by ibjsb4 on 2013-01-29
There is no quantal 12.10 release for that ppa, remove it.

[http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/)

---

### Post by barezi6 on 2013-01-29
> **ibjsb4 said:**
> There is no quantal 12.10 release for that ppa, remove it.

[http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/)

Should i remove this?
[http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu)

i have 2 lines with this URL, remove both?

Thanks for the help, it is really great for me :)

---

### Post by ibjsb4 on 2013-01-29
Yes, remove both.

---

### Post by barezi6 on 2013-01-29
> **ibjsb4 said:**
> Yes, remove both.

I think it resolve my problem, thanks so much for the users that helps me :)

---

### Post by barezi6 on 2013-01-29
> **ibjsb4 said:**
> Yes, remove both.

I think it resolve my problem, thanks so much for the users that helps me :)

---

### Post by ibjsb4 on 2013-01-30
One last thing :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

