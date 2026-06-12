---
title: "Repositories not showing all packages"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by finite9 on 2006-07-13
Hi!

I have main, restricted, universe and multiverse enabled (6.06 LTS amd64), but certain packages do not show up after refreshing the repositories with apt-get or Synaptic!  Eg dvdrip and vmware-player do not exist!  But if I go to [http://archive.ubuntu.org](http://archive.ubuntu.org) and browse the pool folder structure, then they exist there and I can download the .deb and install it.

What gives?

---

### Post by philippe_carlo on 2006-07-13
Are you sure that hese packages exist for 64-bit?

---

### Post by finite9 on 2006-07-13
Yes im sure:

[http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player/](http://archive.ubuntu.com/ubuntu/pool/multiverse/v/vmware-player/)

here is an amd64 deb.  Tried to find dvdrip on the same link but cannot find it for either i386 or amd64.

---

### Post by aysiu on 2006-07-13
Can you post your /etc/apt/sources.list?

---

### Post by finite9 on 2006-07-14
my sources...


deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by aysiu on 2006-07-14
I see the multiverse for the backports, but not the general multiverse.

Try this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then see if DVDRip and VMPlayer show up.

---

### Post by finite9 on 2006-08-09
I got this working, but I had to manually edit sources.list - it didn't work to edit a current entry in Synaptic and add multiverse checkbox, so I added the following:

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper multiverse

and now everything works.  This line is not in sources.list as standard and when you do things through Synaptic it adds something like this:

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

but this doesnt enable multiverse repository.

--finite9

---

