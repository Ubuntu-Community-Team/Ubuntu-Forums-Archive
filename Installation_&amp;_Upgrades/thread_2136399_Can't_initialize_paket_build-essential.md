---
title: "Can't initialize paket build-essential"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by YuiYui on 2013-04-17
Hi, I install Ubuntu 12.04.02 LTS amd64 in a virtual box. I want develop with the Qt-Creator in connection with the g++ compiler. The problem is that the g++ is not inialize and I have no access to the internet. I try follow:

sudo apt-get install build-essential

The result: (I translate from German to English)
Paketlists are read
Dependency tree is build
Status information are reading

E: Paket build-essential not found

In the next step I try to get the build-essential paket from the internet and save it on a dvd with follow result:

With build-essential_11.4build1_amd64.deb  -> result: g++(>=4:4.3.1)
With build-essential_11.5ubuntu2_amd64.deb  -> result: g++(>=4:4.4.3)

My problem is I can't use

sudo apt-get update

because I have no internet connection. In the last step I try to install the g++ 4.4.3 version by the paket g++_4.4.3-1ubuntu1_amd64.deb with follow result:

g++4.4(>=4.4.3-1)

What can I do?

---

### Post by dabl on 2013-04-17
With no internet, there's no solution on that computer.

APT is designed to work with online repositories, and to resolve dependencies on the fly.  You could go to some other computer that has internet connectivity, go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and download the build-essential and linux-headers packages for your OS version, architecture, and kernel version, save them on flash media, and then use dpkg to install them on your system.  But you won't necessarily resolve their dependencies doing it that way, unless you review the dependencies, and the sub-dependencies, and the sub-sub-dependencies, etc. etc. on [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and download all those packages as well.

---

### Post by prshah on 2013-04-17
> **YuiYui said:**
> 
In the next step I try to get the build-essential paket from the internet and save it on a dvd with follow result:


If you have the original installation CDROM (/DVD) then add it as a repository, using the Terminal (Dash-Terminal) command ```
sudo apt-cdrom add
``` You can then install it using the apt-get command.

Alternately, if you have downloaded the .deb file, you can attempt to install it using the Terminal command```
sudo dpkg -i ~/Downloads/build-essential*
# correct the path as appropriate
```

Please post back error messages if you have problems, for more specific troubleshooting.

---

