---
title: "gcc installation cannot find -lc error"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by ravish112 on 2011-08-08
Hi All,
 
I am trying to install gcc v4.3.3 from the source on ubuntu 11.04. I get the following error
and it got exit from the installation.
Error:-
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make[3]: *** [libgcc_s.so] Error 1
I try to googled for this particular error, but I could not find any solution. Could you please
help me in this scenario.
 
Thanks..

---

### Post by realzippy on 2011-08-08
Why compiling and not using software center ?

Anyway,before compiling run
```
sudo apt-get build-dep gcc
```
which installs all dependencies for compiling gcc.
Then try again....btw,welcome to UF!

---

### Post by ravish112 on 2011-08-08
Thanks for the reply, I try to follow your instructions
 
 Here is the result:-
 
[EMAIL="root@rr423:~/packages"]root@rr423:~/packages[/EMAIL]# apt-get build-dep gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list
[EMAIL="root@rr423:~/packages"]root@rr423:~/packages[/EMAIL]# 
 
Could you please check and let us know..
 
Thanks.

---

### Post by realzippy on 2011-08-08
Maybe you have not enabled universe repository.
Check your software sources.
Why on root terminal?

---

### Post by ravish112 on 2011-08-08
I uncomment the couple lines like  #deb-src [http://arm-archive-ubuntu](http://arm-archive-ubuntu) in /etc/apt/sources.list
 
Still same error E: You must put some 'source' URIs in your sources.list
 
Let me explain my requirement clearly:-
 
1) gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3 has been installed in /usr/bin/gcc path.
2) I am trying to install one more gcc 4.3.3 into other customised path (/xyz/) in the same machine.
 
while building gcc 4.3.3 I got the above error i.e., 
 
/usr/bin/ld: cannot find -lc
collect2: ld returned 1 exit status
make[3]: *** [libgcc_s.so] Error 1

I spent more that two days to figure out this issue by doing googling. Please let me the proper solution or which library it is looking for?
 
Thanks,

---

### Post by realzippy on 2011-08-08
> **ravish112 said:**
> I uncomment the couple lines like  #deb-src [http://arm-archive-ubuntu](http://arm-archive-ubuntu) in /etc/apt/sources.list
 
Still same error E: You must put some 'source' URIs in your sources.list
 


Have you updated the sources after modifying?

```
sudo apt-get update
```

---

### Post by ravish112 on 2011-08-08
sourcelist got updated and this is result what I got:-
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking 'gcc-defaults' as source package instead of 'gcc'
The following packages have unmet dependencies:
 debhelper : Depends: dpkg-dev (>= 1.14.19) but it is not going to be installed
 gcj-jdk : Depends: gcj-4.4-jdk (>= 4.4.3-1) but it is not going to be installed
E: Build-dependencies for gcc could not be satisfied

---

### Post by realzippy on 2011-08-08
Guess your sources are still incorrect.
No problem here to install debhelper,dpkg-dev,aso.
Best thing is I give you my current sources list:

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://de.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
```

...don't forget updating apt-get...

---

### Post by ravish112 on 2011-08-11
Hi,
 
Thanks for your source link repositories. 
 
Now I started to install gcc 4.3.3 on ubuntu 11.04 while building I got this error:-
 
/tlink.c:41: error: 'MAXPATHLEN' undeclared here (not in a function)
make[3]: *** [tlink.o] Error 1

I tried to googled around for above issue, no luck. Could you please help me in this.
 
Thanks

---

### Post by realzippy on 2011-08-11
Sorry,I cannot.This is far behind my knowledge.
Make a new thread in programming talk,with this error as title.

---

### Post by ravish112 on 2011-08-12
Hi,
 
I googled around and got some patches, which solves my issue. 
 
[http://gcc.gnu.org/bugzilla/attachment.cgi?id=16643&action=diff](http://gcc.gnu.org/bugzilla/attachment.cgi?id=16643&action=diff)

---

### Post by realzippy on 2011-08-12
Good.
So you can set thread as solved (threadtools)
Have fun!

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

