---
title: "Eclipse and dpkg complain of missing packages"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by bjackfly on 2013-07-08
Hi I installed Eclipse on my ubuntu myself in order to get the latest version. It seems to be working okay, but when I go to install anything else dpkg seems to complain of missing eclipse items. Does someone know how I can fix this? I have eclipse installed in the /opt/eclipse directory.

 dpkg: warning: files list file for package 'eclipse-platform-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eclipse-rcp' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eclipse-platform' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eclipse-jdt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eclipse-pde' missing; assuming package has no files currently installed

---

### Post by claracc on 2013-07-09
What way have you installed eclipse?, from what web page?

The two packages: eclipse-jdt and eclipse-pde are required dependencies in order to install eclipse.

There are eclipse package in ubuntu repositories, you can install it through synaptic or software center. Firstly I think you have to uninstall the eclipse you have installed.

---

### Post by bjackfly on 2013-07-09
I downloaded the package from the site, extracted it and copied it to the /opt folder.  Is there something else I need to do to setup the package dependencies? I set it up similar to the following link.

   *[http://terminaltwister.com/installing-eclipse-juno-in-ubuntu-13-04/](http://terminaltwister.com/installing-eclipse-juno-in-ubuntu-13-04/)

---

### Post by bjackfly on 2013-07-09
Also I should mention I removed any old version eclipse files before doing this as I had used the basic install sudo apt-get install eclipse originally but wanted the latest version so I deleted existing eclipse files found on the system and then followed the instructions to download and copy.

---

### Post by bjackfly on 2013-07-09
deleted the packages using

   *dpkg --list | grep "^ii" | grep eclipse
sudo dpkg --purge <package name>

---

