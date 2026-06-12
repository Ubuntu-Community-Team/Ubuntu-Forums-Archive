---
title: "Package manager destroyed"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by Semn on 2016-08-22
I cannot restore the package manager, its destroyed. Please advise:

See snapshot:

[https://drive.google.com/file/d/0B5Ue-lgnhGeWTW0tTUh2dy1WMFE/view?usp=sharing](https://drive.google.com/file/d/0B5Ue-lgnhGeWTW0tTUh2dy1WMFE/view?usp=sharing)

In terminal it shows:

[sudo] password for sem: 
Hit:1 [http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu) xenial InRelease
Ign:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:3 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) xenial InRelease     
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Hit:5 [http://ppa.launchpad.net/smathot/cogscinl/ubuntu](http://ppa.launchpad.net/smathot/cogscinl/ubuntu) xenial InRelease  
Hit:6 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease
Reading package lists... Done                      
sem@sem-Latitude-E6430:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic
  linux-image-4.4.0-28-generic linux-image-extra-4.4.0-28-generic
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  openjdk-9-jre openjdk-9-jre-headless
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
sem@sem-Latitude-E6430:~$

---

### Post by howefield on 2016-08-22
Duplicate thread closed.

---

