---
title: "smlnj Problem"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by pmghalvo on 2007-05-05
I did run a search and found the topic already created for this problem and I've used it plus searched the web and still can't figure out why I'm having a problem.

when I ```
cat /etc/apt/sources.list
 ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

## Extra
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free 
```

then ```
 sudo apt-get install smlnj
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smlnj 
```

The other thread said to make sure you have the extra repos active, which I thought I did (first code)
I would really like to be able to program in smlnj.

Please help, I'm completely new to Ubuntu and Linux

---

### Post by bapoumba on 2007-05-05
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=smlnj&searchon=names&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=smlnj&searchon=names&subword=1&version=all&release=all")
The package is in the universe repositories.

Did you run```
sudo aptitude update
```
before you tried to install it ?

```
~$ aptitude show smlnj
Package: smlnj
State: not installed
Version: 110.54-0ubuntu1
Priority: optional
Section: universe/devel
Maintainer: Aaron Matthew Read <amread@nyx.net>
Uncompressed Size: 23.7M
Depends: smlnj-runtime (>= 110.54)

```
I can see it.

---

### Post by pmghalvo on 2007-05-05
Yes I did that.

I still can't see it ```
aptitude show smlnj
E: Unable to locate package smlnj
```

When I went to the link you gave me, I clicked the smlnj package for Edgy (I think I have 6.10 Edgy Eft, thats what it says under System - About Ubuntu). Then click to download. I then get an error message

"Error: Wrong Architecture 'i386'"

I get the same error for powerpc.
I'm so confused, is there something els wrong?

---

### Post by bapoumba on 2007-05-06
Hum, I had another look at your sources.list, and it appears you have both dapper and edgy repos. Please fix that first.
```
lsb-release -cd
```
will let you know which ubuntu release you are actually running.

---

### Post by pokerFace12344321 on 2008-04-26
I am having the same problem:

```

.[~]
$ sudo apt-get install smlnj
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smlnj

.[~]
$ aptitude show smlnj
E: Unable to locate package smlnj

```


Before doing this, I ran:

```

sudo aptitude update

```
(everything was up to date.)


This is the version I'm running:

```

.[~]
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

```

Also, I am running the AMD64 version of Ubuntu since I have a quad-core chip.

This is what I have for sources:

```

.[~]
$ cat /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse


## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main universe restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main universe

## Canonical Partner Repository

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security main
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free

```



> 
[http://packages.ubuntu.com/cgi-bin/s...ll&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=smlnj&searchon=names&subword=1&version=all&release=all")

The package is in the universe repositories.


I tried going there, but the page took forever to download.

Any help would be much appreciated:popcorn:!

Thanks.

---

