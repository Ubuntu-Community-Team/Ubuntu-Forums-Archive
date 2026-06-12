---
title: "error... cannot find package"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by corn29 on 2006-10-30
Hello,

I did some searching in this forum and I've tried everything in the HOWTO and in the discussions and I still have this issue.  I'm using 6.06.

When I issue this command:

corn29@laptop1:~$ sudo apt-get install fakeroot java-package java-common

I get these results:

Reading package lists... Done
Building dependency tree... Done
fakeroot is already the newest version.
E: Couldn't find package java-package
corn29@laptop1:~$

Another thread said the error is because of not enabling multiverse in my sources list... corn29@laptop1:/etc/apt$ more sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

As you can see, the two multiverse lines above are uncommented... 

What else am I missing?

Thanks for your time!

---

### Post by skierkegaard on 2006-10-30
Did you sudo aptitude update?

---

### Post by polt on 2006-10-30
try uncommenting the two lines at the end of the following:

> **corn29 said:**
> 
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe


then do 
> sudo apt-get update
and try again.

---

### Post by ciscosurfer on 2006-10-30
Use [Automatix]("http://getautomatix.com") and it will do it for you.

---

### Post by corn29 on 2006-10-30
Thanks... sudo apt-get update worked after I uncommented the two other lines you suggested in the sources.list!  I appreciate your help!

---

