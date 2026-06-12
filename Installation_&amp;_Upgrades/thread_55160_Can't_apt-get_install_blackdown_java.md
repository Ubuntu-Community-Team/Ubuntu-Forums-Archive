---
title: "Can't apt-get install blackdown java"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by greyhound4334 on 2005-08-07
Hi,

New to Ubuntu, but have used debian for the last year or so.  I like what I've seen so far, but am just venturing outside of hoary main/restricted to get stuff I need, like java to run jedit.

At the bottom is my sources.list file.  I have no preferences file as of yet.  When I run 

```
root@delbert:~ # apt-get install j2re1.4 j2sdk1.4
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  j2re1.4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  j2sdk1.4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

```

The problem is that the required libc6 doesn't appear to be anywhere in main/universe/multiverse: 

```
root@delbert:~ # apt-cache policy libc6
libc6:
  Installed: 2.3.2.ds1-20ubuntu13
  Candidate: 2.3.2.ds1-20ubuntu13
  Version table:
 *** 2.3.2.ds1-20ubuntu13 0
        500 cdrom://Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407) hoary/main Packages
        500 http://us.archive.ubuntu.com hoary/main Packages
        100 /var/lib/dpkg/status

```

Here's my sources.list
```
root@delbert:~ # cat /etc/apt/sources.list
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Blackdown Java
deb ftp://ftp.tux.org/pub/java/debian sarge non-free
```

I've had alot of problems running a debian system that mixed stable, testing, and unstable before, and the whole ubuntu package philosophy appeals to me for just that reason.  In general, I hope to stick to main and restricted as much as possible, but I have to have java and some java apps, so I'm kind of stuck.  I'm not sure, but I think libc6 is a pretty critical library, so going outside multiverse for it doesn't seem advisable.

Any advice welcome and appreciated!

Cheers,
john

---

### Post by greyhound4334 on 2005-08-07
***********

I've resolved this specific problem by installing sun-j2re1.5 instead of blackdown java.

I've opened a new thread with the same core issue -- where to get the right version of libc6 -- on the other application forum.  I've run into the same problem (with libc6) trying to install php5

************

---

