---
title: "issue installing pcsx2"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by caleb17 on 2016-05-27
So I had installed this on a linux mint machine I have and it worked perfectly using these ([http://wiki.pcsx2.net/index.php/Setting_up_Linux_version](http://wiki.pcsx2.net/index.php/Setting_up_Linux_version)) instructions. However when I try to do it on my main running ubuntu 14. Everything seems to work fine except for when I actually go to install it and I get this


caleb@Caleb-Main:~$ sudo apt-get install pcsx2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
 pcsx2:i386 : Depends: libgl1-mesa-glx:i386 or
                       libgl1:i386
              Depends: libwxgtk3.0-0:i386 (>= 3.0.0) but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I have only delt with errors installing involving something like "missing lib32" and have not a clue how to deal with or even read this. Much help would be much appreciated.

---

### Post by ajgreeny on 2016-05-27
The same command  ```
sudo apt-get install pcsx2 
```  on my 14.04 Xubuntu suggests that the package is not available.

I have ascertained that it needs a ppa repository at [https://launchpad.net/~gregory-hainaut/+archive/ubuntu/pcsx2.official.ppa](https://launchpad.net/~gregory-hainaut/+archive/ubuntu/pcsx2.official.ppa) which I assume you have enabled.  The ppa seems to be available for all the Ubuntu versions that are still supported so I wonder if you have other ppas enabled that may conflict with the packages available in this one.

---

### Post by caleb17 on 2016-05-31
Do you have any idea of how I could resolve this

---

