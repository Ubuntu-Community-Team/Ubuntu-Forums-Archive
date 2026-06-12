---
title: "new to linux (kubuntu)"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Presnus on 2006-11-01
I've just installed Kubuntu but still have some questions because I'm new to linux.

*When I download a package like sun JDK where should I install it ? I just installed it under my home folder but I'm new to whole the hierarchy. In windows you should put it under Program files but has linux such folders ?

*I try'd to use the package manager. But can't find good mirrors (I think?) becauuse he can't find firefox,eclipse,ndiswrapper,... wich repository should I use? or should I install firefox and other software manually ?

Thanks

---

### Post by Zeroangel on 2006-11-01
Hi. I do not recommend installing programs in your home folder just because it makes a lot of unnecessary clutter. Programs by default should install in the proper directory (/usr/share/programname and /usr/bin) and it should all just work. 

Sun JDK? Ah, so you must be a Java Developer. There are multiple ways you can install the JDK, but the method I would recommend is to unlock the universe and multiverse repositories (do a forum search for 'repositories') open the Konsole, and run the command:```
sudo apt-get install sun-java5-sdk
```And Kubuntu will automatically download, configure, and install the JDK for you.

If your simply trying to set up some of the basics, to make it easier on yourself, I highly recommend you download EasyUbuntu or [Automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38"). These programs will set up a lot of things for you (ie: MP3 support, Java JRE, Flash, etc). Without you having to jump through too many hoops, like you might do otherwise.

---

### Post by themijs on 2006-11-01
another solution,

I'm using ubuntu, but think its the same whit Kubuntu.
You can install sun jdk whit synaptic.
Just use synaptic package manager whit al the repositories ( synaptic package manager--> settings--> repositories--> select all).


Greets

---

### Post by Presnus on 2006-11-01
Well I'll search for some repository's then and try to install it.

*I try'd to install ndiswrapper to for my linksys usb wifi device. But he can't find gcc and make :(


*When i try to install firefox I get this 

[IMG]http://img89.imageshack.us/img89/3453/snapshot1gk1.jpg[/IMG]

---

### Post by Zeroangel on 2006-11-01
That's because you have duplicate repositories in /etc/apt/sources.lst

What I would do if I were you is run this command:```
kdesu kedit /etc/apt/sources.list&
```Then fix the problems with the repositories. If you don't know how then feel free to use my sources.list instead.```
###deb cdrom:[Ubuntu 6.10 _edgy Eft_ - Release i386 (20051012)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb-src http://archive.ubuntu.com/ubuntu edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy universe 
deb-src http://archive.ubuntu.com/ubuntu edgy multiverse 

deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted 
deb http://security.ubuntu.com/ubuntu edgy-security universe 
deb-src http://security.ubuntu.com/ubuntu edgy-security universe 
```It doesnt include the additional repositories that members of the ubuntu community have put up, but this should be good enough for downloading most of the basic apps you will need.

---

### Post by Zeroangel on 2006-11-01
Once you've fixed your repositories, run this command:
```
sudo apt-get install build-essential
```This will install a bunch of things (like gcc and make) that will allow you to compile (make) packages that are not included in the repositories.

If there's other things you are looking for (lets say appname1 and appname2, and appname3) just run the command:```
sudo apt-get install appname1 appname2 appname3
``` and it will look for and install those packages for you.

Also, look around for any Ubuntu starter or beginners guides, because these are really helpful on helping you learn how to use linux.

---

