---
title: "Installing Apps not in Ubuntu--Xaos"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by abha_har on 2006-05-30
I recently installed Ubuntu and then added KDE as well on my XP 2500+ machine, and for the most part I am very favorably impressed. I can see they have gone to great lengths to make it bullet proof so that it is a lot harder for non technical people to break it. But at the same time, it looks like they take away some control too.

For the most part, the package list includes everything one might want, but there are a few applications I wanted to install, and I am having some trouble with it. One of my favorite graphics apps is one called XAOS. [http://k6.xs4all.nl/peter/gallery/](http://k6.xs4all.nl/peter/gallery/) It is old, but it makes beautiful graphics. To my frustration I found that it is included in Edubuntu but it is nowhere to be found in my applications list.

Real Player in this distro is broken, and I also wanted to reinstall that.

I have found Xaos in Knoppix, and I installed it/gotten it to work on other distros. I tried using apt-get to install it but...when I try and use apt-get at the command line to get Xaos...I am dead in the water:

[B]abha@ubuntu:~$ sudo apt-get install XaoS-3.2.1
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package XaoS-3.2.1[/B]

I have downloaded it and tried to get to it in my home folder, but even when I can see it in the GUI, I can't get to it to install it at the command line. I keep getting the message that the folder/file does not exist.

 No such file or directory

Anyway...I am getting pretty frustrated.

Abha

---

### Post by Kapre on 2006-05-31
abha - would suggest to check Xaos first in your SPM (Synaptic Package Manager). If it is there then you can install it, if its not then it means that the repo(s) that has this Xaos is not existent (reason for your error above). 

K

---

### Post by vayu on 2006-11-06
To install a .deb file that is on your hard disk you need to use the dpkg command.

Also, Xaos does exist in the repositories, I'm not sure what version.

---

