---
title: "Update post re-install (with disappearing HDD problems in 3 PC's)"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2012-06-26
I'm having serious problems with hard drives disappearing from BIOS' in 3 computers - I wonder if I have a BIOS virus here.

BUT

a related, different problem is at hand. I just re-installed on one of the machines, and started the initial update.

I got a warning about unauthenticated software. I've never seen this on the initial update after an install.

Isn't the DEFAULT repo list safe? What repos should it include (by default)???

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220328&d=1340766953[/IMG]

---

### Post by josephmills on 2012-06-26
I would not install anything that I did not know where it was coming from. I think that you made the right choice by asking.
could you please open your terminal 
ctrl+alt+t 
then paste the output of these commands here. We are going to look at where you are getting your software.
```
ls /etc/apt/sources.list.d/
```
then 
```
cat /etc/apt/sources.list
```
Thanks

---

### Post by Moozillaaa on 2012-06-27
Don't know what happened on the **list repo command** there Joe, so we did it the old fashioned way:

> dell-124@dell-124-laptop:~$ **[COLOR=Red]exec sudo -s[/COLOR]**
[sudo] password for dell-124: 
root@dell-124-laptop:~# ls /etc/apt/sources.list.d/
root@dell-124-laptop:~# ls /etc/apt/sources.list.d/
root@dell-124-laptop:~# sources.list.d [folder] is emty


Again, this is a fresh install DEFAULT repo values are in place...
> 
dell-124@dell-124-laptop:~$ ping google.com
ping: unknown host google.com
dell-124@dell-124-laptop:~$ ping 192.168.0.1
connect: Network is unreachable
dell-124@dell-124-laptop:~$ ping yahoo.com 
PING yahoo.com (209.191.122.70) 56(84) bytes of data.
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=1 ttl=50 time=111 ms
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=2 ttl=50 time=108 ms
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=3 ttl=51 time=106 ms
^C
--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 106.621/108.667/111.294/1.969 ms
dell-124@dell-124-laptop:~$ **[COLOR=Red]exec sudo -s[/COLOR]**
[sudo] password for dell-124: 
root@dell-124-laptop:~# ls /etc/apt/sources.list.d/
root@dell-124-laptop:~# ls /etc/apt/sources.list.d/
root@dell-124-laptop:~# cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

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
root@dell-124-laptop:~# [IMG]http://ubuntuforums.org/attachment.php?attachmentid=220328&d=1340766953[/IMG]

---

### Post by josephmills on 2012-06-27
close the update manager and run a update on its own. 
```
sudo apt-get update
```
paste the out put here also that list of packages 200 and some can you also paste that here.

---

