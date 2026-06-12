---
title: "Broken Dependencies Fix"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by starkriverfell on 2008-03-07
I dont know if this will help, but here is what I did when the installation of BUDDI cash failed.  I am completely new to Linux and Ubuntu, so there could be too much info below, but it worked.


Broken Dependencies / Logging in as Root
mabernier@mabernier-ubuntu:~$ su

Password: 

root@mabernier-ubuntu:/home/mabernier# apt-get update

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US

Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]

Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US

Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release              

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages

Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources

Fetched 3B in 1s (3B/s)  

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[/B]
root@mabernier-ubuntu:/home/mabernier# dpkg --configure -a

Setting up java-common (0.26ubuntu1) ...



dpkg: dependency problems prevent configuration of buddi:

 buddi depends on sun-java5-jre | sun-java6-jre; however:

  Package sun-java5-jre is not installed.

  Package sun-java6-jre is not installed.

dpkg: error processing buddi (--configure):

 dependency problems - leaving unconfigured

Setting up odbcinst1debian1 (2.2.11-16) ...



Setting up unixodbc (2.2.11-16) ...



Processing triggers for libc6 ...

ldconfig deferred processing now taking place

Errors were encountered while processing:

 buddi

root@mabernier-ubuntu:/home/mabernier# 


AFTER ATTEMPTING REINSTALL I still got the error message about broken dependencies however after running the apt-get update as root I was able to run the following.
root@mabernier-ubuntu:/home/mabernier# sudo synaptic

selected “broken dependices” marked “buddi”  (cannot remember next two steps but recall having to say twice to fix the broken dependency at that point the installing removing window popped up, j[/B[/B][/B]]

---

### Post by insineratehymn on 2008-03-07
Ok, it is saying that java isn't installed...
Try:
sudo apt-get install sun-java5-jre

Then try reinstalling it.

A quick way to build the dependencies of a package is to do:

sudo apt-get build-dep PACKAGE

So, to build all of the dependencies of wine incase you wanted to download some new binaries:

sudo apt-get build-dep wine

---

### Post by zvacet on 2008-03-08
```
sudo dpkg --configure -a
```

---

