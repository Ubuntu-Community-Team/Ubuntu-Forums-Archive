---
title: "Ubuntu 6.06 LTS updates problem?"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by JackAcid on 2007-12-08
Hello, all
I am getting regular updates and for the most part things work well. However when the package manager opens I get the following warning:

[COLOR="Red"]"Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely."[/COLOR]

I have tried both instructions and I still get this warning, both when I "Mark all updates" or "sudo apt-get dist-upgrade" and then the next time the auto updates happens as well.:confused:

This has gone on for a few  weeks now. It's starting to be an annoyance!
Has anyone else run into this problem, or is it just me? How do I "fix" it ?

I don't really want to mess with upgrading to gutsy at the moment, but if that is the solution I guess I will.

Thanks!

---

### Post by Pumalite on 2007-12-08
Post:
cat /etc/apt/sources.list

---

### Post by JackAcid on 2007-12-08
mike@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper multiverse universe main restricted


but what does it all mean;-) ? is there something commented out that shouldn't be?

---

### Post by Pumalite on 2007-12-08
Why don't you get a new sources.list from here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
Let's see what happens.
Backup yours first.
Your sources.list seem OK. but sparse at first glance.

---

### Post by JackAcid on 2007-12-13
Thanks Pumalite!
That appears to have fixed the problem.
Sorry to  keep you waiting on the solution, but sometimes life gets in the way of what I really want to be doing! That and I had to wait for another update cycle to verify  that it worked.

Thanks again!
Jack

---

