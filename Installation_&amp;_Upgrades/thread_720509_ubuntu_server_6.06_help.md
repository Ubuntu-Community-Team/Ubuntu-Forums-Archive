---
title: "ubuntu server 6.06 help"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by ayet on 2008-03-10
I tried to install the entire Ubuntu Desktop Environment using these procedure

> 3 Steps to Install the entire Ubuntu Desktop Environment:
WARNING: This will configure your server to boot to graphical logon

1. Uncomment the "universe" repositories in sources.list:
$ vi /etc/apt/sources.list
$ apt-get update

2. Install the packages:
$ apt-get install ubuntu-desktop
$ apt-get install gdm
$ /etc/init.d/gdm start
$ dpkg-reconfigure xserver-xorg

2. Configure XOrg
$ apt-get dpkg-reconfigure xserver-xorg

I typed  **vi /etc/apt/sources.list** on the server console and it opened a text file that I need to remove the comments, I managed to removed all the comments but I dont know what to do next. any help is appreciated. btw iam new to this.

I also tried to run 
sudo apt-get install ubuntu-desktop
but it made an error.

---

### Post by Oldsoldier2003 on 2008-03-10
> **ayet said:**
> I tried to install the entire Ubuntu Desktop Environment using these procedure



I typed  **vi /etc/apt/sources.list** on the server console and it opened a text file that I need to remove the comments, I managed to removed all the comments but I dont know what to do next. any help is appreciated. btw iam new to this.

I also tried to run 
sudo apt-get install ubuntu-desktop
but it made an error.

what was the error?

---

### Post by ayet on 2008-03-10
> **Oldsoldier2003 said:**
> what was the error?

after typing **sudo apt-get install ubuntu-desktop** this appeared

reading package lists...done
building dependency tree...done
E: Couldn't find package ubuntu-desktop

any help is appreciated.

---

### Post by Pumalite on 2008-03-10
Post:
cat /etc/apt/sources.list

---

### Post by jcwmoore on 2008-03-10
I am guessing one of two things: either the sources.list file didn't save after you made your changes or the apt-get update command didn't work for some reason...

---

### Post by Pumalite on 2008-03-10
I'm guessing he needs to comment out all the sources.

---

### Post by ayet on 2008-03-10
> **jcwmoore said:**
> I am guessing one of two things: either the sources.list file didn't save after you made your changes or the apt-get update command didn't work for some reason...

how do you save the sources.list after I made the changes? what keys do I press?

---

### Post by jcwmoore on 2008-03-10
in vi if you are in "insert mode"...

ESC:w ('escape' + colon + w) enter
now to exit vi hit
:q enter

---

### Post by SJN2k on 2008-03-12
I am a complete beginner and have got a similar problem, ie no GUI, just a CLI. what do I need to do to get to this sources.list that needs editing?

 When I typed vi /etc/apt/sources.list, it just came up with a new empty document. 

My CLI prompt shows administrator@ubunto-server:~$

All help gratefully recieved.

---

