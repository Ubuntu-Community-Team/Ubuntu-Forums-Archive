---
title: "libmysql-java not found"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by danizmax on 2007-01-12
Hello i'm new to ubuntu/debian but not to linux! I have a problem installing JDBC driver, I followed [this]("https://help.ubuntu.com/community/JDBCAndMySQL") howto and aptitude cannot find ** libmysql-java** package. What repositories do I have to make enabled to install this package? 

Thanks for help

---

### Post by bapoumba on 2007-01-12
Hello,
```
~ $ aptitude show  libmysql-java 
Package: libmysql-java
State: not installed
Version: 3.1.11-1
Priority: optional
Section: **multiverse**/libs
```

Multiverse repository ;)

---

### Post by danizmax on 2007-01-13
I have all repositories enabled but apt still can't find it! I have ubuntu server 6.10.

> root@danizmax-srv:~# aptitude show  libmysql-java
No candidate version found for libmysql-java
Package: libmysql-java
State: not a real package

 any idea?

---

### Post by danizmax on 2007-01-14
I really need that package! Do I need to add any non-standard repositories?

---

### Post by bapoumba on 2007-01-14
Sorry I did not answered yesterday, but I'm not sure what to recommend to you :/
[http://packages.ubuntu.com/edgy/libs/libmysql-java]("http://packages.ubuntu.com/edgy/libs/libmysql-java")

Could you post the output to **cat /etc/apt/sources.list** ?

---

### Post by danizmax on 2007-01-15
NP here it is:

> 
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
 deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

O and what fore are **deb-src** sources? I assume that are for program sources and development.

---

### Post by bapoumba on 2007-01-15
Hello,
You have no enable multiverse repositories :
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

