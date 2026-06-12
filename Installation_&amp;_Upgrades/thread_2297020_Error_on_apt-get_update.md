---
title: "Error on apt-get update"
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by Mohan_Yadav on 2015-09-30
I am trying to run update and  i am getting this error : 

```


prince@Devil-Device:~$ sudo apt-get update
Ign http://archive.ubuntu.com trusty InRelease
Get:1 http://archive.ubuntu.com trusty Release.gpg [72 B]
Get:2 http://archive.ubuntu.com trusty Release [11.9 kB]
Get:3 http://archive.ubuntu.com trusty/main amd64 Packages [14 B]
Fetched 12.0 kB in 2s (5,297 B/s)
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'universe/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
prince@Devil-Device:~$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu trusty main universe restricted multiverse


```

---

### Post by Bashing-om on 2015-09-30
Mohan_Yadav; Ouch ??

If :
> 
prince@Devil-Device:~$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main universe restricted multiverse

is all that the fetch file contains ->
Makes me wonder what kind of install this is .

maybe consider regenerating a sources.list ?
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

as a somewhat standard sources.list is :
```

sysop@1404mini:~$ cat /etc/apt/sources.list
# deb http://ftp.utexas.edu/ubuntu/ raring main restricted

# deb http://ftp.utexas.edu/ubuntu/ raring-updates main restricted
#following line is a duplicate unknown why/where (24may2013) and commented out.
# deb http://security.ubuntu.com/ubuntu raring-security main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://ftp.utexas.edu/ubuntu/ trusty main restricted
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.utexas.edu/ubuntu/ trusty-updates main restricted
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ftp.utexas.edu/ubuntu/ trusty universe
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring universe
deb http://ftp.utexas.edu/ubuntu/ trusty-updates universe
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.utexas.edu/ubuntu/ trusty multiverse
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring multiverse
deb http://ftp.utexas.edu/ubuntu/ trusty-updates multiverse
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##backports disabled - Those do not receive security updates.25oct2014
#deb http://ftp.utexas.edu/ubuntu/ trusty-backports main restricted universe multiverse
#(bdq)deb-src http://ftp.utexas.edu/ubuntu/ raring-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
#(bdq)deb-src http://security.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
#uncommented 23may2012
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
#uncommented 23may2013
deb http://extras.ubuntu.com/ubuntu trusty main
# deb-src http://extras.ubuntu.com/ubuntu raring main
sysop@1404mini:~$ 

```
This is my work install, and I do not have a need here for any source code;
that lists serves my use case.

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

