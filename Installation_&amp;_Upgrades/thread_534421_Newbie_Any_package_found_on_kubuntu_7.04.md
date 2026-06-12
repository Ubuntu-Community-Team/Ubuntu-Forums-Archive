---
title: "Newbie: Any package found on kubuntu 7.04"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by fredscripts on 2007-08-25
Hi! I've just installed kubuntu 7.04 and I've just read the kubuntu desktop guide. I've found some problems:

a)  I want to compile and run a java program: "javac Hello.java"," java Hello". When I type on the console "javac" it says to me that I can find that utility on a list of packages; I try sudo apt-get install <packagename> but no matter what package I try it says to me:

E: Couldn't find package <packagename>

and that happens with all the packages I try to install (kubuntu desktop guide recommend a few packages to be installed)

b) Reading kubuntu desktop guide I've seen how to install repositories:

To enable the extra repositories:
1. Start Adept by choosing K Menu - System -Adept (Package Manager) from the Desktop
menu system.
Adding, Removing and Updating Applications
31
2. Select View - Manage Repositories in the Adept package manager window.
3. To enable the Universe repository, find the repository line with the Universe Component, and
right click the line and select Enable.


But the fact is that in my kubuntu 7.04, in the Adept Manager (Manage Packages), there's no view - manage repositories (or I can't find it) I just find Adept - manage repositories, but doesn't match with the description.


To sum up, as a newbie, I would just like to compile and run java programs (as I can do with python or perl), and install packages and repositories (couldn't install anyone yet).

Another newbie things, if someone could help me in how to install netbeans on kubuntu 7.04 (the commands and how to get the correct source) and how to make a keyboard shortcut for moving to the Desktop in the visual environment  (like Windows+D in windows xp) I'll be so grateful.

Thanks to all and I hope some day I'll help newbies like me in this ubuntu world  :)

---

### Post by milton1 on 2007-08-25
you can edit the sources list by hand. 
```
sudo kate /etc/apt/sources.list 
```
just remove the # character from the extra repositories.

---

### Post by milton1 on 2007-08-25
Once you have the extra sources enabled, you can update your cache, 

```
sudo apt-get update 
```

and then hopefully you will find the package you need.

---

### Post by fredscripts on 2007-08-25
Thanks for answering. I must say that I don't have internet on that kubuntu computer (maybe it's a problem).

Running the command:

```
sudo kate /etc/apt/sources.list
```

I get the following message before opening the kate editor:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

 
```


Then, the content of the file is:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://es.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://es.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://es.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://es.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://es.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

I guess I have to uncomment:

```
# deb http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

Am I right? or I'll have some problems with the message I got after running the command?

Thanks!

---

### Post by Pumalite on 2007-08-25
Get Internet

---

### Post by fredscripts on 2007-08-25
I can't because my wireless device(which is quite old and not very good) doesn't work under linux (just xp, 2000,me,98 ). Also, I'm a complete fool on network stuff, I have a wireless router and when I connect that wireless device on a windows computer I get internet, but no response when I connect that device on a linux computer.

Some ideas to get internet? maybe the reason why I can't install any package is that I'm not connected to internet? (sorry for the newbie questions)

---

### Post by Pumalite on 2007-08-25
To use apt or aptitude you need Internet.

---

### Post by osos on 2007-08-25
that would be it.

---

### Post by fredscripts on 2007-08-25
Oh my, that would be the problem. So I must get a wireless device that work on linux before keep trying to install packages (maybe there's another way to get internet without that? I have the linux computer next to the wireless router, maybe configuring something on the network...?).

Thanks to all! probably I'll rescue this post when I have internet :)

---

