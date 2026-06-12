---
title: "Help pls E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by wolfmk on 2008-07-06
I will need a help so any one please:

-----------------------------
theone@theone-desktop:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lokkit gnome-bin mplayer-skins libsvga1 lzma libgnome32 gnome-libs-data
  libart2 libgnorbagtk0 libogg-dev libggi2 libgii1 libgnomeui32 libdb3
  liblzo2-2 libgii1-target-x libtimedate-perl liborbit0 bwidget
  libgnomesupport0 libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up evolution-common (2.10.1-0ubuntu2.4) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.10.1-0ubuntu2.4); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.10.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gthumb (2.10.6-0ubuntu1.1~feisty1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 evolution-common
 evolution
 evolution-plugins
 gthumb
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------------------------------------
And no matter what i try to install I get the last 6 lines ... :(

---

### Post by PmDematagoda on 2008-07-06
Do:-
```
sudo apt-get clean
```
and then do:-
```
sudo apt-get update && sudo apt-get upgrade
```
and see if that fixes the problem.

---

### Post by wolfmk on 2008-07-07
i did as u writte and same thing happened
-------------------------------------
theone@theone-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bpalogin dpkg-dev g++ libatm1 libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up evolution-common (2.10.1-0ubuntu2.4) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.10.1-0ubuntu2.4); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.10.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gthumb (2.10.6-0ubuntu1.1~feisty1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 evolution-common
 evolution
 evolution-plugins
 gthumb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by wolfmk on 2008-07-11
> **PmDematagoda said:**
> Do:-
```
sudo apt-get clean
```
and then do:-
```
sudo apt-get update && sudo apt-get upgrade
```
and see if that fixes the problem.

i did as u writte and same thing happened
-------------------------------------
theone@theone-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
bpalogin dpkg-dev g++ libatm1 libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up evolution-common (2.10.1-0ubuntu2.4) ...
dpkg: error processing evolution-common (--configure):
subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of evolution:
evolution depends on evolution-common (= 2.10.1-0ubuntu2.4); however:
Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
evolution-plugins depends on evolution (>= 2.10.1); however:
Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
dependency problems - leaving unconfigured
Setting up gthumb (2.10.6-0ubuntu1.1~feisty1) ...
dpkg: error processing gthumb (--configure):
subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
evolution-common
evolution
evolution-plugins
gthumb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by PmDematagoda on 2008-07-12
Then try doing:-
```
sudo apt-get autoclean
```
and
```
sudo apt-get upgrade
```
again.

---

### Post by wolfmk on 2008-07-12
> **PmDematagoda said:**
> Then try doing:-
```
sudo apt-get autoclean
```
and
```
sudo apt-get upgrade
```
again.

Same story:(

theone@theone-desktop:~$ sudo apt-get autoclean
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
theone@theone-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  bpalogin dpkg-dev g++ libatm1 libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up evolution-common (2.10.1-0ubuntu2.4) ...
dpkg: error processing evolution-common (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-common (= 2.10.1-0ubuntu2.4); however:
  Package evolution-common is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (>= 2.10.1); however:
  Package evolution is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
Setting up gthumb (2.10.6-0ubuntu1.1~feisty1) ...
dpkg: error processing gthumb (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 evolution-common
 evolution
 evolution-plugins
 gthumb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

