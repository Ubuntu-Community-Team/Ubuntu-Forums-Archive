---
title: "Missing dependencies in 16.04"
date: 2017-06-15
forum: Installation &amp; Upgrades
---

### Post by Semn on 2017-06-15
Hi, as 17.10 and 16.10 do not recognize a series of missing libraries for scientific programs, ubuntu 16.04 which worked previously is used. However, after upgrading and installing updates, the following appears:
upgrade and 
sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 teamviewer:i386 : Depends: libc6:i386 (>= 2.11) but it is not installed
                   Depends: libgcc1:i386 but it is not installed
                   Depends: libasound2:i386
                   Depends: libdbus-1-3:i386 but it is not installed
                   Depends: libexpat1:i386 but it is not installed
                   Depends: libfontconfig1:i386 but it is not installed
                   Depends: libfreetype6:i386 but it is not installed
                   Depends: libjpeg62:i386 but it is not installed
                   Depends: libsm6:i386 but it is not installed
                   Depends: libxdamage1:i386 but it is not installed
                   Depends: libxext6:i386 but it is not installed
                   Depends: libxfixes3:i386 but it is not installed
                   Depends: libxinerama1:i386 but it is not installed
                   Depends: libxrandr2:i386 but it is not installed
                   Depends: libxrender1:i386 but it is not installed
                   Depends: libxtst6:i386 but it is not installed
                   Depends: zlib1g:i386 but it is not installed
E: Unmet dependencies. Try using -f.


I cant find a page that solves this in ubuntu. What is the right sudo command to fix this?

Thanks

---

### Post by Autodave on 2017-06-15
"You might want to run 'apt-get -f install' to correct these."  Have you tried that yet? If so, what happened?

The other option is to manually install everyone of those programs listed.

If this all started with installing Teamviewer, then let's get it installed. Download GDebi and use that to install Teamviewer. Gdebi will get and install the dependencies that you need.

---

