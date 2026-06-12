---
title: "Package download stops midway"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Sh00nya on 2007-05-20
I have been trying to install Beryl on my Ubuntu Feisty ...after upgrading and making the requisite changes in the xirg.conf file, when I run the command to install beryl & emerald themes, the download stops midway.

Here's the output I get:

sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  beryl-core beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings emerald libberyldecoration0 libberylsettings0
  libemeraldengine0
Suggested packages:
  libberylsettings0-gconf libberylsettings0-kconfig
Recommended packages:
  beryl-manager
The following NEW packages will be installed:
  beryl beryl-core beryl-plugins beryl-plugins-data beryl-settings
  beryl-settings-bindings emerald emerald-themes libberyldecoration0
  libberylsettings0 libemeraldengine0
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 4762kB/4967kB of archives.
After unpacking 13.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe beryl-plugins-data 0.2.1-0ubuntu2 [2354kB]
37% [1 beryl-plugins-data 1786647/2354kB 75%] 
---

It just stops and does nothing. any suggestions as to what might fox this or is there something I might be doing wrong?

TKA!

---

### Post by taurus on 2007-05-20
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the **us.** from all your repos.  Then save it and run

```
sudo apt-get update
sudo apt-get clean
sudo apt-get install beryl emerald-themes
```

---

### Post by jii2 on 2008-03-04
Hi,

i'm experiencing the same thing with my kubunutu 7.10 on dell d820 notebook. when connected through a router the download suddenly stops. it affects all downloads - package manager, kget, firefox, even flash movies.

has anybody found a solution for this?

thanks.

---

