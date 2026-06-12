---
title: "Trying to upgrade from 11.04 to 12.04 LTS"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by ali_williams on 2013-06-04
so I am running the server edition of 11.04 on a test machine I have and I noticed I am on a out of date version of Ubuntu. I wanted to upgrade from 11.04 to 12.04 LTS but every time i try via command line the machine locks up.
I did the following.



$ sudo apt-get install update-manager-core

i get this as an output

Reading package lists...
Building dependency tree...
Reading state information...
update-manager-core is already the newest version.
The following packages were automatically installed and are no longer required:
  gnome-desktop-data g++-4.5 python-gconf g++ python-xdg libstdc++6-4.5-dev
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 653 not upgraded.


$ sudo do-release-upgrade -d
from there it goes to
Calculating the changes

24hrs later I am still at that prompt so do you guys know of anyway to fix this?

---

### Post by fantab on 2013-06-04
You cannot jump non LTS versions. Meaning you have first upgrade to 11.10 then to 12.04.

---

### Post by Cheesemill on 2013-06-04
It's failing because you've left it too long to upgrade.  It's trying to upgrade you to the 11.10 version which has also reached end-of-life, the repositories for it don't exist anymore.

I'd suggest backing up all of your data and doing a fresh installation of 12.04.

---

### Post by ali_williams on 2013-06-04
is there a way to backup all of my packages so i can just do a fresh install the have ubuntu auto download all the packages

---

### Post by Cheesemill on 2013-06-04
You can get a list of your currently installed packages by doing...
```
dpkg --get-selections > packages.txt
```
This will create a file called packages.txt which contains a list of all of the packages installed on your system, copy this file somewhere safe.

When you have your fresh installation you can run the following commands...
```
sudo dpkg --set-selections < packages.txt
sudo apt-get-f install
```
This will install all of the packages onto your new installation.

Bear in mind that this only installs the packages, any configuration you have done as well as your data will need restoring from your backup onto the new system.

---

### Post by ali_williams on 2013-06-04
> **Cheesemill said:**
> You can get a list of your currently installed packages by doing...
```
dpkg --get-selections > packages.txt
```
This will create a file called packages.txt which contains a list of all of the packages installed on your system, copy this file somewhere safe.

When you have your fresh installation you can run the following commands...
```
sudo dpkg --set-selections < packages.txt
sudo apt-get-f install
```
This will install all of the packages onto your new installation.

Bear in mind that this only installs the packages, any configuration you have done as well as your data will need restoring from your backup onto the new system.

that is far better than nothing!!! thanks :-D

---

### Post by ali_williams on 2013-06-06
So this command worked
sudo dpkg --set-selections < packages.txt

This one is not working. 
sudo apt-get -f install 

I get the following error
# sudo apt-get -f install
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.

so it sees the 118 packages but it wont install them

---

### Post by cincinnatus13 on 2013-06-06
Hey, FYI, I'm guessing you already set up the new system but if it's not too late, be sure to separate your / and /home into two partitions. This will allow you to upgrade the OS by itself in the future without issue.

Can't help you on the above unfortunately.

---

### Post by fantab on 2013-06-07
> **ali_williams said:**
> So this command worked
sudo dpkg --set-selections < packages.txt

This one is not working. 
sudo apt-get -f install 

I get the following error
# sudo apt-get -f install
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 118 not upgraded.

so it sees the 118 packages but it wont install them

Try:
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get -f install
```

---

