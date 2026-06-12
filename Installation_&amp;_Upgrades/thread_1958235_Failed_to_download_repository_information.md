---
title: "Failed to download repository information"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by ben44b on 2012-04-13
Greetings,

Been trying to check for updates for a while now and I always get the "Failed to download repository information" pop-up when I try to. 

I tried unchecking the marks in the software sources one at a time to no avail.

I took a screenshot of my Software Sources now. They're all unchecked. Starting to get lost now. Need help.

Thank you.

---

### Post by raja.genupula on 2012-04-13
in the terminal type ```
sudo apt-get update
``` and post the output here .

---

### Post by ben44b on 2012-04-14
This is the output

```
bernie@ubuntu:~$ sudo apt-get update
Ign http://mirror.csclub.uwaterloo.ca oneiric InRelease
Ign http://mirror.csclub.uwaterloo.ca oneiric-updates InRelease
Hit http://mirror.csclub.uwaterloo.ca oneiric Release.gpg
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates Release.gpg
Hit http://mirror.csclub.uwaterloo.ca oneiric Release  
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates Release         
Ign http://security.ubuntu.com oneiric-security InRelease             
Hit http://mirror.csclub.uwaterloo.ca oneiric/restricted Sources      
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates/restricted amd64 Packages
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates/main amd64 Packages
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates/multiverse amd64 Packages
Hit http://mirror.csclub.uwaterloo.ca oneiric-updates/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/oneiric/Release  Unable to find expected entry 'independent/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://mirror.csclub.uwaterloo.ca/ubuntu/dists/oneiric-updates/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/oneiric-security/Release  Unable to find expected entry 'independent/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
bernie@ubuntu:~$ 

```

Thanks.

---

### Post by raja.genupula on 2012-04-14
```
cat /etc/apt/sources.list
```

give the output of it , we have mistakes at those three lines .

---

### Post by ben44b on 2012-04-14
Output of cat :

```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release amd64 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric restricted independent main
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric restricted independent main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric universe
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric multiverse
deb-src http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.


# deb http://extras.ubuntu.com/ubuntu oneiric main #Third party developers repository
# deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
deb http://security.ubuntu.com/ubuntu/ oneiric-security restricted main multiverse universe independent
deb http://mirror.csclub.uwaterloo.ca/ubuntu/ oneiric-updates restricted main multiverse universe independent
bernie@ubuntu:~$ 

```

Thank you again.

---

### Post by jadtech on 2012-04-14
i have had this same issue tonight not sure why the out put from the apt get is the same
I could add after checking updates I get a notice to check my internet connection which is working fine as you can see I am post this message :)

---

### Post by ben44b on 2012-04-17
I found a website that generates a default sources.list depending on the release. That will be good for now.

[http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)

---

