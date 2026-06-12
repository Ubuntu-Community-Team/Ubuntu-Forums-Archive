---
title: "Error opening Synaptic"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by grebarton on 2008-01-24
I get the following error when opening synaptic:

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_multiverse_binary-i386_Packages)

Any idea how to correct this as its annoying more than seems to be a real problem?

---

### Post by PmDematagoda on 2008-01-24
Post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by grebarton on 2008-01-24
Here it is actuallly Linux Mint based on Ubuntu:

## -----------------------                                   
## LINUX MINT REPOSITORIES
## -----------------------

## +++ Daryna (Linux Mint 4.0) +++
deb [http://www.linuxmint.com/repository/](http://www.linuxmint.com/repository/) daryna main upstream import 
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna community
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna backport

## +++ Romeo (Linux Mint Unstable) +++
## deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo daryna

## +++ Source Repositories +++
## deb-src [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna main upstream import
## deb-src [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna community
## deb-src [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) daryna backport
## deb-src [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo daryna

## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Gutsy (Ubuntu 7.10) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse 

## +++ Backports & Proposed (Ubuntu Unstable) +++
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse  
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed main restricted universe multiverse  

## +++ Source Repositories +++
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse  

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical +++ 
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) gutsy partner 

## +++ Medibuntu +++
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt/](http://www.getautomatix.com/apt/) gutsy main 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse 
#AUTOMATIX REPOS END


deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/

---

### Post by zvacet on 2008-01-24
You doubled one line and it is 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

So you can make it look 

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

or you can simply delete it from your source list.

```
sudo mousepad /etc/apt/sources.list
```

and make changes.Save and close the file.

```
sudo apt-get update
```

---

### Post by grebarton on 2008-01-25
I tried it but it says:

grebarton@grebarton-desktop:~$ sudo mousepad /etc/apt/sources.list
[sudo] password for grebarton:
sudo: mousepad: command not found

---

### Post by grebarton on 2008-01-25
I have just removed access to those repositories in synaptic instead and its now fine.

Thanks for helping.

---

### Post by meindian523 on 2008-01-25
the problem was that zvacet uses Xubuntu which uses mousepad as the default editor.For ubuntu,use gedit and for Kubuntu,use kwrite.Please Mark the thread as solved.

---

### Post by zvacet on 2008-01-25
I use Ubuntu but i don´t know why I think that Mint use mousepad.Anyway I should advice** nano**.Sorry,my mistake!

---

