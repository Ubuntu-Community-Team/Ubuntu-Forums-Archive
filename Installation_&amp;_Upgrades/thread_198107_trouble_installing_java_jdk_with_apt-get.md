---
title: "trouble installing java jdk with apt-get"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by WillieBHines on 2006-06-16
Trying to install sun's java jdk via the command line on a ubuntu server. I type this:
sudo apt-get install sun-java5-jdk

and get this...
Reading pacakage lists... Done
Building dependence tree... Done
E: Couldn't find pacakage sun-java5-jdk

Is it trying to find the files on my CD-ROM?

Here's my sources.list file:

# 
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

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
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by givré on 2006-06-16
These programm is in multiverse, add this repo via synaptic, or just add 
multiverse after the the universe in the source.lst
Should look like that:
```
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

---

### Post by givré on 2006-06-16
Also uncomment your security line, it's quite important

---

### Post by givré on 2006-06-16
A wiki page explaining how to add repository 
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) ;)

---

### Post by WillieBHines on 2006-06-19
Excellent! I not-intelligently thought that the dapper-backports line which ended in multiverse was enough. I also uncommented the security lines.

I had seen that page in the wiki, but it describes how to do it via the GUI. I've installed the server software which does not have the GUI.

Thank you so much! Worked great.

---

