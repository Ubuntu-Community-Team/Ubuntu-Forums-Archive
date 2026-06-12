---
title: "help"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by omlx2 on 2008-06-27
i was trying to install berly in my pc and when i did first update i got this
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

---

### Post by omlx2 on 2008-06-27
E: Type ‘“deb’ is not known on line 44 in source list /etc/apt/sources.list

---

### Post by wormser on 2008-06-27
Post the results of the following commands.

```
ls -la /etc/apt/sources.list
```
```
gedit /etc/apt/sources.list
```

---

### Post by omlx2 on 2008-06-27
-rw-r--r-- 1 root root 2512 2008-06-27 18:39 /etc/apt/sources.list

# newer versions of the distribution.

deb [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://tl.archive.ubuntu.com/ubuntu/](http://tl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

---

### Post by wormser on 2008-06-27
> **omlx2 said:**
> &#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221;
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

Delete those last two line.  

```
gksudo gedit /etc/apt/sources.list
```Then

```
sudo apt-get update
```Do you want to have Automatix?  It is not recommended to use it.

---

### Post by omlx2 on 2008-06-27
You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.



i try to save it!!!!but i got that

---

### Post by wormser on 2008-06-27
> **omlx2 said:**
> You do not have the necessary permissions to save the file. Please, check that you typed the location correctly and try again.

i try to save it!!!!but i got that

You have to use the command with gksudo to get permissions.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by omlx2 on 2008-06-27
its working nw...\
ii need to insall automatix if u may give the code


thanks dodu

---

### Post by wormser on 2008-06-27
> **omlx2 said:**
> its working nw...\
ii need to insall automatix if u may give the code
thanks dodu

It looks like the [Automatix project]("https://help.ubuntu.com/community/Automatix") is dead.

> **Note - the Automatix project has now been discontinued. It is not recommended for use.**Take their advice and don't use it.  Make sure you mark the thread Solved and click the star icon on the post that helped.  Next time use a descriptive title.  These things make the forum easier to use.

---

