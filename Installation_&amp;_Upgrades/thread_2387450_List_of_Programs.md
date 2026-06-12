---
title: "List of Programs"
date: 2018-03-19
forum: Installation &amp; Upgrades
---

### Post by calebo5 on 2018-03-19
So I have a list of applications here that I need some help on installing the latest version of Ubuntu 17.10 so here they are (In case anyone is looking at this, I'm basically asking about how I can install applications via the terminal since I like the terminal better than the packages and the ubuntu software center.)


My computer is running either 17.10 or 16.04 and is an x64 bit system.


Gdebi
Synaptic Package Manager (Installs but cannot open sometimes)
Burning program to burn files onto a cd/DVD
Google Chrome
Steam
RealVNC
Ubuntu Software Center
Minecraft
Java
Flash
Text Editor
VLC
Virtualbox
VMWare Workstation
Emulation Program
QEMU
USB Creator Program
Disk Manager
Ubuntu Restricted Extras
ETC ETC ETC (I cannot think of any for right now but I will edit it or comment with a new app that I need to install from the command line)
List item


These are the programs that I want to install from the command line but if some require to be installed differently, that's ok for right now.

---

### Post by TheFu on 2018-03-19
```
sudo apt install {list of package names}
```
It is pretty standard stuff. Just need to figure out what the package name for each program is. Usually they are pretty simple. 

Proprietary programs probably aren't in the normal repos, so you might need to add a PPA.  If that doesn't exist, you should look for a .deb file, download it, and use 
```
sudo dpkg -i {name.of.package.deb}

```

Lastly, some programs aren't in the repos, don't have a PPA and don't have a .deb package file, so you'll need to get the source code and follow the INSTALL or README instructions.  Some are very clear and work well. Others are vague or assume knowledge you (and I) don't have to handle things.

Much of this stuff is answered in Ubuntu books.  When you are really new to Linux, working through a book would be smart, since  google isn't always your friend.  Many things change with every new release while other things have worked exactly the same for 20+ yrs. "The Linux Command Line" - google that - is a free ebook which works through how to use and run a Linux system.

---

### Post by oldos2er on 2018-03-19
There's an easier way to do this via terminal, using "dpkg --get-selections" and "dpkg --set-selections" commands; this will give you the actual package names rather than generic descriptions like your list. Though I don't quite understand from your question if you will be installing packages from one Ubuntu version to another version, is that your intention? 

[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)

---

