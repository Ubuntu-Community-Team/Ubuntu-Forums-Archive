---
title: "Cannot open Synaptic Project Manager"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by pireland on 2010-09-24
I was trying to install java on 10.04 in firefox. Now whenever I try to get new software, there is none to be found. I am getting the error message "E: Malformed line 54 in source list /etc/apt/sources.list (dist parse) E: the list source cannot be read". To top it all off, I still cannot get java to function. I am pretty new to this. Please help.

---

### Post by howefield on 2010-09-24
You need to edit your sources.list and fix the errant line.

Post the output of the terminal command

```
cat /etc/apt/sources.list
```

---

### Post by pireland on 2010-09-24
patti@patti-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

Many thanks

---

### Post by howefield on 2010-09-24
Use the terminal command

```
gksudo gedit /etc/apt/sources.list
```

and try changing the second last line (line 54) the one that reads 
```
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
```
and make it look like this..

```
deb http://archive.canonical.com/ubuntu lucid partner
```

Save the file and reload your sources, then try installing java again.

---

### Post by pireland on 2010-09-24
It looks as if it worked. Again thank you. Just one more question. 
How should I go about installing java. I would rather not screw it up again.

---

### Post by ajgreeny on 2010-09-24
It appears that you will now have duplicate lines at 54 and 55 in that file, so you can remove one of them or simply comment it out (add a # at the start of the line).

I am surprised you do not get a message telling you there is a duplicate, but perhaps the system is more forgiving now than it used to be.

For java, as you have the partner repos enabled you should be able to find sun-java6-jre etc etc using synaptic. Install the jre, jdk, plugin and so on as needed.  I think the sun version is better than the open source versions, but it is up to you to choose.

---

### Post by pireland on 2010-09-24
I have what looks to be all relevant programs installed, but firefox still does not seem to be recognizing them. I have this handy little application that allows me to view whether or not javascript, java, flash, etc. are enabled, and it will not let me enable java. Am I missing something here?

---

### Post by ajgreeny on 2010-09-25
> **pireland said:**
> I have what looks to be all relevant programs installed, but firefox still does not seem to be recognizing them. *I have this handy little application that allows me to view whether or not javascript, java, flash, etc. are enabled, and it will not let me enable java.* Am I missing something here?
What little application is that?  Most likely for windows, I expect, so would not be expected to work in linux.

I would go to a website to check whether or not those plugins are enabled, eg [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) for java plugin and [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) for flash plugin.

---

