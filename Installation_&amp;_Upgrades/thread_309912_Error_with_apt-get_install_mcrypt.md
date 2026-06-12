---
title: "Error with apt-get install mcrypt"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by DoctorEternal on 2006-11-30
I am trying to install mcrypt onto an Ubuntu 6.06 box. I installed it one this machine no problem by running 'apt-get install mcrypt', but the same command on my other 6.06 box results in:

root@whost:/# apt-get install mcrypt
Reading package lists... Done
Building dependency tree... Done
Package mcrypt is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mcrypt has no installation candidate

I have done an update for aptitude, still no luck.

](*,)

---

### Post by taurus on 2006-11-30
Did you enable both universe & multiverse in /etc/apt/sources.list?

---

### Post by frodon on 2006-11-30
Weird, anyway you can find the ubuntu dapper mcrypt .deb file there :
[https://bugs.launchpad.net/+builds/+build/162192/mcrypt](https://bugs.launchpad.net/+builds/+build/162192/mcrypt)

Hope it helped you

---

### Post by DoctorEternal on 2006-11-30
> **frodon said:**
> Weird, anyway you can find the ubuntu dapper mcrypt .deb file there :
[https://bugs.launchpad.net/+builds/+build/162192/mcrypt](https://bugs.launchpad.net/+builds/+build/162192/mcrypt)

Hope it helped you

Yes it did. :-D  Downloaded that, and it's dependencies. Now works fine. Thanks!

Dr.E

---

### Post by mechx on 2007-03-21
I did as advised above and installed mcrypt package. now my question is how to install it into apache and php?

[This doc]("http://pl.php.net/mcrypt") says I need to compile PHP with parameters. Is that required? How do you do that in Ubuntu?

My apache server is apache2 and i use PHP5.

any help would be nice

---

### Post by thePFY on 2007-08-14
I am now facing the same problem, is there any doc that would outline the steps required?

---

### Post by sitmex on 2008-04-08
Same problem here...

I also need to get the CURL (libcurl)

---

