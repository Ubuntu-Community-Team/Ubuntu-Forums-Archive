---
title: "Cannot install any new package"
date: 2013-07-20
forum: Installation &amp; Upgrades
---

### Post by Big Dazed and Confused on 2013-07-20
Hi , 

Every package I am trying to install I get the following error: 
E: Unable to correct problems, you have held broken packages.



```
Dazed@Box:~$ sudo apt-get install openjdk-7-jreReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 openjdk-7-jre : Depends: openjdk-7-jre-headless (= 7u25-2.3.10-1ubuntu0.13.04.2)
                 Depends: libgif4 (>= 4.1.4) but it is not installable
                 Depends: libatk-wrapper-java-jni (>= 0.30.4-0ubuntu2) but it is not installable
                 Recommends: libgnome2-0 but it is not installable
                 Recommends: libgnomevfs2-0 but it is not installable
                 Recommends: libgconf2-4 but it is not installable
                 Recommends: ttf-dejavu-extra but it is not installable
E: Unable to correct problems, you have held broken packages.



```


I have tried many google solutions ,nothing helped so far : 
sudo apt-get autoremove && sudo apt-get autoclean
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade 
sudo dpkg --configure -a
sudo apt-get clean 



Thanks for your help

---

### Post by GwL3eNC on 2013-07-30
Hi!

You have wrote sudo apt-get install -f but it should be

sudo apt-get -f install.

is it just a typing error?

---

### Post by Bhawani007 on 2013-07-30
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

Try this, it helped me. It will solve you problem too

---

### Post by ian-weisser on 2013-07-30
This problem happens for a couple possible reasons. Here are three of the most common:

1) You added a PPA which requires specific dependencies, which conflict with the new package dependencies.
To see what PPAs you have added, look in /etc/apt/sources.list.d/ .
If this is the problem, you must remove the conflicting PPA.

2) You added a package intended for a different release of Ubuntu.
This is more rare, but does happen when people download .debs off the internet instead of using the package manager.
If this is the problem, uninstall the package.

3) You did a "partial-upgrade" of Ubuntu.
Bad. That indicates a serious problem that may take some effort to resolve.
If this is the problem, backup your data. If you cannot determine the problem, you may wind up reinstalling.

How long has the problem been going on?
Did you install anything before it started happening?
What version of Ubuntu are you running? What release?

---

### Post by Big Dazed and Confused on 2013-08-12
Tried it as well , did not help .

---

### Post by Big Dazed and Confused on 2013-08-12
bouncing

---

### Post by Big Dazed and Confused on 2013-08-12
I have removed all PPA files . 
$ ls -ltr /etc/apt/sources.list.d/
total 0

All packages that downloaded by apt-get or Ubuntu software manager . 

This issue is several weeks already  I am not sure about partial upgrade is the issue. 

$ cat /etc/issue
Ubuntu 13.04 \n \l

---

### Post by ian-weisser on 2013-08-12
If it were me troubleshooting, I would:
1) Double check /etc/apt/sources.list (the file, you already checked the directory)

2) Post the results of "sudo dpkg --audit"

---

### Post by Big Dazed and Confused on 2013-08-20
Hi , 
Sorry for late response , Thanks for you help .
```

$ cat  /etc/apt/sources.list |grep -v "#"


deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted


deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted


deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe


deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse


deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse


deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner


deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main

$ sudo dpkg --audit
$ 




```


Any idea?

---

