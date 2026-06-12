---
title: "libpq5 issue - wouldn't upgrade, now won't install"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by dblagbro on 2010-01-22
so, using update manager i found that for the last week "libpq5" had a newer version available but wouldn't upgrade.  So, after several attempts and realizing that i couldn't use the 'reinstall' option i decided to remove it and try reinstall.  but that has now left me where I needed to remove it and a bunch of things that depended on it including open office.... and now i can't reinstall it and can't reinstall open office.

it looks like the libpq5 installer looks for something called libkbrf0 which won't install either...   so, where do i go from here?   not sure how to troubleshoot a dependancy issue like this as this is the first time i've run into such a problem...


thanks in advance!
-d

---

### Post by dblagbro on 2010-01-22
correction, trying to install 'libpq5' tries to install libkrb53 not libkrbf0...



error message:

libpq5:
 Depends: libkrb53 (>=1.6.dfsg.2) but it is not installable

---

### Post by mageus on 2010-01-22
Exact same issue.  Would also appreciate help with this.

---

### Post by dblagbro on 2010-01-23
BUMP - still happening... no other answers found yet.
-d

---

### Post by dblagbro on 2010-01-24
I don't know if this is related or not but now having issues with both network-manager and wicd (not at same time)...  neither will run so now i have to stay connected with cat5 because I can't get wireless working without either wicd or network-manager....

if you are having this issue, don't try removing (if you plan on trying to reinstall and use) either wicd or network-manager.

BUMP - still an issue.

tks
-d

---

### Post by drclue on 2010-01-27
libpq5 has been listed in my update manager for a while now under the "other software" section , and won't allow section of it's checkbox , but
after multiple update cycles is still sitting there.

I did post a thread about this , but have received no responses.

I really sorta hope it goes away or a solution shows up some time soon.

My Ubuntu 9.10 is working great otherwise.

---

### Post by morganwahl on 2010-02-05
are there any uncommented lines (i.e. ones that don't begin with #) in your /etc/apt/sources.list ? I had the same problem and found a jaunty-backports entry in there. Commenting it out solved the problem.

I'm guessing this may be a bug in the jaunty-karmic upgrade process? Anyway, it's easy to fix.

---

### Post by solitaryr on 2010-02-06
This worked for me (I actually had an intrepid backport line).  Commenting it out and updating my package list made this go away.

---

### Post by mageus on 2010-02-06
> **morganwahl said:**
> are there any uncommented lines ... in your /etc/apt/sources.list ? I ... found a jaunty-backports entry in there...

Yup, that was my problem.  Jaunty backports was enabled.  Thanx!

---

### Post by henrik_daver on 2010-02-14
Thanks a lot, this worked for me too.

---

### Post by Slyvr on 2010-03-09
Had this problem too and it finally bothered me enough to go looking for the solution.  I had the intrepid backport enabled as well.  Commented it out, updated the package lists, and the issue disappeared.

I'm with morganwahl that it was probably caused by my upgrade to karmic.  Weird that I've upgraded 6 system and this was the only one to have this issue.

---

### Post by JoL1 on 2010-03-23
I don't find the problem in my sources list.
Does anyone else see it?

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic main restricted
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates main restricted
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic universe
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic universe
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates universe
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic multiverse
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic multiverse
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates multiverse
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security main restricted
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security main restricted
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security universe
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security universe
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security multiverse
deb-src [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-security multiverse
# deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) karmic main # inaktiverad vid uppgradering till karmic
deb [http://ppa.launchpad.net/muravjov-il/ppa/ubuntu](http://ppa.launchpad.net/muravjov-il/ppa/ubuntu) karmic main
deb [http://ftp.port80.se/ubuntu/](http://ftp.port80.se/ubuntu/) karmic-backports restricted main multiverse universe

---

### Post by badpenguin on 2010-03-28
@ JoL1 - It's in the 6th section of your list.

This fixed it for me, too.  Thanks!

---

### Post by oldschoolDebian on 2010-04-20
Hello guys,

 **libpq** is a C library that enables user programs to communicate with the PostgreSQL database server.  The server can be on another machine and accessed through TCP/IP.  This version of libpq is compatible with servers from PostgreSQL 8.2 or later. 
 This package contains the run-time library, needed by packages using libpq. 
 PostgreSQL is an object-relational SQL database management system. 	  

This is connected to the kernel and many other programs in Ubuntu.  If you try to "install"  KDE desktop you will get a nightmare, as well as a wanted removal of over 700 packages.  All pointing to  Libpq5.

Lots of bug reports on  libpq5  i only grabbed one below.  


[https://bugs.launchpad.net/ubuntu/+source/postgresql-8.3/+bug/435050](https://bugs.launchpad.net/ubuntu/+source/postgresql-8.3/+bug/435050)

[SIZE=1]Not to mention all the backports on the sources list.[/SIZE]

Nice site guys  :popcorn:

---

### Post by imaligertamer on 2010-04-26
Sorry for reviving an older topic, but I have the same problem. I've commented the lines containing anything to do with jaunty, but the libpq5 update notification will not go away. Help?

---

### Post by imaligertamer on 2010-04-28
Bump --  This issue is really bugging me. Especially with the release of 10.04 so close. Help me please?

---

