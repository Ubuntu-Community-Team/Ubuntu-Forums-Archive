---
title: "Update Ubuntu 10.10 asks for 6.06 CD?"
date: 2011-02-08
forum: Installation &amp; Upgrades
---

### Post by pe7er on 2011-02-08
Using Ubuntu 10.10 & updating via:
System > Administration > Update Manager, or ```
sudo apt-get update
``` both result in ```

Media change: please insert the disc labeled                                                                                                                 
 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)'
in the drive '/cdrom/' and press enter
```
I have not installed 6.06 on my PC, but originally installed 9.10 / or 10.04 which I upgraded to 10.10.
I tried setting another repository & re-update, but the same error appears.

Why do I get that message? And how can I solve it?
Thanks!

---

### Post by ikt on 2011-02-08
Are you able to check your sources.list hasn't been mixed up?

How very odd o.O

---

### Post by pe7er on 2011-02-08
Thanks for your answer!

The first few lines of my /etc/apt/sources.list say:
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted
```

Can I change or remove the line with the 6.06 reference?
And what can I put there?

**edit:** in another post I saw the reference ```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
```
I have replaced the 6.06 reference with that...
But I got another error: ```
W: Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
```
So I've just #commented the "deb cdrom" line, and now it works okay again.

Thanks for your help regarding sources.list!

---

### Post by ikt on 2011-02-08
> **pe7er said:**
> Thanks for your answer!

The first few lines of my /etc/apt/sources.list say:
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted
```

Can I change or remove the line with the 6.06 reference?
And what can I put there?

Yep you will want to remove the 6.06 lines, they shouldn't be there.

The sources.list file is basically a file full of places where ubuntu can get its updates from, I personally get rid of the cdrom references because I don't have the cd rom in my drive, I use just the internet for updates.

There is a great wiki article on the whole thing here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

have fun :)

for reference this is what mine looks like:

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security main restricted
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ maverick-security multiverse
```

---

### Post by pe7er on 2011-02-08
> **ikt said:**
> Yep you will want to remove the 6.06 lines, they shouldn't be there.

The sources.list file is basically a file full of places where ubuntu can get its updates from, I personally get rid of the cdrom references because I don't have the cd rom in my drive, I use just the internet for updates.

There is a great wiki article on the whole thing here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

have fun :)
Marvelous! The error is gone...
Thanks for your help!

---

### Post by ikt on 2011-02-08
> **pe7er said:**
> Marvelous! The error is gone...
Thanks for your help!

All good :D

---

### Post by amal55 on 2011-04-26
i have the same problem but I'm new to Ubuntu can you pleas explain more
what should i do and if i have to change the source could where can i fund it ?
help please :(

---

### Post by pe7er on 2011-04-27
> **amal55 said:**
> i have the same problem but I'm new to Ubuntu can you pleas explain more
what should i do and if i have to change the source could where can i fund it ?
help please :(

I changed it in /etc/apt/sources.list via ```
sudo nano /etc/apt/sources.list
```
The 4th line in my file stated:
```
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/ dapper main restricted
```Instead of removing, I just disabled that line by commenting it (putting "#" in front of it).

---

