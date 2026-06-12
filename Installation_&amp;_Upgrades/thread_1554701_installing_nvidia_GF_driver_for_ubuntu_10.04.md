---
title: "installing nvidia GF driver for ubuntu 10.04"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by runescape on 2010-08-17
Here is the steps to install Nvidia GF graphic card for Ubuntu 10.04:

1-  download  /..../nvidia.run 
2- recovery mode ( just choose it from  the list after the computer boots)
3- choose the last option (says  something like 'working in shell root')
4- sudo su
5- init 3
6-  login and password for your ubuntu desktop
7- sudo su
8- sh  /..../nvidia.run
9- while installing choose yes for disabling the  kernal with nvidia's support
10-  sudo reboot (restart ubuntu and  choose the normal mode)
11- cofigure nvidia server x  (system>preferences>nvidia x server settings)
12-choose all the  list and save the settings
13-sudo /etc/init.d/gdm restart (restart  server x from terminal)

---

### Post by tommcd on 2010-08-17
The nvidia driver from the Ubuntu repos should be your first choice. It is installed as a .deb package so APT (ubuntu's package manager) can easily maintain it. Thus it integrates into the Ubuntu system better than the driver from nvidia.com.
The only reason to use the driver from nvidia.com is if the driver in the Ubuntu repos will not work for you for some reason, or you need a new feature that has been added to the latest driver from nvidia.com. Usually the driver from the Ubuntu repos will work for the majority of nvidia users just fine.
What nvidia card do you have?
You should know that you will have to reinstall the driver from nvidia.com whenever there is a kernel update for Ubuntu.

And welcome to the Ubuntu forums!

---

### Post by runescape on 2010-08-17
Thanks for the hint, i should check out repos and see for myself what that is. 
mine is GF 6600, i did those steps and it worked as a charm, thought i'd share it with others since it took me couple of days to figure it out myself.

I wont have to reinstall the driver again because the neuv. kernal is disabled (look step 9).

---

### Post by tommcd on 2010-08-18
There is no advantage to using the driver from nvidia.com for an older card like a 6600. There is really no harm either; but installing the driver from the Ubuntu repos is easier, and it better integrated into the system.

The nvidia driver runs on the kernel is was built on. Reinstalling the driver is necessary when a new kernel is installed according to everything I have read:
[https://help.ubuntu.com/community/NvidiaManual#Kernel%20and%20Mesa%20Updates](https://help.ubuntu.com/community/NvidiaManual#Kernel%20and%20Mesa%20Updates)

---

### Post by runescape on 2010-08-18
Thanks again, for everybody there is a much easier way for ubuntu 10.04 users, simply :
 
System> Administration> Hardware drivers (activate)

---

