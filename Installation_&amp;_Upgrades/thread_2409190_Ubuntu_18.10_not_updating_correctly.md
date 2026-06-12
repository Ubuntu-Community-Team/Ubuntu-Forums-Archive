---
title: "Ubuntu 18.10 not updating correctly"
date: 2018-12-29
forum: Installation &amp; Upgrades
---

### Post by maravingian on 2018-12-29
Hi All,

I have noticed an issue with Ubuntu  over the last 2 weeks and was wondering if anyone else had this issue.

Software Updater tells me as usual updates are available.  I click Install and it updates. I check again and it advises No software update available afterwards, HOWEVER, the next time i boot the computer it asks for the same update files.  This has now been going on for the last 2 weeks.  Other than reinstalling Ubuntu is there anything else i can do??

My first screen when updating:



Then my second screen after it finally finds the updates:

---

### Post by Autodave on 2018-12-29
Try doing it manually and see what happens.  I have had the same issue a few times.  In a terminal:

sudo apt-get update

Then: 

sudo apt-get upgrade

---

### Post by oldos2er on 2018-12-29
Please post the full output of ```
sudo apt update
```

---

### Post by maravingian on 2018-12-30
d the commands of apt-get update and here is the response:

abraxys@M5A78L-M:~$ apt list --upgradable
Listing... Done
google-chrome-stable/stable 71.0.3578.98-1 amd64 [upgradable from: 70.0.3538.77-1]
N: There is 1 additional version. Please use the '-a' switch to see it
abraxys@M5A78L-M:~$ apt list -- upgradable -a
Listing... Done
abraxys@M5A78L-M:~$ apt list -a --upgradable
Listing... Done
google-chrome-stable/stable 71.0.3578.98-1 amd64 [upgradable from: 70.0.3538.77-1]
google-chrome-stable/now 70.0.3538.77-1 amd64 [installed,upgradable to: 71.0.3578.98-1]

---

### Post by maravingian on 2018-12-30
abraxys@M5A78L-M:~$ sudo apt update
[sudo] password for abraxys: 
Hit:1 [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) cosmic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease             
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) cosmic InRelease                     
Hit:4 [http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu](http://ppa.launchpad.net/paulo-miguel-dias/pkppa/ubuntu) cosmic InRelease 
Hit:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) cosmic-updates InRelease
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) cosmic-backports InRelease
Ign:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Ign:8 [http://download.opensuse.org/repositories/home:/strycore/xUbuntu_18.10](http://download.opensuse.org/repositories/home:/strycore/xUbuntu_18.10) ./ InRelease
Hit:9 [http://download.opensuse.org/repositories/home:/strycore/xUbuntu_18.10](http://download.opensuse.org/repositories/home:/strycore/xUbuntu_18.10) ./ Release
Hit:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.

---

### Post by maravingian on 2019-01-01
same problem this morning when i opened Software Update.  Think the original problem is the fat it cannot update the repository

---

### Post by maravingian on 2019-02-10
Hi All,

The issue is finally resolved using your advice. Many Thanks :)

---

