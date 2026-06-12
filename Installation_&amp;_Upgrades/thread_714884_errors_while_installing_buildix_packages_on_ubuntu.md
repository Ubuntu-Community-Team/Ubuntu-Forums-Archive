---
title: "errors while installing buildix packages on ubuntu 7.0.4"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by robinsingh on 2008-03-04
Hi there, 
Please excuse me if I am posting in the wrong forum, I couldn't find a better fit than this forum for this question. I am trying to install a package called  [BUILDIX]("http://buildix.thoughtworks.com/") by adding appropriate repository in my /etc/apt/soruces.list 
This buildix package (*by Thoughtworks) is basically a combination of - Subversion (source versioning), CruiseControl (continuous integration), Trac (bug management system).
I posted my issue at their support forum but didn't get a response. Mainly I am getting this error while running the installation. 

```
user@user-vm-linux:~$ sudo aptitude install buildix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
buildix cruisecontrol mingle
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.8MB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
buildix: Depends: trac (>= 0.9.6-2) which is a virtual package.
Depends: apache2 (>= 2.0.55-4) which is a virtual package.
Depends: libapache2-mod-jk which is a virtual package.
Depends: libapache2-svn which is a virtual package.
Depends: libapache2-mod-fastcgi which is a virtual package.
Depends: python-cheetah which is a virtual package.
Depends: python-flup which is a virtual package.
Depends: ant-optional which is a virtual package.
cruisecontrol: Depends: sun-java5-jdk which is a virtual package.
Depends: subversion which is a virtual package.
mingle: Depends: sun-java5-jdk which is a virtual package.
Depends: postgresql-8.2 which is a virtual package.
Resolving dependencies...
Unable to resolve dependencies! Giving up...
Abort

```

Here's the link to the forum thread: 
[http://buildix.thoughtworks.com/forums/viewtopic.php?t=155]("http://buildix.thoughtworks.com/forums/viewtopic.php?t=155")
I would appreciate if someone can take a look at it and point out what exactly am I doing wrong. 
Here are the complete installation instructions that I followed to install this package 
[http://buildix.thoughtworks.com/index.php/documentation/package-installation/]("http://buildix.thoughtworks.com/index.php/documentation/package-installation/")


I am looking for general help to understand the reason for these errors, so that I can notify the product owners if it is an issue on their side or on their repository. 

Thanks for your help in advance,
robin

---

### Post by zvacet on 2008-03-04
You can go to the **synaptic>edit tab>fix broken packages**,and if that doesn´t work install all dependencies with synaptic.Good luck!

---

