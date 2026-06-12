---
title: "dpkg install, apt-get...out of sync"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by hambonebrown on 2007-12-24
I've recently installed Skype...works fine. I downloaded the .deb file & used dpkg to install. However, now, when I try to use apt-get to build-dep or install any new package, I receive a message about apt-get needing to remove skype?

user@localhost:/$ sudo apt-get build-dep darksnow
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  skype
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 16.3MB disk space will be freed.

 -- or --

user@localhost:/$ sudo apt-get install darksnow
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  skype: Depends: libasound2 (> 1.0.12) but 1.0.11-7ubuntu3 is to be installed
         Depends: libqt4-core (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
         Depends: libqt4-gui (>= 4.2.1) but 4.2.0-1ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-- then --

user@localhost:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libpcre3-dev libldap2-dev libpcrecpp0 skype
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  skype
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 16.3MB disk space will be freed.

I believe the above mentioned libraries are installed...Skype is working fine...

Any suggestions are appreciated!

---

### Post by PmDematagoda on 2007-12-24
Do:-

```
sudo apt-get install -f
```
see if that solves your problem.

---

### Post by hambonebrown on 2007-12-24
sudo apt-get -f install results in this unwanted result:

user@localhost:/$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
libpcre3-dev libldap2-dev libpcrecpp0 skype
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
skype
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 16.3MB disk space will be freed.

It states that Skype will be removed. I never requested that it be removed, which is the strange thing?

---

### Post by PmDematagoda on 2007-12-24
Dpkg is rather "forceful", so use Gdebi to find out exactly what is required and what will not work before installing it, but first you will have to remove Skype, to do that:-

```
sudo dpkg -P skype
```

---

### Post by hambonebrown on 2007-12-24
I'm not familiar with gdebi...is that part of a standard install?

Thanks --

---

### Post by PmDematagoda on 2007-12-24
Gdebi is the graphical install, you just double-click on the deb file and Gdebi starts automatically.

---

