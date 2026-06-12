---
title: "How to install kile 1.7??"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-29
When I search synaptic I can only get kile version 1.6, but I read on the kile homepage that there is a kile version 1.7!

Is it not possible to install this version for Ubuntu??

---

### Post by Burgundavia on 2005-04-29
Probably the version was released after something called Upstream Version Freeze, which means that new versions of the software are not added to Ubuntu for stability reasons.

Thus, to get the new version, wait until the next release or track the development version. The 2nd is highly not recommended at teh current time.

Corey

---

### Post by Alexander Kirillov on 2005-04-29
[QUOTE=bigblop]When I search synaptic I can only get kile version 1.6, but I read on the kile homepage that there is a kile version 1.7!

Is it not possible to install this version for Ubuntu??[/QUOTE]
 It is definitely possible - I have Kile 1.7.1 installed. Just enable universe repository (I use Ubuntu, not Kubuntu).

---

### Post by bigblop on 2005-04-29
This is what I got in my sources.list file:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe  
deb [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) binary/ 
deb-src [ftp://neacm.fe.up.pt/pub/ubuntu-java/](ftp://neacm.fe.up.pt/pub/ubuntu-java/) source/ 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted


deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

What do I need to add to install Kile 1.7?

---

### Post by Seth on 2005-04-29
You're using Warty. You would need to use Hoary to get Kile 1.7.

---

### Post by Alexander Kirillov on 2005-05-02
[QUOTE=Seth]You're using Warty. You would need to use Hoary to get Kile 1.7.[/QUOTE]
 And this is Hoary forum - Warty questions should be posted in a different forum.

---

