---
title: "Installing java 1.6/6.0 on Jaunty"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by robinc on 2010-02-26
Hi Guys, I'm having some trouble installing JRE 1.6/6.0 on a Jaunty server, any help would be very much appreciated, as I'm going round in circles on Google.

if I try this

**apt-get install sun-java6-jdk**

I get


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate


if I try

**apt-get install sun-java6-jre**

I get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate


Here is my sources file.

```
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
 deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
 deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse



deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
 deb http://security.ubuntu.com/ubuntu jaunty-security universe
 deb-src http://security.ubuntu.com/ubuntu jaunty-security universe

deb http://apt-mirror.sourceforge.net/ apt-mirror/
```


Any ideas

---

### Post by mick222 on 2010-02-26
I had the same problem this fixed it. [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by robinc on 2010-03-01
> **mick222 said:**
> I had the same problem this fixed it. [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I love you

---

